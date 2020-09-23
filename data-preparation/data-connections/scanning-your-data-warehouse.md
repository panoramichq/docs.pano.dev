# Scanning your data warehouse

## Scanning Your data

#### First time scan

* After you’ve set up a new data warehouse connection in the platform by adding authentication credentials, Panoramic needs to scan that warehouse to ensure we can access the warehouse and that we have permission to query all the tables you need for your analysis.
* Upon adding a new data connection, Panoramic will automatically run an initial scan on the connection to discover all of the tables that are available. This process can take up to an hour depending on the number of tables in your connection and the volume of data in each table. You can monitor the status of this scan in the connection details screen of the new connections

#### Subsequent Scans

* Since connection scans can take some time, and are only needed when the underlying tables change, Panoramic does not run automated scans on your underlying data. This is beneficial as it will lower your data warehouse costs, but it has the side effect that you need to re-scan your data connection whenever an underlying change takes place.
* When you do run a subsequent scan on your data connection, the scanned models will be automatically updated and available within that connection, these models will:
  * Add any new tables that were discovered in the data connection
  * Remove any models that no longer exist in the underlying connection
  * Update the columns discovered in each of the models

## Types of scans

#### Full scan

A scan of the entire data connection and all of the contents within, this is also known as a “deep scan” and can take up to an hour to complete. This type of scan is run when the connection is first added and this is the only type of scan that is available through the Panoramic UI

#### Filtered scan

A filtered scan allows the user to define regex-style filters to apply when scanning the connection. These filters limit the number of tables scanned to only include the subset that matches the filter logic. Filtered scans are great if you know that a change was made to your “facebook” schema so you want to update your facebook models but not take the time to rescan the rest of your data. A filtered scan can only be performed directly through the CLI at this time.

## Output - “Scanned” folder - what’s in there?

* All of these scans will update the contents of the “scanned” folder. Do not edit the files in the scanned folder directly, that is a representation of the state of your data warehouse at the time of the last scan. Re-running a scan will update the files in the scanned folder to reflect new tables or added/removed columns
* You can scan your data warehouse as many times as you need and you will always have the scanned folder as an output of what exactly was discovered in your warehouse
* In the UI, the contents of the scanned folder can be found in the data connection details view, which shows a list of all the models discovered during the scan

