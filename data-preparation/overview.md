---
description: Data Preparation Overview
---

# Overview

## What is Data Preparation?

Data preparation, also known as data cleaning, is the process usually taken on by data engineers and data analysts to organize data into a format that it is easily queryable through simple SQL queries or via BI tools. 

This commonly takes form in the following ways

* Data Aggregations
* Type Casting - updating the data types to ensure they are correct and match across all tables. Sometimes metrics show up as strings, sometimes IDs show up as decimals, they need to be corrected before any further analysis can take place
* Normalizing text - making sure that names are set up the exact same across multiple systems so they can be properly joined and aggregated for reporting
* Fixing Typos - aka fixing misspellings, typos and other common user mistakes so the data matches
* structuring datasets - transforming unstructured JSON or arrays of data into easier to query, relational, columnar data tables
* Deduplication of rows - sometimes the same report is fetched multiple times from an api, If both of these reports include the same date then there is a chance the metrics could be duplicated, this is why its important to declare identifiers, which can be used to remove duplicates and only query the latest, most up-to-date version of a specific report

## 

## Data Preparation

> "Data preparation is a must-have technology for enabling business teams to find, prepare and share heterogeneous data for their integration, analytics and data science use cases" - Gartner

> **"Data preparation** is the act of manipulating \(or pre-processing\) raw data \(which may come from disparate data sources\) into a form that can readily and accurately be analysed, e.g. for business purposes. Data preparation is the first step in data analytics projects and can include many discrete tasks such as loading data or data ingestion, data fusion, data cleaning, data augmentation, and data delivery." - Wikipedia

## How Does Panoramic Help?

UPDATE

![UPDATE](https://files.readme.io/a29dd19-data-workflow.png)

### Datasets

Also known as a “universe” of data, a dataset forms a group of tables that have an implicit relationship between the data. Usually all of these tables come from the same source, such as Facebook Marketing API, or Shopify API. The set of tables within a dataset have implicit joins between them, usually in the form of primary keys and foreign keys like campaign\_id or product\_id. These tables may also include

### Data Projections

Pure SQL transformations applied to an existing data table to convert it into a new structure, this is commonly used to pre-aggregate raw event data, remove duplicate records from a table or to flatten rows into columns so they can be queried more easily

### Data Models

Data "modeling" can mean many things depending on the context and the language/platform you are working with. In general, data modeling is defining an abstract definition of what a set of data "means" by adding metadata to the data that is not available directly in the underlying database. This metadata is very commonly things like descriptions for what each column means, the data type, how multiple tables can be joined together, etc. 

Data modeling refers to the process of applying business logic to make sense of physical data. This process aims to:

* Consolidate data from multiple data sources
* Transform data, produce business-friendly data units, in other words, easier to query and to interpret
* Give business meaning to raw data generated from your system with metadata
* Promote data self-service and collaboration

#### Field Mapping

Panoramic works a bit differently from typical data modeling tools in that we have abstracted fields from the models where they exist. Its very common for the same field to exist in multiple tables, for example, you may have a column for "spend" that exists in your raw event table, your daily aggregated reporting table and your monthly billing table. All three of these columns represent the same conceptual field and are often even aggregated from one table up to the next. In Panoramic, we will map all three of these columns to the same "spend" field. This allows us to centralize management of the field, how it should be aggregated, formatted, what it means .... and separate this information from the actual tables where the field exists. This makes it much easier to map columns to fields, since you don't need to copy extensive metadata across multiple files, as well as much faster to update since changes to the centralized field definition instantly apply everywhere where the field is referenced. 

#### Identifiers

Identifiers are used to uniquely identify the uniqueness of a row of data in a table. Each table of data should have one or more identifiers defined. The general idea is that no two rows in a table can have the same values for the set of identifiers defined. So if I have a table and I declare "date" as the only identifier in that table, then there should only ever be one row for each date. Identifiers allow query services, like your analyst, or panoramic, to know how the data in the table is structured and what is the best way to query it.

Identifiers are commonly referred to as primary keys or compound keys. In traditional relational databases, these keys can be set in the table definition, and 9 times out of 10 those keys will match the Panoramic identifiers. But not all cloud data warehouses support implicit primary key and foreign key definitions. For these cloud warehouses you need to go and define the identifiers in the data model, even though they are not strictly enforced by the warehouse itself.

#### Joins



#### Transformations



### Self-Organizing Pipelines

* **Connect Everything, query anything**
  * Pano works with your existing data warehouses and data pipeline vendors to create a unified view of the data you need
    * time-series event data or aggregated metrics
    * On-premise databases or cloud data warehouses \(aws, azure, gcp\)
  * Your data admins can set up all the proper security guardrails. Don’t want to share sensitive metrics or PII with an external consultant, easily set up a workspace with a limited scope of metrics
* **Modernize your reporting stack**
  * Keep your data where it is and bypass the need to write your own data transformations and run long ETL batch jobs. Pano keeps track of all the data that is available and continuously optimizes queries to be the fastest and most efficient, without the need to move any data.
  * Need to add a new metric? Want to change how a metric is calculated? Don’t worry about expensive data reprocessing, Pano gives you immediate access to the new data while dynamically rebuilding your pipeline for you
    * Pano figures out exactly what analyses are possible in the data and gets an answer to the team immediately. Then we go back and optimize that pipeline as more users ask the same questions
* **The power of choice**
  * The market is evolving, the goal is to keep track of all your data so you can perform the best analysis. We focus on your ability to query and understand your data, regardless of where it comes from and how you store it. Totally agnostic:
    * **Self-serve data pipelines** - Write your own API pipelines or work with any available ETL vendor to pipe data to your managed data warehouse
    * **Managed data pipelines** - connect any of Panoramic’s managed API pipelines to instantly access cleaned data from sources you don’t already have
    * **Custom Offline datasets** - let's face it, some data just isn't modern, it lives in excel files on your computer. Upload this data into Pano and make it instantly available for unified analysis
    * **Data Pipelines 2.0** - many modern SaaS companies now offer direct extraction of data directly to your data warehouse. Pano connects directly to this data and makes it instantly queryable.

