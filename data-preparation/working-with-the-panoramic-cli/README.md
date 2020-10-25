---
description: Getting started with the CLI
---

# Pano CLI

## Prerequisites

* Python3

## Installing the CLI

The Pano Command line interface \(CLI\) is available publicly on PyPI and can be installed by following the [Installation instructions](installation.md).

## Setting up the CLI

In order to use the CLI, you need to configure it. This only needs to be done one time. Don't worry - you can run the`pano configure` command multiple times if you need to change your user or credentials.

To configure the CLI, run this:

`pano configure`

This command will prompt you for your API credentials. If you don't have them, [login to Pano and generate them](../../getting-started/your-profile.md#generating-an-api-token).

The configure command will create a directory called`.pano` in your home directory. All configuration information will be contained in that directory. If you ever need to reset the configuration of the CLI, simply remove the directory from your system.

## Common workflow & use cases

Create a folder that you’ll use as the workspace for your company, cd into it and run

Next, run

`pano init`

and enter the slug of the company you want to set the folder up for. This will create a file called pano.yaml in your workspace folder.

Then, see all available FDQ connection slugs through

`pano list-connections`

Using a FDQ connection slug, you can run the scan command, which will create models that can fetch data from the tables in the FDQ connection. Scan can be either run on all of the resources available to the connection:

`pano scan <connection-slug>`

Since the scan takes a while, you’d usually want to limit the scan using a SQL wildcard syntax \(% is the wildcard character, in this case\)

`pano scan sf -f stg.adwords_metrics.%`

At this point, you probably want to assign the model to a dataset.

\*\*\*\*⚠ _**IMPORTANT** The CLI does not safeguard against human errors in lifecycle management. Mistakes could possibly overwrite platform state for other users. Make sure to follow these steps!_

Before you start working with models, make sure your folder is representing the up-to-date state of the company.

`pano pull`

Create a dataset by creating a new directory and adding a dataset file inside. Running the following command will help:

`mkdir a_cool_dataset \ && \ echo \ "dataset_slug: a_cool_dataset display_name: ACoolDataset" \ > a_cool_dataset/dataset.yaml`

In order to assign the model to the dataset, just copy it from the scanned folder to the dataset folder: 

`cp scanned/db.stg.adwords_metrics.entity_accounts.model.yaml a_cool_dataset`

In order to push the changes to the platform, just do

`pano push`

Congratulations, now you're ready to start transforming your data in the Platform!

