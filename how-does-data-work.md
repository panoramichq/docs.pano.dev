# An Introduction to Data Models

## What are Metric Tables?

Metric tables record measurements or metrics for a specific event. They generally consist of metric values and dimensions that relate to entity tables where additional descriptive attributes are stored. Metric tables are designed to a low level of granularity, meaning they can record metrics at a very atomic level. You may also hear these referred to as "Fact" tables.

### How metrics can be stored

* Lifetime Metric - this shows all the metrics that have been delivered or attributed to a specific entity over all time. For example, top-level ad group impressions are the sum of all impressions served for the ad group in one table row.
* Delta Metric - the total metric value is split across multiple rows in a column based on the set of dimensions in the table. For example, impressions by ad group by date, each row in this table would contain only the impressions served on a given date for a given ad group.
* Cumulative metric - each record includes a new value aggregated with a series of previously existing values. For example, each row would contain the sum of impressions from previous rows in addition to the current date's impressions.

Since metrics accrue over time, there are many possibilities to break metrics down by various reporting dimensions, the most common dimension is time. Panoramic uses time breakdowns heavily in being able to fetch and replay metrics.

Common time breakdowns are hourly, daily, weekly, or monthly. Panoramic reads data at the most granular time breakdown provided by each platform, this allows the system to have more flexibility when aggregating metrics for a specific analysis.

Other breakdowns that are commonly provided by platforms include geographic, demographic, and psychographic attributes. All of these breakdowns can be added to the Data Glossary within Pano. This allows our users to easily aggregate breakdown metrics across multiple datasets, allowing for easy answers to questions like, “How much have we spent toward men in the past week?” or, “How does my ROI in NY compare to LA?”

## What are Entity tables?

Entity tables usually have a relatively small number of records compared to metric tables, but each record may have a very large number of attributes to describe the fact data. You may also hear entity tables referred to as "Dimension" tables. Entities can define a wide variety of attributes that can be valuable for analysis, such as name, start date, creative type, status, price or age.

In the modern data world, it is very common to think of entities as the objects that you create across all the tools you use. This could be a campaign in Facebook, a new customer in Salesforce or a new web page in Google Analytics. Each tool will have its own set of objects that you create in order to use the service. When the data from all these tools gets pulled into your data warehouse, a mirror image of all the entities that exist in each tool becomes available in your data. The relationship between all these entities depends on the specifics of each tool, but there are usually commonalities within tools in the same space. For example, all social marketing platforms have a 3 tier hierarchy of entities that are used to define media budget and targeting. These are usually named like campaign &gt; adgroup &gt; ad and they can be combined across platforms for more robust analysis. Pano helps keep track of these relationships to make sure you can query and aggregate data correctly.

## What are "Log" or "History" tables?

These tables are common in API-driven data collection since the same piece of data may be collected multiple times by the system. Very often the system that talks to the API and collects the reporting metrics does not "know" whether a given report has already been collected. These systems will try to collect the same piece of data multiple times to ensure that they don't miss anything. It is usually best practice to collect the same piece of data multiple times because the source platform may restate the data and there may be "fresher" data if its collected again. This is commonly the case with conversions and long attribution windows, where the number of conversion events can continue to grow for up to 30 days after the user interaction.

In some cases these duplicate records are "deduplicated" by the system that collects the data, but in some cases they are not. This will result in multiple rows in your database that reflect the same piece of data. If you aggregate this information without correctly handling these duplicates, you may find errors in your analysis. Pano helps with this analysis by deduplicating log data as well as providing multiple useful aggregation types to ensure you are reporting correctly.

