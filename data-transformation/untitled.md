# Transformations

## Why is Dynamic Querying Important?

#### Reduce the strain on your database

Many BI tools and SQL-generation platforms require their users to define strict join relationships between all of their models. They then use these definitions to generate a SQL query that will be executed in your database.  Very often these SQL generators use very simple logic to assemble their queries, usually pulling your entire data model in when generating the query. This means that they will query all of your data tables every time you run a query or load a chart instead of only fetching the data that you need for that chart. This can result in unnecessary burden on your database which in turn, results in increased costs.

Pano uses graph theory to understand all the relations between your data, it then uses this knowledge to find the shortest path \(or fewest number of tables\) to fetch the data that you ask for. If you decide to add a new aggregate table... no need to rewrite all your queries, once that table is modeled, Pano will dynamically rewrite your transformation queries to fetch the aggregate data whenever possible.

You can think of this like directions written on a map vs directions in google maps. Legacy transformation tools require you to define the route you want to take, then they just keep track of it and repeat it back to you. Panoramic constantly monitors all the relationships between your data and will always tell you the fastest route to get where you need to go.

## The Benefits of Abstract Models

In order for regular analyses to be useful, they have to be reasonably performant. If you have to wait 3 days for a query to run every time you execute it, its really going to slow down the impact of those insights \(and probably be pretty frustrating too\). To make dashboards, reports and other analyses load quickly, it is important to pre-aggregate the data in those reports, sometimes this is done through hand-written aggregation pipelines, other times its done through clever caching techniques. 

In either scenario, this means that you can have the same fields existing in multiple different tables. Impressions can live in the raw event log, the daily aggregation table and a weekly cross platform aggregation table.

If your BI tool requires you to explicitly define which model you want to select data from, then it won't be able to take advantage of any aggregated views of that data, which would reduce the query complexity and improve performance. 

By abstracting the models you allow the query service to monitor all the available models for you. This way it can find the best source of the data based on the specifics of each query. It can pull data from an aggregated table if the analysis only looks at Total Spend, but if the analysis asks for Total Spend by Age by Device by Date then the query service can dynamically rewrite the query to source data from a more granular model.



