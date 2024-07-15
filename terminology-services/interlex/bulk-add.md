---
description: Simplified example of bulk add for InterLex terms.
---

# Bulk Add

## Prerequisite code

With `gspread`, you can automate various tasks such as retrieving and updating tabular data, clearing sheets, and handling multiple tabs within a Google Sheet. This can significantly streamline workflows involving InterLex terms.`gspread` is a powerful tool for interacting with Google Sheets, allowing users to add and update InterLex terms efficiently. It offers functionality to open, modify, and manage Google Sheets using Python, making it easier to handle data programmatically.&#x20;

All the needed code for gspread is found below:

<pre class="language-python"><code class="lang-python"><strong>import gspread 
</strong><strong>
</strong><strong>class GSheet:
</strong>    """Can Opens/Modify Google sheets 1 tab at a time :D"""

    def __init__(self, sheet_name: str) -> None:
        gc = gspread.oauth()
        self.sheet_name = sheet_name
        try:
            self.sheet = gc.open(sheet_name)
        except:
            self.sheet = gc.open_by_key(sheet_name)

    def get_tab(self, tab_name: str) -> pd.DataFrame:
        """
        Get Google Sheet tab as a pandas DataFrame

        Parameters
        ----------
        tab_name : str
            Specific Google Sheet tab name (Google has the default to "Sheet1")

        Returns
        -------
        pd.DataFrame
        """
        worksheet = self.sheet.worksheet(tab_name)
        try:
            header, *body = worksheet.get_all_values()
            return pd.DataFrame(body, columns=header)
        except:  # worksheet is empty
            return pd.DataFrame()

    def update_tab(
        self,
        tab_name: str,
        df: pd.DataFrame,
        cell_range: str = None,
        include_header: bool = True,
    ) -> None:
        """
        Updates only the text of a single tab within the Google Sheet initialized. This does not update the
        Google Sheet settings, colors, fonts, or funcitons. Just the text value.

        Parameters
        ----------
        tab_name : str
            Google Sheet tab name
        df : pd.DataFrame
            DataFrame of the data to be completely overwritten on the tab
        """
        worksheet = self.sheet.worksheet(tab_name)
        if include_header:
            data = [df.columns.values.tolist()] + df.values.tolist()
        else:
            data = df.values.tolist()
        if cell_range:
            worksheet.update(cell_range, data)
        else:
            worksheet.update(data)
            
    def clear(self, tab_name: str) -> None:
        """deletes contents of sheet"""
        worksheet = self.sheet.worksheet(tab_name)
        worksheet.clear()         
</code></pre>

## Gspread Usage

Gspread should be unique in naming scheme in order to avoid using ID hashes for the input.

```python
gsheet = GSheet('Google Sheet Name')
df = gsheet.get_tab('Sheet1')
```

## Curate new Terms

With the string\_profiler function you can `clean` the existing labels with parenthesis for special &#x20;

```python
def string_profiler(
        string: str,
        start_delimiter: str='(',
        end_delimiter: str=')',
        remove: bool=True,
        keep_delimiter: bool = True,
    ) -> List[str]:
    '''
    Seperates strings fragements into list based on the start and end delimiters
    Args:
        string: complete string you want to be broken up based on start and stop delimiters given
        start_delimiter: delimiter element to start
        end_delimiter: delimiter elemtent to end
        remove: decide whether or not to keep strings inside the delimiters
    Returns:
        List[str]: list of strings that are split at start and end delimiters given and whether
            or not you want to remove the string inside the delimiters
    Tests:
        long = '(life is is good) love world "(blah) blah" "here I am" once again "yes" blah '
        print(string_profiler(long))
        null = ''
        print(string_profiler(null))
        short = '(life love) yes(and much more)'
        print(string_profiler(short))
        short = 'yes "life love"'
        print(string_profiler(short))
    '''
    outer_index  = 0  # stepper for outer delimier string elements
    inner_index  = 0  # stepper for inner delimier string elements
    curr_index   = 0  # actual index of the current element in the string
    string_list  = [] # string broken up into individual elements whenever a start and end delimiter is hit
    outer_string = '' # string tracked while outside the delimiters
    inner_string = '' # string tracked while inside the delimiters

    for outer_index in range(len(string)):
        # Actual pointer position (inner delimiter counter + outer delimiter counter)
        curr_index = inner_index + outer_index
        # Close once acutal index is at the end
        # NOTE: outer_index will keep going till end regardless of hitting a delimiter and adding to inner stepper.
        if curr_index == len(string): break
        ### DELIMITER HIT ###
        if string[curr_index] == start_delimiter:
            # If we his a delimiter, collect the string previous to that as an element; flush
            if outer_string:
                # Option: .extend(outer_string.strip().split()) | If you want every word seperate. Maybe an option?
                string_list.append(outer_string.strip())
                outer_string = ''
            for j in range(curr_index+1, len(string)):
                # Stepper that is pushed while in inner delimiter string.
                inner_index += 1
                # Once we his the end delimiter, stop iterating through the inner delimiter string
                if string[j] == end_delimiter: break
                # String inside delimiters
                inner_string += string[j]
            # If you want the string inside the delimiters
            if not remove:
                if keep_delimiter:
                    inner_string = start_delimiter + inner_string + end_delimiter
                string_list.append(inner_string)
            # inner delimiter string restart
            inner_string = ''
        # String outside of the delimiters
        else: outer_string += string[curr_index]
        # End delimiter is either nested or not the real target; should ignore
        if string[curr_index] == end_delimiter:
            if string_list and outer_string:
                string_list[-1] += outer_string
                outer_string = ''
    # In case of not hiting a delimiter at the end of the string, collect the remaining outer delimiter string
    # Option: .extend(outer_string.strip().split()) | If you want every word seperate. Maybe an option?
    if outer_string: string_list.append(outer_string.strip())
    return string_list
```

## Cleaned label column

```python
df['cleaned_label'] = df['label'].apply(lambda x: ''.join(string_profiler(x)).lower())
```

## (Optional) Add Synonyms

Synonyms can be inferred as labels for exact ontology types. If you want to check synonyms for a data source you know is not unique, add as so.

<pre class="language-python"><code class="lang-python"><strong>if isinstance((df['Synonyms'].applymap(type) == list).all():
</strong><strong>    df['Synonyms'] = df.explode('Synonyms')
</strong><strong>
</strong><strong>df['cleaned_synonyms'] = df['Synonyms'].apply(lambda x: ''.join(string_profiler(x)).lower())
</strong></code></pre>

## Add Terms and update Google tab

```python
ilx_id_column = 'ILX UUID'

for i, row in df.iterrows():
    entity_field = row.to_dict()
    
    if 'interlex' in row[ilx_id_column]:
        continue
    elif not row['cleaned_label']:
        continue
    elif row['cleaned_label'] in cleaned_labels: 
        print('row:', row.name + 2, ' -- ', row['cleaned_label'], ['http://uri.interlex.org/base/' + ilx for ilx in label2ilx[row['cleaned_label']]])
        continue
    
    df.loc[i, ilx_id_column] = ilx_cli.add_entity(label=row['label'].strip(), type='term', definition=row['Definition'], **entity_fields)['ilx']
```

## Update Google Tabe

<mark style="color:red;">! Warning !</mark> Please make sure that there is an existing 'ILX UUID' column in the sheet to write over or it will append the column and might remove the annotation meaning such as colors and grouped sets made on the Google sheets.

```python
gsheet.update_tab(df=df, tab_name='Sheet1')
```
