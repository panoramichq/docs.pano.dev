---
description: Coming Soon in Data Explorer!
---

# Signals

## What is a Signal?

Signals are a section in Panoramic where users are able to create custom threshold settings for summary metrics. Users are able to create Signals in a Panoramic Workspace and be notified in their Feed.

\*\*\*\*

## **Signals Dashboard**

In the Signals dashboard, users will be able to see all pre-existing Signals when available, and create a new Signal.

The following functions will be available:

* Search -- the ability to search for a Signal by name
* Sort -- the ability to sort the signals by Recently Started, Ending Soon, Overpacing, and Underpacing
* Active tab -- see all ongoing Signals
* Completed tab -- see all Signals that are past the End Date

All pre-existing Signals will be displayed with the following information:

* Signal name
* Date Range
* Target metric
* Status

## **Creating a Signal**

Navigate to your Workspace and find Signals in your left-side bar

![](https://downloads.intercomcdn.com/i/o/222910525/f4a81c2e7d0fa1c796171a5c/image.png)

Click on Create Signal on the Signals Dashboard to open the Signal Explorer

![](https://downloads.intercomcdn.com/i/o/222913400/62c4403ddf57cfdbf736c318/image.png)

Just as in Data Explorer, select your Data Source, apply relevant filters to make sure you're pacing the right data set

![](https://downloads.intercomcdn.com/i/o/222913717/26d2dcb7902f8466cc2d4cd9/image.png)

Select the date range, the summary metric you want to track, the Target value, and the threshold.

For example: A user might want to pace your overall spend for a data source, and receive a notification when you are "Above", "Below" or "Above or Below" a percentage of the threshold that has been set.

![](https://downloads.intercomcdn.com/i/o/222914497/d94739671d30e4fba3defd76/image.png)

Add all the Subscribers that should receive notifications, name and save your Signal!

![](https://downloads.intercomcdn.com/i/o/222915802/30f134b8d3890d297263e705/image.png)

## \*\*\*\*

## **Anatomy of a Signal**

In the Signals UI, the user will be able to create a new Signal in a large modal. When creating a new Signal, the following inputs will be required:

#### **Date range**

* Users will be required to input a start and end date and time that is at least 24 hours. The Signal stops monitoring the metric when the end date and time is reached. 
* Users will be able to input time in the highest granularity available to the data source they selected. For example: because Hourly is available in Facebook Ads, Signals using Facebook Ads as their data source will be able to input a specific hour of the day for their start/end date.

#### **Data source**

Users will be required to specify which data source to monitor for the Signal.

* Data Source will be a required condition.
* Users will be allowed to add filters to apply to the data source being monitored, such as Publisher, Campaign Name contains, Age Bucket, Gender, etc.
  * Workspace filters Must be applied before Signal filters, e.g. the actual husky query must apply workspace\_filters + signal\_filters
  * If Workspace Filters are edited while Signals are scheduled in the future OR some Signals are mid-flight, when the user saves their edited workspace filters, a prompt will be triggered, stating: “These updates will not apply to your current Signals. Would you like to proceed?”
  * Filters available will include both metrics and dimensions.

#### **Target metric**

When creating a Signal, users will be required to select a summary metric they would like to track. The menu of selectable metrics will be a list of taxons where taxon\_type=’metric’, and aggregation\_type = ‘SUM’’, and metric\_calculation=None.

#### **Advanced settings**

#### **Target value**

Users will be allowed to apply a target value to the target metric, which is a target value specifically for the Signal’s date range. 

#### **Pacing model**

When a target metric is being measured against a target value, the user will have the ability to select a pacing model that the platform will monitor their Signal with. In V1, “Even” pacing will be available, and more to come in the future.

#### **Pacing threshold**

When a Signal has a target value, users will be able to set a threshold \(% value\) for their pacing. 

* The default value will be X%. 
* A Collaboration message will only fire when the target metric is outside of the pacing threshold upon reaching a pacing checkpoint. More on this in the Pacing Checkpoints section.

#### **Signal name**

As the user is filling out the Data Source and Metric fields, the name field will parse the inputs and auto-fill with the format {{Data Source}} {{Metric}} {{Create Date}} \(example: Facebook Ads Spend 02/20/2020\).

#### Subscribers

Users will have the ability to add Subscribers for their Signal.

* By default, the Signal creator is a Subscriber to the Signal, but can be removed.
* Workspace users can be added as Subscribers to a Signal.
* Updates are posted as Collaboration conversation messages in the Signal Line Chart. See the Subscription section for more information on how and when these notifications are posted.
* When Subscribers are added or removed to a Signal, they are added or removed as Followers of all conversation messages in the Signal Line Chart.

Once a Signal has been created, the user will be returned to the Signals dashboard, where the Signal is now displayed as a row in a table interface.  


## **FAQ's \(to work into description\)**

**Can I create a Signal for a date that is in the past?**

You can create a Signal for a date that begins in the past, but it must have an end date that is in the future.

Your date range must also be at least 24 hours.

**Can I create a Signal for multiple data sources?**

Just like in Data Tagging, you can create multiple Signals across data sources, but each individual signal is Data source specific.

**What is level of granularity that I can track?**

You can input the time in the highest granularity available to the data source selected. For example: Because hourly is available for Facebook Ads, Signals using Facebook Ads as the data source, will be able to input a specific hour of the day for the start/end date.

**What happens if I make changes to my Workspace mid-flight?**

If Workspace Filters are edited while Signals are scheduled in the future **OR** some Signals are mid-flight, when a Workspace, the new updates will not apply to the current Signals.

**What if I want to track a rate metric?**

We are working on adding rate metrics as the next iteration of Signals and will be releasing this soon!

