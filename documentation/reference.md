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

|Title|Description|Type|Required|
|----|----|----|----|
|Identifier|The unique identifier for this grant. Made up of your 360Giving prefix, and an identifier from your records. See the [360Giving Grant identifier guidance](http://www.threesixtygiving.org/standard/identifiers/#toc-grant-identifier) for details.|string|True|
|Title|A title for this grant activity. This should be under 140 characters long.|string|True|
|Description|A short description of this grant activity.|string|True|
|Currency|The currency used in amounts. The currency used in amounts. Use the three-letter currency code from [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) eg: GBP|string|True|
|Amount Applied For|Total amount applied for in numbers (do not include commas or currency symbols such as £). If you have provided detailed transaction information on a separate table, this should equal the sum of all the application transactions for this grant.|number|False|
|Amount Awarded|Total amount awarded in numbers (do not include commas or currency symbols such as £). If you have provided detailed transaction information on a separate table, this should equal the sum of all the award transactions for this grant.|number|True|
|Amount Disbursed|Total amount disbursed (paid) to this grantee when this record was last updated (in numbers: do not include commas or currency symbols such as £)). If you have provided detailed transaction information on a separate table, this should equal the sum of all the disbursement transactions for this grant.|number|False|
|Award Date|When was the decision to award this grant made. The date should be written as YYYY-MM-DD, or in full date-time format.|string|True|
|URL|A URL (Web Address) where further information about this grant can be found. This could point to the website of the recipient organisation, or might link to further details on the funders website.|string|False|
|Planned Dates:Start Date|When the applicant / implementing organisation originally intend this activity to take place.  All events should have a start date. Dates should be in YYYY-MM-DD or date-time format. If the month or day are not available, these may be omitted.|string|False|
|Planned Dates:End Date|When the applicant / implementing organisation originally intend this activity to take place.  Events or activities lasting more than one day should have either a duration (in months) or an end date. Dates should be in YYYY-MM-DD or date-time format. If the month or day are not available, these may be omitted.|string|False|
|Planned Dates:Duration (months)|When the applicant / implementing organisation originally intend this activity to take place.  Events or activities lasting more than one day should have either a duration (in months) or an end date.|string|False|
|Recipient Org:Identifier|Details of the recipient of this grant. A globally unique identifier for this organisation. This is important to enable data on funders and recipients to be linked up across different grant-makers. The [Organisation Identifier Standard](http://www.threesixtygiving.org/standard/identifiers/#toc-organisation-identifier) guidance explains how to create this ID, based either on the known company or charity number, or upon identifiers held in the grant-maker's internal systems.|string|True|
|Recipient Org:Name|Details of the recipient of this grant. Organisation name|string|True|
|Recipient Org:Charity Number|Details of the recipient of this grant. Registered charity number, if applicable.|string|False|
|Recipient Org:Company Number|Details of the recipient of this grant. Registered UK company number, if applicable.|string|False|
|Recipient Org:Street Address|Details of the recipient of this grant. Building number and street name.|string|False|
|Recipient Org:City|Details of the recipient of this grant. City or town.|string|False|
|Recipient Org:County|Details of the recipient of this grant. County|string|False|
|Recipient Org:Postal Code|Details of the recipient of this grant. Postal code (please try and provide a post code whenever possible)|string|False|
|Recipient Org:Country|Details of the recipient of this grant. Country|string|False|
|Recipient Org:Description|Details of the recipient of this grant. A short description of this organisation and its area of work|string|False|
|Recipient Org:Web Address|Details of the recipient of this grant. A web address for the Organisation|string|False|
|Beneficiary Location:Name|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. A name for this location.|string|False|
|Beneficiary Location:Country Code|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. The ISO Country Code of the location of this activity.|string|False|
|Beneficiary Location:Latitude|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. The latitude of a point location|string|False|
|Beneficiary Location:Longitude|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. The longitude of a point location|string|False|
|Beneficiary Location:Geographic Code|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. A code referring to a geographical area, drawn from an established gazetteer. For example, the code for a local authority ward, or parliamentary constituency.|string|False|
|Beneficiary Location:Geographic Code Type|Information about the location of beneficiaries. Further information about beneficiaries can be provided through classifications. The type of Geographic Code (geoCode) used (e.g. Ward, Parliamentary Constituency etc.). This value for this field should be drawn from the [codelist of geographic code types](https://github.com/ThreeSixtyGiving/standard/tree/master/codelists/geoCodeType.csv).|string|False|
|Funding Org:Identifier|Details of the funder A globally unique identifier for this organisation. This is important to enable data on funders and recipients to be linked up across different grant-makers. The [Organisation Identifier Standard](http://www.threesixtygiving.org/standard/identifiers/#toc-organisation-identifier) guidance explains how to create this ID, based either on the known company or charity number, or upon identifiers held in the grant-maker's internal systems.|string|True|
|Funding Org:Name|Details of the funder Organisation name|string|True|
|Funding Org:Department|Details of the funder The department or sub-unit of this organisation making or receiving the grant.|string|False|
|Grant Programme:Code|- An identifier for this grant programme.|string|False|
|Grant Programme:Title|- The title of this grant programme.|string|False|
|Grant Programme:URL|- A web link to more details of this grant programme.|string|False|
|From an open call?|Was this grant made as the result of an open call for applications? Values should be 'Yes' or 'No'|string|False|
|Last modified|When was information on this grant last updated? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|
|Data Source|A web link pointing to the source of this data. This may be an original 360Giving data file, a file from which the data was converted, or an organisation website.|string|False|


### Additional tables

The grants sheet can only accommodate one-to-one relationships. For example, one classification or location per grant. It also only includes common information.

To provide details of additional classifications, locations, events, documents, organization and transaction information you can use the other tabs of the spreadsheet. 

In the first column of each tab you would enter the identifier of the grant to which the additional information relates, as recorded in the id column of the grant sheet. 

#### Classification

|Title|Description|Type|Required|
|----|----|----|----|
|Vocabulary|A vocabulary used for this classification.|string|False|
|Code|A codelist value in the chosen vocabulary.|string|False|
|Title|The title of this classification.|string|True|
|Description|A description of this classification.|string|True|
|URL|A web link to more details of this classification.|string|False|
|Last modified|When was this grant classification information last modified? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


#### Location

|Title|Description|Type|Required|
|----|----|----|----|
|Identifier|Location identifier|string|True|
|Name|A name for this location.|string|False|
|Country Code|The ISO Country Code of the location of this activity.|string|False|
|Latitude|The latitude of a point location|string|False|
|Longitude|The longitude of a point location|string|False|
|Description|A description of this location. This could include details of the element of the activity that takes place here.|string|True|
|Geographic Code|A code referring to a geographical area, drawn from an established gazetteer. For example, the code for a local authority ward, or parliamentary constituency.|string|False|
|Geographic Code Type|The type of Geographic Code (geoCode) used (e.g. Ward, Parliamentary Constituency etc.). This value for this field should be drawn from the [codelist of geographic code types](https://github.com/ThreeSixtyGiving/standard/tree/master/codelists/geoCodeType.csv).|string|False|
|Last modified|When was this location information last modified? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


#### Documents 

|Title|Description|Type|Required|
|----|----|----|----|
|Identifier|An identifier for this document.|string|True|
|Title|The document title.|string|True|
|Web Address|The URL of the document.|string|False|
|Description|A description of the document.|string|True|
|Document Type|A document category. For example, 'Application Form', 'Photo' or 'Project Report'. In future, 360Giving will provide a codelist of document types.|string|False|
|Last modified|What was this information last modified? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


#### Event

|Title|Description|Type|Required|
|----|----|----|----|
|Title|The title of this event|string|True|
|Start Date|All events should have a start date. Dates should be in YYYY-MM-DD or date-time format. If the month or day are not available, these may be omitted.|string|False|
|End Date|Events or activities lasting more than one day should have either a duration (in months) or an end date. Dates should be in YYYY-MM-DD or date-time format. If the month or day are not available, these may be omitted.|string|False|
|Duration (months)|Events or activities lasting more than one day should have either a duration (in months) or an end date.|string|False|
|Description|A description of this event|string|True|
|Last modified|When was information about this event last modified? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


#### Organization

|Title|Description|Type|Required|
|----|----|----|----|
|Identifier|A globally unique identifier for this organisation. This is important to enable data on funders and recipients to be linked up across different grant-makers. The [Organisation Identifier Standard](http://www.threesixtygiving.org/standard/identifiers/#toc-organisation-identifier) guidance explains how to create this ID, based either on the known company or charity number, or upon identifiers held in the grant-maker's internal systems.|string|True|
|Name|Organisation name|string|False|
|Department|The department or sub-unit of this organisation making or receiving the grant.|string|False|
|Contact Name|-|string|False|
|Charity Number|Registered charity number, if applicable.|string|False|
|Company Number|Registered UK company number, if applicable.|string|False|
|Street Address|Building number and street name.|string|False|
|City|City or town.|string|False|
|County|County|string|False|
|Country|Country|string|False|
|Postal Code|Postal code (please try and provide a post code whenever possible)|string|False|
|Phone Number|Contact phone number.|string|False|
|Alternate Name|An alternative name for this organisation (e.g. trading name)|string|False|
|Email|-|string|False|
|Description|A short description of this organisation and its area of work|string|True|
|Organisation Type|A description of this organisation|string|False|
|Web Address|A web address for the Organisation|string|False|
|Last modified|When was the organisation information for this grant last modified? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


#### Transaction

|Title|Description|Type|Required|
|----|----|----|----|
|Identifier|Identifier|string|True|
|Transaction date|When did this transaction take place? The date should be written as YYYY-MM-DD, or in full date-time format.|string|False|
|Currency|The currency used in amounts. The currency used in amounts. Use the three-letter currency code from [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) eg: GBP|string|True|
|Value|The total value of this transaction.|integer|False|
|Value date|The date that this value was set (to allow historical currency conversion). The date should be written as YYYY-MM-DD, or in full date-time format.|string|False|
|Description|A description of this transaction.|string|True|
|Provider|The organisation identifier of the provider of transaction funds.|string|False|
|Recipient|The organisation identifier of the recipient of transaction funds.|string|False|
|Last modified|When was information about this transaction last updated? A full date-time should be given. Usually this can be generated automatically by the software managing or exporting this data.|datetime|False|


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

|Title|Name|Type|
|----|----|----|
|Identifier|id|string|
|Title|title|string|
|Description|description|string|
|Currency|currency|string|
|Amount Applied For|amountAppliedFor|number|
|Amount Awarded|amountAwarded|number|
|Amount Disbursed|amountDisbursed|number|
|Award Date|awardDate|string|
|URL|url|string|
|Planned Dates:Start Date|plannedDates[]/startDate|string|
|Planned Dates:End Date|plannedDates[]/endDate|string|
|Planned Dates:Duration (months)|plannedDates[]/duration|string|
|Recipient Org:Identifier|recipientOrganization[]/id|string|
|Recipient Org:Name|recipientOrganization[]/name|string|
|Recipient Org:Charity Number|recipientOrganization[]/charityNumber|string|
|Recipient Org:Company Number|recipientOrganization[]/companyNumber|string|
|Recipient Org:Street Address|recipientOrganization[]/streetAddress|string|
|Recipient Org:City|recipientOrganization[]/addressLocality|string|
|Recipient Org:County|recipientOrganization[]/addressRegion|string|
|Recipient Org:Postal Code|recipientOrganization[]/postalCode|string|
|Recipient Org:Country|recipientOrganization[]/addressCountry|string|
|Recipient Org:Description|recipientOrganization[]/description|string|
|Recipient Org:Web Address|recipientOrganization[]/url|string|
|Beneficiary Location:Name|beneficiaryLocation[]/name|string|
|Beneficiary Location:Country Code|beneficiaryLocation[]/countryCode|string|
|Beneficiary Location:Latitude|beneficiaryLocation[]/latitude|string|
|Beneficiary Location:Longitude|beneficiaryLocation[]/longitude|string|
|Beneficiary Location:Geographic Code|beneficiaryLocation[]/geoCode|string|
|Beneficiary Location:Geographic Code Type|beneficiaryLocation[]/geoCodeType|string|
|Funding Org:Identifier|fundingOrganization[]/id|string|
|Funding Org:Name|fundingOrganization[]/name|string|
|Funding Org:Department|fundingOrganization[]/department|string|
|Grant Programme:Code|grantProgramme[]/code|string|
|Grant Programme:Title|grantProgramme[]/title|string|
|Grant Programme:URL|grantProgramme[]/url|string|
|From an open call?|fromOpenCall|string|
|Last modified|dateModified|datetime|
|Data Source|dataSource|string|



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


