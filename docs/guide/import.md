# Importing data

[CSV] importers are provided for all [asset] and [log] types in farmOS.

This video by Chris Callahan at [UVM Extension]'s
[Agricultural Engineering Program] summarizes the comma separated variable
(CSV) import and export feature of FarmOS which allows for the import and
export of FarmOS data from and to spreadsheet applications. This may be
especially helpful for offline use.

<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/NoOuNZRNjRo?rel=0" allowfullscreen></iframe>
</div>

Links to each importer can be found at the top of each primary asset or log
listing page (accessible via the [main menu] of farmOS). For example, if you
want to import Animal assets, click on Assets > Animals in the main menu, and
then click the "Import animals" action link at the top of the page.

There is a link to "Download a template" within the importer page, which will
give you a blank CSV file with all the necessary column headers. Start with the
template file, and add a row for each of the records you want to import. Save
this file and upload it to the importer form to create the new records in
farmOS.

## Common fields

Each asset/log type has its own importer, and some have fields that are unique
to their type, but there are some common fields that are shared across all
importers.

Common asset fields include:

* **Name** - The name of the asset (required).
* **Archived** - Whether or not the asset is archived. See "Boolean options"
  below for allowed values. If omitted, the asset will not be archived.
* **Description** - A longer description of the asset.
* **Parent IDs** - A comma-separated list of asset IDs that represent parents
  of the asset being imported. These parent assets must already exist in farmOS
  in order for the link to be created. **See notes below.**
* **Parent names** - A comma-separated list of asset names that represent
  parents of the asset being imported. These parent assets must already exist in
  farmOS in order for the link to be created. **See notes below.**

Common log fields include:

* **Name** - The name of the log. This will be automatically generated if it is
  left blank.
* **Date** - The date when the logged event takes place (required). This can be
  a string in any English date format that is convertable to a UNIX timestamp.
* **Done** - Whether or not the log is complete. See "Boolean options" below
  for allowed values. If omitted, the log will be marked as "done".
* **Notes** - A longer description of the logged event.
* **Asset IDs** - A comma-separated list of asset IDs that this log is related
  to. These assets must already exist in farmOS in order for the link to be
  created. **See notes below.**
* **Asset names** - A comma-separated list of asset names that this log is
  related to. These assets must already exist in farmOS in order for the link to
  be created. **See notes below.**
* **Archive assets** - If this is set to "Y", then any assets referenced on the
  log will be archived. This can be used to archive assets at the same time as
  recording their harvest logs, for example. See "Boolean options" below
  for allowed values. If omitted, assets will not be archived. Note that this
  will archive assets even if the log is not marked "Done" during import.
* **Areas** - A comma-separated list of areas that this log is related to.
  Areas will be matched on their name, and new areas will be created if they do
  not exist.
* **Categories** - A comma-separated list of log categories that should be
  applied to the log. The categories must already exist in farmOS in order for
  the assignment to take place.

Common fields that are required are noted above. Specific asset/log type
importers may have additional required fields.

### Asset names vs IDs

In some importers, it is possible to reference assets by either their names or
their IDs. For example, with the "Asset names" and "Asset IDs" columns in log
importers, or the "Parent names" and "Parent IDs" in asset importers.

**Do not use both of these columns at the same time.**

There is currently a [known issue] with merging the two columns together. It is
OK to use IDs in one row, and names in another row. Do not use both in a single
row.

**If two assets with the same name exist, the one with the higher asset ID will
be selected.**

This is based on the assumption that you want to import records associated with
recent assets. If you are trying to import old records, and you have duplicate
asset names in your system, you must use the "Asset IDs" column and reference
the assets explicitly with their IDs.

## Boolean values

The following values are acceptable for boolean fields, like "Archived" for
asset importers, and "Done" for log importers. These values are not case
sensitive (so "Yes" and "yes" will be treated the same).

### True

* Yes
* Y
* True
* T
* 1

### False

* No
* N
* False
* F
* 0

## Access

CSV importers are only available to users with the Farm Manager [role].

[CSV]: https://en.wikipedia.org/wiki/Comma-separated_values
[asset]: /guide/assets
[log]: /guide/logs
[UVM Extension]: https://www.uvm.edu/extension
[Agricultural Engineering Program]: https://www.uvm.edu/extension/agriculture/agricultural_engineering
[main menu]: /guide#navigation
[role]: /guide/people
[known issue]: https://www.drupal.org/project/farm/issues/3086844

