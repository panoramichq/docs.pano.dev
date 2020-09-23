# Working with the Panoramic CLI

## Prerequisites

## Installing the CLI

The Panoramic Command line interface \(CLI\) is available publicly in the pypi project and can be installed by following the instructions here:

[https://pypi.org/project/panoramic-cli/](https://pypi.org/project/panoramic-cli/)

## Common workflow & use cases

Create a folder that you’ll use as the workspace for your company, cd into it and run

`pano configure`

This will prompt you for your credentials.

Next, run

`pano init`

and enter the slug of the company you want to set the folder up for. This will create a file called pano.yaml in your workspace folder.

Then, see all available FDQ connection slugs through

`pano list-connections`

Using a FDQ connection slug, you can run the scan command, which will create models that can fetch data from the tables in the FDQ connection. Scan can be either run on all of the resources available to the connection:

`pano scan <fdq-connection-slug>`

Since the scan takes a while, you’d usually want to limit the scan using a SQL wildcard syntax \(% is the wildcard character, in this case\)

`pano scan sf -f metrics3_stg.adwords_views.%`

At this point, you probably want to assign the model to a dataset.

**IMPORTANT** pano-cli does not safeguard against human errors in lifecycle management. Mistakes could possibly overwrite platform state for other users. Make sure to follow these steps!

Before you start working with models, make sure your folder is representing the up-to-date state of the company.

`pano pull`

Currently, creating a dataset is a bit manual-labor intensive operation. In the future, a CLI command will do it for you.

`mkdir a_cool_dataset \ && \ echo \ "dataset_slug: a_cool_dataset display_name: ACoolDataset" \ > a_cool_dataset/dataset.yaml`

In order to assign the model to the dataset, just copy it from the scanned folder to the dataset folder: 

`cp scanned/sf.metrics3_stg.adwords_views.entity_accounts.model.yaml a_cool_dataset`

In order to push the changes to the platform, just do

`pano push`

Congratulations, now you're ready to start transforming your data in the Platform!  


## Troubleshooting

