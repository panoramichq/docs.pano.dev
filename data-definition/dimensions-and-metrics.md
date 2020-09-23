---
description: Dimensions and metrics
---

# Fields

## What is a field?



### Attributes of a field

#### Field Slug

just as we do with models above, every field is defined by a unique, human readable slug. This field never changes once its created and must be globally unique across your company. The field slug is what users see and work with when working with the CLI and directly in model files. You can also see the slug in the URL when viewing field details. However, in general, the slug is there so that the code works correctly and the platform should use the display name in almost all scenarios.

#### Dataset Fields vs Blended Fields

Dataset fields are created automatically through the database scan feature but they can also be created manually if a user desires. Mapped fields are the lowest level in the calculation hierarchy because all mapped fields reference specific columns in the data warehouse. Mapped fields must all have a data type declared for validation purposes as well as an aggregation type declared \(if its a metric\) so that the Panoramic system knows how to aggregate the data.

Blended fields are different then mapped fields because custom fields all reference other fields that exist in the system. You can think of custom fields like custom dimensions and metrics that you derive based on other existing pieces of data.

* Ex: a data warehouse has columns date, impressions and clicks. Each of these three columns would be associated with a corresponding mapped field. If you wanted to then create a custom metric like “Click through rate” then you would create a custom field that is derived from clicks and impressions via a calculation clicks / impressions

#### Blended Fields

One of the biggest benefits of using Panoramic as your marketing visualization tool, is all the work our teams do to pre-map and model the metrics and dimensions we pull in from the marketing platforms you connect. 

Some metrics that we pull in exist in multiple platforms, and are mapped together "out of the box", those are one of our **Global taxons.** 

Example: "Marketing Spend" exists in Facebook, Twitter and Snapchat. When you select Marketing Spend in Explore mode, it will automatically map across all 3 of those platforms. 

However, in order to enable [**Data Blending**](http://help.panoramichq.com/en/articles/3999904-data-blending-part-1) the Panoramic Glossary generates **NameSpaced Taxons** for every metric, for every platform that it exists on. 

Marketing Spend = Global Taxon  
\(Facebook Ads\) Spend= Namespaced Taxon  
\(Twitter\) Spend = Namespaced Taxon  
\(Snapchat\) Spend = Namespaced Taxon

By breaking out the metric by platform, it allows you to create [**Custom Terms**](http://help.panoramichq.com/en/articles/4043962-custom-terms) with much greater flexibility.

#### Field Type

Dimensions - dimensions are fields where you want all unique values displayed in your output models. This means that dimension fields are not aggregated in any way and are, instead, used to group data by. In SQL you can think of dimensions as the list of columns included in thee GROUP BY clause of your SELECT statement

Metrics - Conversely, metric fields are any fields that are not dimensions. Metrics are aggregated in some way by a set of dimensions, some common aggregation types are sum, count, average, etc. Metrics must have an aggregation type defined or they will be treated as dimensions. Metrics can be divided, grouped or split based on any number of available dimensions, often these different aggregations are stored in permanent or temporary tables. The panoramic query service will dynamically choose the best table to source metrics from based on the set of dimensions the user requests.

#### Data type

Data type appears in two locations in the panoramic system and is used to declare and validate that all the values for a given field match the defined type, e.g. if data type is set to number, then the panoramic system will assert that all of the values are numbers and throw an error if it finds a string value

Model Data Types - Data Type in scanned model files is extracted directly from the data connection and is a read-only reference to show the defined column type in the underlying data warehouse. Panoramic never alters the underlying model data so this field is available strictly for helpful context

Field data type - In panoramic, users are able to redefine the data type of a given field.

* This allows users to take advantage of additional data types that are not supported by databases. Common use cases are to define data type as money or percent which then tells panoramic to add a currency symbol or to multiple by 100 when displaying the values
* This also allows panoramic to convert a value from one type to another at query time. Sometimes you have a number, like budget, that is part of a string. You can use functions to parse out the budget and then convert it to a numeric money type so that the values can be safely aggregated.

#### Aggregation type

In order for a field to be treated as a metric, it must have an aggregation type defined. A complete list of aggregation types can be found in THIS ARTICLE on supported functions.

Each field can be defined with one and only one aggregation type

Aggregation type can only be defined on mapped fields, all custom fields are derived from mapped fields and inherit the aggregation type of the underlying mapped fields.

* Ex: I have two columns in my underlying data table, one for “spend” and one for “clicks”. I create one field called “spend” that maps to “spend” and has aggregation type = SUM and a second field called “clicks” that maps to “clicks” and has an aggregation type = SUM. I can now build a model with date, spend & clicks and panoramic will implicitly SUM\(spend\) and SUM\(clicks\) in the model.
* Now, if I create a custom field called “Cost per Click” I will define the calculation as “spend / clicks”. Whenever users are building models, panoramic will implicitly aggregate the metrics prior to applying calculations, so the SQL for this calculation will evaluate to SUM\(spend\) / SUM\(clicks\)

#### Calculation

For blended fields, this is where you can define and store the logic for how the field should be calculated. Pano works very similar to excel where you can apply functions to transform data however you need it.

See the page on functions & calculations for complete details

#### Display formatting

Every field has a number of additional attributes, or helpful “metadata” that are available to define field formatting and help users understand what the field means.

Display name - The display name is the editable name for each field. This name can be nicely formatted and include special characters. The purpose of the display name is so that you can reference fields in a way that’s most familiar to your company. So if Facebook calls them AdSets and Snap calls them AdSquads, but in your company you call them all AdGroups, you can use display name to simplify the naming so you don’t need to retrain everyone in your organization.

Abbreviation - Abbreviation is available to set in case there are common industry acronyms for certain fields, this can come in handy when displaying tables with many columns, Panoramic will display the abbreviation instead of the long name. This is also great for search, so users can search for “CPM” even if the field has a display name of “Cost per Thousand Impressions”.

Description - The field description is available to give users a thorough explanation of each field, what it means, where it comes from and any other relevant information that could be useful to end users who may not be as familiar with the data

Group - This is a customizable, user defined group that allows users to categorize similar fields so they are better organized and easier to find when building models. Some common groups include “Video engagement”, “social”, “geographic”, etc

Units & symbols - a growing set of display formatting options are available to tailor exactly how specific fields are displayed in models. These can include standard factors like significant figures and addition of % or currency symbols, but will also expand into displaying hyperlinks, creative thumbnails and other useful visual formatting of common data types.

*   <table>
    <thead>
      <tr>
        <th style="text-align:left">Format</th>
        <th style="text-align:left">
          <p></p>
          <p>Input Type</p>
        </th>
        <th style="text-align:left">Output</th>
        <th style="text-align:left"></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="text-align:left">TO_DURATION({field}, interval, [NULLIFY_ERRORS])</td>
        <td style="text-align:left">Dimension or metric, interval units for the input (hours, minutes, seconds,
          etc)</td>
        <td style="text-align:left">Metric in hours, minutes, seconds format (00:00:00)</td>
        <td style="text-align:left"></td>
      </tr>
      <tr>
        <td style="text-align:left">TO_MONEY({field}, currency, [decimals - integer, optional, default 0],
          [NULLIFY_ERRORS])</td>
        <td style="text-align:left">dimension or metric, currency, integer for decimal places</td>
        <td style="text-align:left">metric formatted with currency and decimal places</td>
        <td style="text-align:left"></td>
      </tr>
      <tr>
        <td style="text-align:left">TO_PERCENT({field}, [decimals - integer, optional, default 0], [NULLIFY_ERRORS])</td>
        <td
        style="text-align:left">dimension or metric, integer for decimal places</td>
          <td style="text-align:left">metric multiplied by 100 with % and decimal places added</td>
          <td style="text-align:left"></td>
      </tr>
      <tr>
        <td style="text-align:left">TO_LINK()</td>
        <td style="text-align:left">hyperlinks</td>
        <td style="text-align:left"></td>
        <td style="text-align:left"></td>
      </tr>
      <tr>
        <td style="text-align:left">TO_IMAGE()</td>
        <td style="text-align:left">Image rendering from URL</td>
        <td style="text-align:left"></td>
        <td style="text-align:left"></td>
      </tr>
    </tbody>
  </table>

## **Creating a new field**

Navigate to the Glossary, and click "Create Term" just like you did in Custom Terms.

Fill in all of the relevant information but this time, summing \(+\) all the platform-specific metric terms together.

example calculation: Facebook \(Initiate Checkouts\) + Twitter Conversions + Snapchat Conversions

![](https://downloads.intercomcdn.com/i/o/207471634/5edb365769ddc83260d29545/image.png)

  
  


### **Create Fields**

Once you’ve published a dataset you can also add any terms or metrics that might be measured uniquely by your organization. Some common examples of a Custom Fields include: a custom calculation for engagement rate that might be industry-specific, applying an internal formula that incorporates how your business determines profitability, or re-labeling existing fields in the vernacular that is most familiar to your team.

#### To Create a Custom Term:

1. Log in to your Panoramic account
2. Navigate to your Company Settings by selecting the **COMPANIES** tab from your home screen
3. Under your Company Settings Menu, navigate to the **GLOSSARY** tab
4. Select **CREATE TERM** on the far right of the Glossary screen
5. Enter the **NAME** and **DESCRIPTION** of your Custom Term in the Create Term popup. The **Name** you provide will appear wherever your Term is used again \(e.g. in Custom Charts, Reports, etc.\)
6. Select whether your Term is a **METRIC** or **DIMENSION**
7. Select the **DATA TYPE**
   * If you selected **DIMENSION,** the four **DATA TYPES** available are:
     1. **Text** - is a text field, such as Region \(e.g. CALIFORNIA\)
     2. **URL** - is a link, such as Website URL \(e.g. [https://panoramichq.com](https://panoramichq.com/)\)
     3. **Boolean** - has a value that is either ‘TRUE’ or ‘FALSE’
     4. **List** - includes several values, such as Age Buckets \(10-20, 21-30, 31-40, etc.\)
   * If you selected **METRIC,** the four **DATA TYPES** are:
     1. **Number** - is a number, such as Video Views
     2. **Duration** - is an amount of time, such as Average Session Duration
     3. **Percent** - is a percent, such as Bounce Rate
     4. **Money** - is a value indicating currency, such as Spend or Average Order Value \(or AOV\)
   * If you selected **METRIC,** the two **AGGREGATION TYPES** depend on whether the value can stand alone or is dependent on another value to be calculated.
     1. **Summary** - is simply a summary, and does not depend on any other value.
     2. **Ratio** - relies on other values, but does not need to be calculated within Panoramic. Examples of Ratio Metrics include Cost Per Click \(or CPC\) or Click Rate.
8. Select **CREATE** to save your Custom Field and add it to any of your Boards.

