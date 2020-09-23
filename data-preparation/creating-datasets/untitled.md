# Data Models

## What are model files?



## Mapping Fields

#### Linking fields across models

Panoramic query engine operates by building a graph of all of your underlying data. Very often when working with metric reporting data, you will have multiple tables that include the same conceptual field, just aggregated at different levels. For example, you may have a web analytics table that includes every transaction that has occurred on your website. Each of these events has an attribute for transaction revenue. You may also have a job that aggregates this data to the daily level to show total transaction revenue by day. Both of these transaction revenue columns conceptually represent the same metric, each one is just aggregated with a different set of dimensions. If panoramic sums transaction revenue across all rows from each of these tables, it should get the same total transaction revenue for your organization.

This is the concept behind linking fields. Any fields that conceptually represent the same data should be linked and are then referred to as a single “field” from then on in the panoramic system. Panoramic’s query service will determine which underlying table is the best one to use to fetch the necessary data based on the model that each user requests. This means that the most important step of a successful panoramic integration is properly linking fields.

Linking fields in panoramic is easy, in the model files you just need to map all the data columns to the same field slug. Once the same field slug is mapped to multiple data\_references, that will tell panoramic that all those columns across all those models represent the same data.

* When panoramic scans your data connection it automatically maps every column and creates a field with the same name to map the column to.
* This works the opposite way too, if two columns of data that are not supposed to be linked have the same name, then they will be linked. So common db column names like “id” or “name” will link fields that may not represent the same data. When this happens its important to review and clean up your model mapping. This can be done by updating the name of the field slug that a data\_reference is mapped to. When in doubt, use a unique name that is not linked to any other models. You can always return to your model mapping and clean it up if you find that two columns are linked when they shouldn’t be, or two columns need to be linked
* A common practice is to prepend common db column names with the model they belong to, so if you have an “id” column in your “campaign” table, then the field should be named “campaign\_id”.
* Common db terms that we recommend prepending with the model name are: id, name, type, status, updated\_at, created\_at

#### Partial datasets

Sometimes there are scenarios where two metrics tables may contain the same metric but, for some reason, one table does not contain a complete set of data. The rule of thumb for metrics is - if i aggregate that metric, without any dimensions, i should get the same results from all models that include the metric. This rule breaks if you create a table that includes only data for a subset of days, or only for a few campaigns. In these scenarios you should not link the metrics in these tables and instead keep them unlinked and specific to the model. So if the model is called “video\_campaign\_metrics” and includes metric columns for spend and impressions, these fields should not be linked to your global spend and impressions and should instead be defined like “video\_campaign\_spend” and “video\_campaign\_impressions”. This aligns with our core rule that all data that a field is linked to should represent the same conceptual data.

#### Transforming columns

Very often when working with data, especially data that may be outside of your control, you will find slight nuances between tables. Sometimes columns are named differently, sometimes the units are different \(microdollars vs dollars\), etc. These can be a real pain to change in the underlying dataset since there may be downstream dependencies. However, with pano model transformations, you can take advantage of the panoramic suite of functions to virtually transform this data without effecting the underlying database. When you define these rules once in the modeling layer, you no longer need to worry about them later on in your reporting stack… no more converting reporting timezones from different platforms, or remembering to convert microdollars to dollars for that one platform. Set it up once in the model and forget about it.

* Ex:
  * Spend = “spend\_micro / 1000000”
  * Link\_clicks = “app\_clicks + web\_clicks”
  * My\_Leads = IFF\( action\_name = “lead”, value, null\)

#### Mapping multiple fields to the same column

In more advanced scenarios, you may find that you want the ability both to link a field to its references in other models, as well as reference the column in the model individually for some special analysis. This is supported by the ability to map a single data column to multiple fields. To do this you just need to list out all the fields that you want in the field\_map in the model file.

This could look something like a model called daily\_metrics with a column called impressions. The impressions column could be mapped to the global “impressions” field which is mapped to multiple columns across multiple tables as well as a new field called “daily\_metric\_impressions” that points only to this one, single column.

## Defining Identifiers

#### What is an identifier?

Identifiers are used to mark the compound keys on a model. Concatenating the set of identifiers for a model creates a unique “compound” ID that can be used to remove duplicates from a model. Identifiers are also used to assemble queries, where panoramic tries to query models with fewer identifiers first since they are generally smaller, more aggregated datasets.

Identifiers should always be set as dimension type fields since a metric should not be used to uniquely identify a table row

Every model with greater than 1 row of data should have at least one identifier defined. In order for queries to function properly and aggregate data correctly it is crucial to review the identifiers on every model and ensure they match the underlying data structure.

#### Defining fields as identifiers

* In the CLI, there is a block of each model file for identifiers, this block accepts an array of one or more fields. The fields listed in the array must exist and be mapped in the respective model, if you try to add identifiers that do not exist in the model then you will see an error message.
* In the UI, in the model details table you will see an icon for identifiers to show which fields are flagged as identifiers in the model. You can enable additional fields as identifiers or disable existing identifiers. You must click save when you’re done to publish your changes.

#### Identifier auto-scan

Panoramic offers an identifier-detection model that scans the underlying data in a model to interpret which field combinations can be used to uniquely define a row. This combination of fields is the same as the set of identifiers so the output of the model sets the identifiers for you. THis is very helpful if you are not the author of the underlying data table and are not intimately familiar with the data and how it works.

## Defining Joins

#### What is a join?

#### Linking dimensions vs Joining Dimensions

#### Starting with the fact/metric tables and join up to the dimension/entity tables

Panoramic is designed to write all queries starting with the metric tables, this helps ensure two things:

* first, if you just want to query some metrics, this approach limits the number of joins required \(and query complexity\) in order to return an answer, this makes queries run faster since we’re dynamically querying only the tables that include the data we’re asking for
* Second, this helps ensure that some metrics don’t get lost when traversing the entity tree from top level entities down to granular metrics reports. When fetching thousands of reports from a reporting API every day, sometimes certain reports can experience delays, by starting all queries from the metrics we ensure the greatest chance of returning the most accurate and up-to-date metrics, even if some entity reporting hasn’t been refreshed yet.

#### Types of joins

* Left
* Right
* Inner

#### Cardinality

* Many\_to\_one
* One\_to\_one
* One\_to\_many
* Many\_to\_many

#### Multiple fields in a join

#### Join auto-scan

