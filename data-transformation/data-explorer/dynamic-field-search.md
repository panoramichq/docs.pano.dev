# SmartSearch for Fields

Panoramic abstracts the Models so you don't have to worry about updating queries and dependencies. This approach makes it simpler for users who are not familiar with data, databases, or your underlying schema to still perform an analysis safely, without calculating something incorrectly, or having to take the time to learn what fields are in every table. Data engineers and analysts can focus on the underlying data model, to ensure everything is defined correctly, joined and exposed, and the business team can be free to explore the data in a safe and easy manner.

Pano's Field Selector dynamically updates as you add each field to your Dataframe. Based on the underlying data model, Pano "knows" which relationships can be formed between multiple models, or dimensions and metrics. The field selector will automatically enable or disable available fields based on the set that you have already selected. 

## Tips & Tricks

* Start every analysis by first pulling in the dimensions or metrics that you care about most. If spend is the most important metric, then add spend to your exploration. The field selector will then automatically update by removing any metrics or dimensions that cannot be analyzed with spend.
* If you are performing an analysis and one of the fields that you are interested in is disabled, try removing some of the fields you have already added until the field becomes available again.
* Dimensions have the most impact on which fields can be included in an analysis, since dimensions are what we use to define the relationships between models. If the field you are interested in is disabled, try removing some dimensions before you try removing some metrics.

