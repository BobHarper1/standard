<div id="toc"></div>

## Standard Reference

This page provides reference information on publishing to the 360Giving Data Standard.

It assumes some technical knowledge.

If you are just getting started with the 360Giving data standard, consult the [start publishing](/get-involved/publish-your-data/) pages.

## Data formats

There are two main formats available for representing 360Giving data.

1. **Spreadsheet**: provided with user-friendly **column titles**, and for recording one grant per row. This is the most common template that publishers choose.
2. **JSON Schema**: for providing a structured representation of your data direct from your internal databases or via an API. Ideal for direct use by developers building visualisations and web apps.

In future, [a CSV Data Package](http://data.okfn.org/doc/data-package) serialisation will be available. Contact us if you need this.

The [CoVE](http://cove.opendataservices.coop/360/) (Convert, Validate and Explore) tool can be used to round-trip data between these formats, providing structured data for developers, and spreadsheet simplicity if you want to browse, sort and filter data on your desktop. 

## Spreadsheet format

The 360Giving Spreadsheet format consists of a 'grants' sheet which contains the most common data fields, and a series of additional tabs which can be used to provide more details about individual grants.

### Grants Sheet

The default grants sheet includes sections for:

* Basic information about the grant;
* Planned dates of the activity;
* Details of the recipient organisation;
* Details of the funding organisation;
* The location of beneficiaries;
* Details of the grant programme funding is from;

To provide classifications of grants, more than one location, or additional documents related to the grant, you will need to publish information in sub-tables. 

{{grant.csv|Title,Description,Type,Required}}

### Additional tables

The grants sheet can only accommodate one-to-one relationships. For example, one classification or location per grant. It also only includes common information.

To provide details of additional classifications, locations, events, documents, organization and transaction information you can use the other tabs of the spreadsheet. 

In the first column of each tab you would enter the identifier of the grant to which the additional information relates, as recorded in the id column of the grant sheet. 

#### Classification

{{Classification.csv|Title,Description,Type,Required}}

#### Location

{{Location.csv|Title,Description,Type,Required}}

#### Documents 

{{Documents.csv|Title,Description,Type,Required}}

#### Event

{{Event.csv|Title,Description,Type,Required}}

#### Organization

{{Organization.csv|Title,Description,Type,Required}}

#### Transaction

{{Transaction.csv|Title,Description,Type,Required}}

### Field guidance

#### Dates and times

360Giving allows you to provide information on when a grant was awarded, when a project is taking place, and when you last updated information about aspects of the grant.

There are three different rules for validating dates

##### Award dates
The ```Award Date``` must provide a full date, including year, month and day in YYYY-MM-DD format (e.g. 2016-04-02 for the 2nd April 2016). 

In some rare cases, an award date might also need to include the time of the grant, using a date-time format (e.g. 2016-04-02T16:45:00Z for a grant made at 4.45 if the afternoon). 

**Tip**: You can set Excel to present a date column in YYYY-MM-DD format using a custom format [as described here](http://superuser.com/questions/409896/how-do-i-enter-dates-in-iso-8601-date-format-yyyy-mm-dd-in-excel-and-have-exc/409899#409899). 

##### Other events
Other events in the lifetime of a grant, such as the planned dates when the funded activity will take place may include more or less specific dates. Funders should aim to be as specific as they can be, but do not need to guess at the particular day or month when an activity will take place if they do not know. Dates should always be provided in YYYY-(MM)-(DD) format. 

For example, if an application only indicates a project will start in May 2016, then the ```Planned Dates:Start Date``` field may be '2016-05'. 

It is up to users of the data to judge how to interpret dates which only include a year, or year and month. Different applications and analysis may require different judgements. 

##### Last modified dates
All rows in a 360Giving spreadsheet, and all objects in the JSON structure, can have a ```Last Modified``` date. 

This should always be a full date-time so that if multiple updates take place on a single day, consuming applications can work out which version to use. 

**Tip**: You can set Excel to present a date column as a full date-time using the custom format of "yyyy-mm-ddThh:mm:ssZ". If you set the formula for the column to ```=Now()``` then the last updated value will be refreshed automatically everytime you save the file. 

* **Award Date** - this should be the full date 


### Conformance

In order to conform with the spreadsheet standard:

You must:

* **Read the column definitions carefully and follow the format they request** - for example, formatting identifiers and dates according to the standard. Full reference information is provided below.
* **Provide an identifier** for each grant
* **Update the last modified date** whenever the status of a grant changes

You can:

* **Remove or hide non-required columns that you are not using** - although make sure you check any [hidden columns](#hidden-columns) before publishing your data, and always remove rather than hide sensitive information.
* **Re-order the columns** so that information is arranged in the way you want
* **Add extra columns** to include information you want to share, but that is not covered by the standard. 

You must not:

* **Add extra rows at the top of the table**
* **Change the field names provided by the standard**

## JSON data model

The 360Giving standard is defined by a modified [JSON Schema](http://json-schema.org/). This details the entities that can be described using the standard, and the properties it recognises. 

At the root of the data model is a grant. Grants have a number of direct properties (e.g. Title, Description, Currency, Amount Awarded etc.) and then a number of related entities, including Organisations (Funder and Recipient), Locations (Recipient, Beneficiary), Classifications, Grant Programmes, and Transactions. 

### 360Giving JSON Schemas
The 360Giving JSON Schemas are the authoritative source of information about the standard, and it should always be possible to transform 360Giving data into structured JSON data according to these schema. 

The [360Giving Grant Schema](/wp-content/plugins/threesixty_docs/standard/schema/360-giving-schema.json) defines the structure of an individual 'grant' and the documentation from this is displayed below, or [fullscreen here](/wp-content/plugins/threesixty_docs/docson/index.html#/wp-content/plugins/threesixty_docs/standard/schema/360-giving-schema.json).

When exchanging data about a single grant or any number of grants, those grants need to be packaged into a single JSON file. The [360Giving Package  Schema](/wp-content/plugins/threesixty_docs/standard/schema/360-giving-package-schema.json) describes how grants are packaged into one file.

In general, most publishers will initially only use a sub-set of the possible features of the standard, but it is designed to accommodate comprehensive data about all stages of a grant process: for a full 360-degree view.

<div style="height:400px; overflow:auto; border:1px solid grey;">
<script src="/wp-content/plugins/threesixty_docs/docson/widget.js" 
        data-schema="/wp-content/plugins/threesixty_docs/standard/schema/360-giving-schema.json">      
</script>
</div>

### Field names and titles

Each entity, property and relationship in the schema has both a machine-readable field name and an English language title.

The English language titles are important for humans working to make sense of the data in everyday desktop software, and so the default Summary Template makes use of titles as opposed to field names. 

The field names are important for computers reading the data, and even if other language titles are provided in future, the underlying field names will remain constant.

A mapping between column titles and field names for the Summary Table is given below:

{{grant.csv|Title,Name,Type}}


## Extending the summary table
The default summary table template is defined by use of special ‘rollUp’ properties in the [underlying JSON Schema file](/wp-content/plugins/threesixty_docs/standard/schema/360-giving-schema.json). There is a [Flatten Tool](https://github.com/OpenDataServices/flatten-tool) that uses these properties when creating templates. However, it is possible, following the same naming convention for fields, to bring most properties into the Activity table if a particular use-case requires. 

For example, the structure:

* Activity
  * relatedDocument
    * url

can by represented in the Activity table under the column name:

* ```relatedDocument[]/url``` 

or the column title

* ```Related Document:URL```

The naming convention for field names is to:

* If the relationship can be a one-to-many relationship, append ```[]``` to the relationship property name 
* Concatenate the relationship and property names using /
* If required, indicate the type of the column values using the ```:number```, ```:integer```, ```:string```, ```:date-time``` and so-on.

The naming convention for field titles is to:

* Concatenate the relationship and property titles using a ```:```.

In the event that a value for a property is given in both a sub-table, and the summary table, the sub-table value always takes precedence, and will over-write the summary value. 

### JSON

When data is being generated directly out of a database system, publishers should consider using the JSON schema to provide a JSON file.

Developers may also wish to build their applications of JSON versions of the data. 

The [CoVE](http://cove.opendataservices.coop/360/) (Convert, Validate and Explore) tool supports round-tripping of data between Summary spreadsheet, multi-table datapackage and JSON representations. 


## Schema documentation

Identifiers are documented on the [identifiers](/identifiers/) pages.


