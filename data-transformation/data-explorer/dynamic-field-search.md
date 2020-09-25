# Dynamic Field Search

Panoramic abstracts the Models so you don't have to worry. This approach makes it simpler for users who are not familiar with data, databases, or your underlying data model to still perform an analysis safely, without calculating something incorrectly, or having to take the time to learn what fields are in every table. The data engineering and analytics team can work on the underlying data model, to ensure everything is defined correctly, joined and exposed, and the business team can be free to explore the data in a safe and easy manner.

Field Selector dynamically updates as you add each field. Based on the underlying data modeling that has already been defined, the Panoramic platform "knows" which relationships can be formed between multiple models, or dimensions and metrics. The field selector will automatically enable or disable available fields based on the set that you have already selected. 

Best practice is to start every analysis by first pulling in the dimensions or metrics that you care about most. If spend is the most important metric, then add spend to your exploration. The field selector will then automatically update by removing any metrics or dimensions that cannot be analyzed with spend.

If you are performing an analysis and one of the fields that you are interested in is disabled, try removing some of the fields you have already added and it should become enabled again.

General rule of thumb is that dimensions have the most impact on which fields can be included in an analysis, since dimensions are what we use to define the relationships between models. If the field you are interested in is disabled, try removing some dimensions before you try removing some metrics.

