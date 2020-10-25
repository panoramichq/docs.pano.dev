---
description: Dimensions and Metrics
---

# Fields

## Attributes of a field

#### Field Slug

just as we do with models, every field is defined by a unique, human readable slug. This field never changes once its created and must be globally unique across your company. The field slug is what users see when working with the CLI and directly in model files. You can also see the slug in the URL when viewing field details. However, in general, the slug is there so that the system functions correctly.

#### Mapped Fields vs Calculated Fields

Mapped fields are created automatically by the database scan but they can also be created manually if needed. Mapped fields are the lowest level in the calculation hierarchy because all mapped fields reference specific columns in the data warehouse. Mapped fields must all have a data type declared for validation purposes as well as an aggregation type declared \(if its a metric\) so that Pano knows how to aggregate the data.

Calculated fields are different then mapped fields because calculated fields always reference other fields that already exist in Pano. You can think of calculated fields like custom dimensions and metrics that you derive based on other existing pieces of data.

* Ex: a data warehouse has columns date, impressions and clicks. Each of these three columns would be associated with a corresponding mapped field. If you wanted to then create a custom metric like “Click through rate” then you would create a calculated field that is derived from clicks and impressions via a calculation "clicks / impressions"

#### Field Type

Dimensions - dimensions are fields where you want all unique values displayed in your output models. This means that dimension fields are not aggregated in any way and are, instead, used to group data by. In SQL you can think of dimensions as the list of columns included in thee GROUP BY clause of your SELECT statement

Metrics - Conversely, metric fields are any fields that are not dimensions. Metrics are aggregated in some way by a set of dimensions, some common aggregation types are sum, count, average, etc. Metrics must have an aggregation type defined or they will be treated as dimensions. Metrics can be divided, grouped or split based on any number of available dimensions, often these different aggregations are stored in permanent or temporary tables. The panoramic query service will dynamically choose the best table to source metrics from based on the set of dimensions the user requests.

#### Data type

Data type appears in two locations in Pano and is used to declare and validate that all the values for a given field match the defined type, e.g. if data type is set to number, then the panoramic system will assert that all of the values are numbers and throw an error if it finds a string value

* Source Data Types - Data Type in scanned model files is extracted directly from the data connection and is a read-only reference to show the defined column type in the underlying data warehouse. Pano never alters the underlying model data so this field is available strictly for helpful context
* Data type - In pano, users are able to redefine the data type of a given field. This allows users to take advantage of additional data types that are not supported by databases. Common use cases are to define data type as money or percent which then tells panoramic to add a currency symbol or to multiple by 100 when displaying the values

This also allows Pano to convert a value from one type to another at query time. Sometimes you have a number, like budget, that is part of a string. You can use functions to parse out the budget and then convert it to a numeric money type so that the values can be safely aggregated.

#### Aggregation type

In order for a field to be treated as a metric, it must have an aggregation type defined. A complete list of aggregation types can be found on the [**Functions & Calculations**](functions-and-calculations.md) page.

Aggregation type can only be defined on mapped fields and each mapped field can be defined with one and only one aggregation type. All calculated fields are derived from mapped fields and inherit the aggregation type of the underlying mapped fields.

* Ex: I have two columns in my underlying data table, one for “spend” and one for “clicks”. I create one field called “spend” that maps to “spend” and has aggregation type = SUM and a second field called “clicks” that maps to “clicks” and has an aggregation type = SUM. I can now build a model with date, spend & clicks and Pano will implicitly SUM\(spend\) and SUM\(clicks\) in the model.
* Now, if I create a calculated field called “Cost per Click” I will define the calculation as “spend / clicks”. Whenever users are building models, Pano will implicitly aggregate the metrics prior to applying calculations, so the SQL for this calculation will evaluate to SUM\(spend\) / SUM\(clicks\)

#### Calculation

The calculation field tells Pano what logic to apply in order to derive the field. Field calculations are always applied in order, so if Field B has a calculation that includes Field A, then Field A's calculation will be executed and then the results will be passed into Field B. 

Pano works very similar to excel where you can apply multiple functions to transform data however you need it. See the page on [**Functions & Calculations**](functions-and-calculations.md) for complete details

#### Display Formatting

Every field has a number of additional attributes, or helpful “metadata” that are available to define field formatting and help users understand what the field means.

* **Display name -** The display name is the editable name for each field. This name can be nicely formatted and include special characters. The purpose of the display name is so to reference fields in a way that’s most familiar to your company. So if Facebook calls them AdSets and Snap calls them AdSquads, but in your company you call them all AdGroups, you can use display name to simplify the naming so you don’t need to retrain everyone in your organization.
* **Abbreviation -** Abbreviation is available to set in case there are common industry acronyms for certain fields, this can come in handy when displaying tables with many columns, Pano will display the abbreviation instead of the long name. This is also great for search, so users can search for “CPM” even if the field has a display name of “Cost per Thousand Impressions”.
* **Description -** The field description is available to give users a thorough explanation of each field, what it means, where it comes from and any other relevant information that could be useful to end users who may not be as familiar with the data
* **Group -** This is a customizable, self-defined group that allows you to categorize similar fields so they are better organized and easier to find when building models. Some common groups include “Video engagement”, “social”, “geographic”, etc
* **Units & symbols -** A growing set of display formatting options is available to tailor exactly how specific fields are displayed in Dataframes. These can include standard factors like significant figures and addition of % or currency symbols, but will also expand into displaying hyperlinks, creative thumbnails and other useful visual formatting of common data types.

## **Creating a New Field**

![Create \| Edit Form for Fields](https://downloads.intercomcdn.com/i/o/207471634/5edb365769ddc83260d29545/image.png)

Once you’ve published a dataset you can also create any fields that might be useful to your company. 

#### To Create a Custom Field:

1. Log in to your Panoramic account
2. Navigate to your Company Settings by selecting the **COMPANIES** tab from your home screen \(Admins only\)
3. Under your Company Settings Menu, navigate to the **GLOSSARY** tab
4. Select **CREATE TERM** on the far right of the Glossary screen
5. Enter the **NAME** and **DESCRIPTION** of your Custom Field in the Create Field popup. The **Name** you provide will appear wherever your Field is used again.
6. Select whether your Field is a **METRIC** or **DIMENSION**
7. Select the **DATA TYPE** \(Data type is dependent on whether you are creating a dimension or a metric\)
   * **Text** - is a text field, such as Region \(e.g. CALIFORNIA\)
   * **URL** - is a link, such as Website URL \(e.g. [https://panoramichq.com](https://panoramichq.com/)\)
   * **Boolean** - has a value that is either ‘TRUE’ or ‘FALSE’
   * **List** - includes several values, such as Age Buckets \(10-20, 21-30, 31-40, etc.\)
   * **Number** - is a number, such as Video Views
   * **Duration** - is an amount of time, such as Average Session Duration
   * **Percent** - is a percent, such as Bounce Rate
   * **Money** - is a value indicating currency, such as Spend or Average Order Value \(or AOV\)
8. If you selected **METRIC** and you are creating a mapped field then you must choose an aggregation type. See [**Functions & Calculations**](functions-and-calculations.md) for a full list of Aggregations.
9. Select **CREATE** to save your Custom Field and add it to any of your Boards.

