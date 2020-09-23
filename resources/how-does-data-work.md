# How Does Data Work

## Data 101

#### Entities

what are they - id space in the external platform, think of something that you go and create in a platform like an account or a campaign  


Attributes - data that is associated with an entity like a name, start\_date, objective, etc  


Relationships - entities can be related to each other in many different ways, each platform decides this based on their specific use case and needs. We keep track of these relationships to make sure we can query and aggregate data correctly  


Metrics

Lifetime - at its most basic, this shows all the metrics that have been delivered or attributed to a specific entity  


Since metrics accrue over time, there are many possibilities to break metrics down by various reporting attributes, the most common attribute is time. Panoramic uses time breakdowns heavily in being able to fetch and replay metrics \(historical and into the future\)  


Common time breakdowns are hourly, daily, or monthly. Panoramic fetches data at the most granular time breakdown provided by each platform, this allows us to aggregate metrics up in the most flexible ways to make custom analysis more functional  


Other common breakdowns that are commonly provided by platforms are based on geographic, demographic and psychographic attributes. Whenever possible panoramic pulls breakdown metric reporting at these levels as well.  


These common breakdowns allow panoramic to utilize its data glossary and data mapping functionality to map breakdowns across platforms. This allows our users to easily aggregate breakdown metrics across their marketing platforms, allowing for easy answers to questions like “how much have we spent toward men in the past week?” or “how does my ROI in NY compare to LA?”  


## Data 201

Collection - how we collect data, how often it refreshes, how refresh intervals work with time breakdowns, overwriting data within specific windows and adding new buckets  


What is a record or “bucket” of data  


Lookback windows, how do we replay old data  


Fetching historical data when accounts are added  


Attribution windows, how attributed metrics like conversions accrue over time. How we replay old metrics to ensure we collect all the conversions. impression/click timestamp vs conversion timestamp attribution, we pull based on the conversion timestamp so you will see conversion trickle in even after media stops running. This trickle could go for as many days as your defined attribution window on the platform is configured \(usually something like 1 day post view 28 day post click\)  


