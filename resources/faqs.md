# FAQ's



* Aggregation is an attribute of a field & NOT part of a standard TEL calculation
  * Taxonless querying may be an exception here, but we need to work through some specifics about whether taxonless querying utilizes or overrides existing field logic \(calc or agg\)
  * Aggregation can only be defined once, on fields that point directly to db columns. NULL/no aggregation is also an option and indicates that the field be treated as a dimension instead of a metric
  * A field that points to a db column and has an aggregation type set can also have a calculation applied, things like “db\_col \* 1000” or “IFF\(objective = x, db\_col, null\)”. These calculations are transforming each row of data before the aggregation would be applied and this logic should be added in the model file data\_ref
* Any transformation that applies to the field itself should be defined in the model transformation instead of the field calculation
  * This means metric fields that point to data will:
    * always have an aggregation type attribute defined
    * Never have a calculation defined
    * Optionally have a transformation applied at the model level
  * This should integrate well with the rest of the system since we have decided to support the same TEL functions in both the model transformation and the field calculation
  * So to cover the SUMIF\(\) example, if someone has a model with facebook actions and they want to create a new metric for each action type. They would define each metric in the model like
    * sql\_ref: IFF\(action == ‘lead’, value\)
    * Field\_map:
      * Leads
    * sql\_ref: IFF\(action == ‘visit’, value\)
    * Field\_map:
      * Visits
  * Then at the field level, they would define an aggregation type == SUM on both of these metrics

