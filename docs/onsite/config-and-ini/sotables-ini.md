---
# This basic template provides core metadata fields for Markdown articles on docs.superoffice.com.

# Mandatory fields.
title: sotables_ini       # (Required) Very important for SEO. Intent in a unique string of 43-59 chars including spaces.
description: SoTables.ini # (Required) Important for SEO. Recommended character length is 115-145 characters including spaces.
author: {github-id}             # Your GitHub alias.
keywords:
so.topic: reference             # article, howto, reference, concept, guide

# Optional fields. Don't forget to remove # if you need a field.
# so.envir:                     # cloud or onsite
# so.client:                    # online, web, win, pocket, or mobile
---

# SoTables.ini

Used by [DBSetup.exe][1]

* This file is up until 8.1 used during the setup phase - it describes which prime data files are to be loaded into the newly created or upgraded database.

* Before 8.1 the file is created automatically during the setup process with links to our priming data. From 8.1 the priming data is part of our dictionary steps and the files are no longer used.

* You may manually edit this file to import additional data.

Before SuperOffice 8.1 and the [continuous database][2], this file would also have some sections that where always loaded after a fresh install, when creating a new database. These are not available from the dropdown menu inside DBSetup.exe to avoid running them unintentionally.

Some sections may be re-run to update or add additional data, and you may also create your own section to add your own import files.

## Sections in this file

Init - Register - Upgrade are hidden from the Load or re-load initial data into an 8.1+ database dropdown in SuperOffice CRM Database Maintenance (DBsetup.exe) menu.

You may add your own import files and add a section inside brackets, like: `[MyImportSection]`

The prefix before =path.and.filename just needs to be unique.

```text
UNIQEPREFIX_A=c:\program files (x86)\SuperOffice\SuperOffice Server\Init\MyImportFile.imp
```

## Creating your own imp file

The imp file must match the table you want to import, starting with the table name inside brackets. On the line below you may specify what you want to do with the current data in this table.

### Truncate\_table

This will delete all data in the table before it imports what is found in the imp file.

### Truncate\_BuiltIn and Set\_BuiltIn

Special data marked as belonging to SuperOffice may be updated in later releases, this is done by us flagging our data with 1 inside the IsBuildIn field of the database table. Then we can later tell DBSetup that we only want to delete our data, but leave customer and partner rows behind in the database.

> [!NOTE]
> If you set the primary key of a table to 0 then DBSetup with automatically set the primary key to the next available value. If you want to set it hard to a specific ID like we do in SORPublish table in the *I\_STDReportsNew.imp* file.
If you need to reuse a privacy key later, in another table you may use variables like `#MyTableEntry_id1`, `#MyTableEntry_id2` and so on. Then in a later table in the same imp file, you may pick up the value and assign it as a foreignKey.

![x][3]

<!-- Referenced links -->
[1]: https://community.superoffice.com/en/technical/documentation/administration/dbsetup/
[2]: https://community.superoffice.com/en/content/content/database/continuous-database/
[3]: media/primaryforeignkey.png