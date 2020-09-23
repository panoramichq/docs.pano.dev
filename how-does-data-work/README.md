# An Introduction to Data Analysis

## Common Database Structures

Databases - cloud vs on-premise

Schemas

Tables

Views

Columns

## What are Metric tables?

You may also hear these referred to as "Fact" tables. 

#### How metrics can be stored

* A top-level metric is a metric totaled over its entire entity. So for example, a top-level ad group impressions is the sum of all impressions for the ad group.
* Delta Metric - the total value is split across multiple rows in a column based on the set of dimensions in the table
* Cumulative - each record includes a new value aggregated with a series of previously existing values 

Lifetime - at its most basic, this shows all the metrics that have been delivered or attributed to a specific entity

Since metrics accrue over time, there are many possibilities to break metrics down by various reporting attributes, the most common attribute is time. Panoramic uses time breakdowns heavily in being able to fetch and replay metrics \(historical and into the future\)

Common time breakdowns are hourly, daily, or monthly. Panoramic fetches data at the most granular time breakdown provided by each platform, this allows us to aggregate metrics up in the most flexible ways to make custom analysis more functional

Other common breakdowns that are commonly provided by platforms are based on geographic, demographic and psychographic attributes. Whenever possible panoramic pulls breakdown metric reporting at these levels as well.

These common breakdowns allow panoramic to utilize its data glossary and data mapping functionality to map breakdowns across platforms. This allows our users to easily aggregate breakdown metrics across their marketing platforms, allowing for easy answers to questions like “how much have we spent toward men in the past week?” or “how does my ROI in NY compare to LA?”

## What are Entity tables?

An entity is a thing you can take a measurement of. Some common ones are account, campaign, ad group, ad, and creative. These are the “things” that we measure the marketing performance of.

You may also hear these referred to as "Dimension" tables. 

what are they - id space in the external platform, think of something that you go and create in a platform like an account or a campaign

Attributes - data that is associated with an entity like a name, start\_date, objective, etc

Relationships - entities can be related to each other in many different ways, each platform decides this based on their specific use case and needs. We keep track of these relationships to make sure we can query and aggregate data correctly

## What are "Log" or "History" tables?

These tables are common in API-driven data collection since the same piece of data may be collected multiple times by the system. Very often the system that talks to the API and collects the reporting metrics does not "know" whether the report its asking for has already been collected. These systems will try to collect the same piece of data multiple times, sometimes to account for API issues or missing it the first time, sometimes because data may be restated and there may be "fresher" data if we collect it again, this is commonly the case with conversions and long attribution windows, where the number of conversion events can continue to grow for up to 30 days after the user interaction.

In many cases these duplicate records are "deduplicated" by the system that collects the data, but in some systems, or in some cases they are not and instead you will have multiple rows in your database that reflect the same piece of data. If you aggregate this info without correctly handling these duplicates, you may find errors in your analysis, like counting how many creatives were running, or summing spend for a given day. 

## Basics of Data Collection

Collection - how we collect data, how often it refreshes, how refresh intervals work with time breakdowns, overwriting data within specific windows and adding new buckets

What is a record or “bucket” of data

Lookback windows, how do we replay old data

Fetching historical data when accounts are added

Attribution windows, how attributed metrics like conversions accrue over time. How we replay old metrics to ensure we collect all the conversions. impression/click timestamp vs conversion timestamp attribution, we pull based on the conversion timestamp so you will see conversion trickle in even after media stops running. This trickle could go for as many days as your defined attribution window on the platform is configured \(usually something like 1 day post view 28 day post click\)

## What is Data Blending?

