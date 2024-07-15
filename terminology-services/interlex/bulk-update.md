---
description: Simplified example of bulk update for InterLex terms.
---

# Bulk Update

## Prerequisite code

Please see [bulk-add.md](bulk-add.md "mention")for all prequisite code

## Bulk Update

```python
from ontquery.interlex import interlex_client 
from ilxutils.sql import production_sql

# from_backup=True only avaliable if used cmd `backup_ilx` once ilxutils was installed
sql = production_sql(from_backup=True)


terms = sql.get_terms()
syn = sql.get_synonyms()
annotations = sql.get_annotations()
ex = sql.get_existing_ids()
superclass = sql.get_superclasses()
relationship = sql.get_relationships()

# Client
ilx_cli = interlex_client('scicrunch.org').ilx_cli
```

The docstring for the update\_entity!

```python
ilx_cli = interlex_client('scicrunch.org').ilx_cli

[ out ] ilx_cli.update_entity(
    ilx_id: str,
    label: str = None,
    type: str = None,
    definition: str = None,
    comment: str = None,
    superclass: str = None,
    cid: str = None,
    orig_cid: str = None,
    status: str = None,
    add_synonyms: Union[List[dict], List[str]] = None,
    delete_synonyms: Union[List[dict], List[str]] = None,
    add_existing_ids: List[dict] = None,
    delete_existing_ids: List[dict] = None,
) -> dict
Docstring:
Updates pre-existing entity as long as the api_key is from the account that created it.

:param ilx_id: Interlex IRI, curie, or fragment of entity to update.
:param label: Name of entity.
:param type: InterLex entities type: term, cde, fde, pde, annotation, or relationship
:param definition: Entities official definition.
:param comment: A foot note regarding either the interpretation of the data or the data itself
:param superclass: The ilx_id of the parent of this entity. Example: Organ is a superclass to Brain
:param cid: Community ID.
:param status: Entity status.
    -2 : Withdrawn; entity is no longer searchable and is not visible
    -1 : Under review; entity is visible
    0 : No action needed; entity is visible
:param add_synonyms: Synonyms to add if they don't already exist.
:param delete_synonyms: Synonyms to delete.
:param add_existing_ids: Add alternative IRIs if they don't already exist.
:param delete_existing_ids: Delete alternative IRIs.
:return: Server response that is a nested dictionary format
```
