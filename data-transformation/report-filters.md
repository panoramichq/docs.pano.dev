# Data Filters

## **Filters**

All filters in the Pano system work in the same way and follow the same UI style. Filters can be applied at multiple levels, like a hierarchy, where each filter level restricts data access for all levels below it.

* **Workspace Filters -** Filters all data available within the Workspace. This filters all the data that is accessible to all collaborators within a Workspace. These are best used for restricting access to certain dimensions or metrics when a team does not have permission to that data.
* Board Filters - Filters all data available within the board
* Dataframe Filters - Filters all data available within the Frame or Chart

The logic in the filters is the same no matter where they are applied. Each Filter "clause" is a self-contained filter, all values **within** a single clause are evaluated with **OR** logic and multiple clauses are always **combined** with **AND** logic. You can append as many filter clauses as you need. This filter setup can be read as follows:

`{FIELD_1} {OPERATOR} {VALUE_1} OR {FIELD_1} {OPERATOR} {VALUE_2}              AND                                                                     {FIELD_2} {OPERATOR} {VALUE_3} OR {FIELD_2} {OPERATOR} {VALUE_4}`

Ex: "Campaign Name Contains any of "Test" or "National" and impressions is greater than 1000

![Filter Configuration](https://panoramic-e054c097e46a.intercom-attachments-1.com/i/o/195602768/ab51df9861cfac7c18e87781/Screen_Shot_2020-03-02_at_6.17.22_PM.png)

### **Adding Filters**

 Here's how to add Filters:

1. Click the Filter icon to open the Filters dialog
   1. Workspace Filters - Go to your Datasets tab within a Workspace. 
      1. Select the More Icon to the right of the Data Source you want to filter. 
         1. For example, let's say you know your West Coast store openings are only being advertised on Facebook, you would only need to apply the filter to your Facebook Ads account.
   2. Board Filters - When the board is in edit mode, click the pencil icon next to the date range or the comparison 
   3. Dataframe Filters - Open the Data Explorer and scroll down to the filters section in the right menu
2. Use the filter options to set the exact filters you need.
   1. For example, if you want to Filter by Campaign Name, select **CAMPAIGN NAME** in the first dropdown, then select the condition **EQUALS ANY OF,** then select the value which is the actual Campaign Name you want to filter.
   2. _Note: The locked icon prevents other users from applying filters to your Chart. Selecting this icon enables Users to filter the Chart themselves._
3. Select **SAVE** once you have applied one or more Filters to that Data Source

### **Editing or Removing a Filter**

Please note that you can remove filters at any time. To remove a Filter, follow these steps.

1. Return to the Filters dialog where you set the filter
2. Select **Edit Filters** from the dropdown.
3. Select the grey X to the right of the Filter you wish to remove
4. Select **SAVE**.

