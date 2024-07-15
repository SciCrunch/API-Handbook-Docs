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

## Curate new Terms

## &#x20;
