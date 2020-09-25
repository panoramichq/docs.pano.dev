# Transformations \(Husky\)

## Why is dynamic querying important?

#### Reduce the strain on your database

Many BI tools and SQL-generation platforms require their users to define strict join relationships between all of their models. They then use these definitions to generate a SQL query that will be executed in your database.  Very often these SQL generators assemble very simple queries, which pull your entire data model in when generating the query. This means that they will query all of your data every time you run a query or load a chart, instead of \*just\* the data that you need for that chart. This can result in unnecessary burden on your database which in turn, becomes increased costs.

Updates and changes to underlying data, you shouldn't be managing the SQL scripts to aggregate your data, then you have a chain of dependencies to maintain and update all the time. The important thing is keeping your data mapped, and mapping new data, once its mapped correctly it becomes easy to reformat queries to fetch the right data from the right location

Panoramic uses graph theory to understand all the relations between your data, but then it applies clever logic to ensure that it always queries the least amount of data in order to give you the results you need. 

You can think of this like directions written on a map vs directions in google maps. Traditional systems require you to define the route you want to take, then they just keep track of it and repeat it back to you. Panoramic constantly monitors all the relationships between your data and will always tell you the fastest route to get where you need to go.

## How graph relationships benefit your data modeling?

## The benefits of abstracting Models

## How The Query Service builds queries

![](../.gitbook/assets/0%20%282%29.png)



