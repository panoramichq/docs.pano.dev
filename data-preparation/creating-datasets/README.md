# Datasets

## What is a dataset?

Also known as a “universe” of data, a dataset forms a group of tables that have an implicit relationship between the data. Usually all of these tables come from the same source, such as Facebook Marketing API, or Shopify API. The set of tables within a dataset have implicit joins between them, usually in the form of primary keys and foreign keys like campaign\_id or product\_id. These tables may also include

## Naming a dataset

* Datasets, like many objects in the panoramic system, are split into two parts, a slug and a display name.
* A slug is a human readable identifier that is used by our system to uniquely identify an object in the panoramic system. Slugs are always unique strings and cannot be modified once they are created.
* The Display name is the label associated with the slug that will be used for display in all platform UI elements and data models. Since the slug cannot be changed once its created, we offer the display name as the available field to use to modify how a dataset is visualized, updated and displayed for Panoramic users.
  * A common example of this idea is Google’s “Adwords” platform. You may first create a dataset to map “adwords” data and it would have a slug and display name of “Adwords”. However Google decided to rebrand its platform to “Google Ads”. In our system the dataset slug would still remain “adwords” but you can easily update the display name to “Google Ads”.
* In the UI you can create and manage datasets directly, you will not need to create a slug in the UI as one will be created for you based on the first display name you input.
* In the CLI you should create a new folder per dataset that you wish to create and name that folder with the same name as the dataset slug.
  * Once the folder is created, you should create a file called “dataset.yaml” within that folder and add values to the following keys within the file:
    * api\_version: \[v1\]
    * Dataset\_slug: \[alphanumeric\_string\_name\]
    * Display\_name: \[“My Pretty Name”\]

## Copying scanned files into datasets

In order to make the scanned models in your data connection available for modeling and querying, the files must be copied into the “scope” of a dataset. Working with the CLI this means copying the relevant model files into the dataset folder you just created. Within the UI this means navigating into the dataset detail view and clicking the “add models” button, then selecting and adding the relevant models from the list.

## Creating model files

Once you’ve copied all your scanned files into the dataset folder, you are ready to start modifying your models to meet all your reporting needs. Editing models can be done by modifying four key areas:

* Fields - the mapping between columns of data in your data warehouse and queryable “fields” in the panoramic system
* Identifiers - a definition of the identifiers, or compound keys in a model to show the Panoramic system how data is structured and how best to query it
* Joins - a definition of the relationship between multiple models. Defining joins declares which fields in each model are related \(can be JOINed in SQL terms\) and defines the relationship between the data in each model \(primary vs foreign, left or inner join\)
* Projections - the ability to transform the underlying structure of an existing table in your data connection. Sometimes this is necessary in order to structure the data in a format that is queryable by Panoramic \(such as transforming EAV structure into columnar or unpivoting an already transposed dataset\). Projections are written in pure SQL and are executed first in the data transformation process.

#### Types of models

* dimension/entity models
* fact/metric models
  * Defining the reporting date / hour field

## Publishing your Dataset

* Glossary
  * Once you are finished editing your models you can either a\) push to production via the CLI or b\) click save in the platform in order to publish all your changes and make your datasets, models and fields available for querying and model building. As soon as you publish your fields they will become available in the Platform Glossary. This is the view where you and any other member of your team can view all the data that they have access to, what that data means and how it can be used for reporting
  * When initially publishing fields, panoramic makes a few assumptions about how the field will be used based on the type of data. These assumptions are based on hundreds of thousands of tables scanned and are best practices for getting up and running quickly. With that said, these defaults will only get you started and many fields will need to be updated to better reflect the underlying data.
    * Any text or date fields will be created as dimensions by default
    * Any numeric \(decimal, float, integer\) fields will be created as metrics with an aggregation type of SUM by default
  * Once the fields are available in the glossary you are free to go in and edit any of the attributes associated with fields \(mentioned above\). One of the benefits of panoramic is that you can easily edit the meaning of fields and it will dynamically update that field everywhere in the system. This means that you do not need to go add additional logic to every table in your system that contains a piece of data...like spend.
    * We recommend reviewing the defaults on all new fields to ensure they are properly defined as a dimension or a metric, that they have the correct aggregation type and that the display formatting is properly defined.

