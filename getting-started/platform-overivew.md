# Platform Overview

## Getting Started with Panoramic

Getting started is easy and you can be up and running in less than 30 minutes by just following these three steps.

1. Connect your data and **define all your datasets** - already have the data, connect your data warehouse. Need help getting the data, Integrate with one of our Data Pipeline partners. Once you're connected, Data Preparation and Data Definition has never been easier to manage.
2. Let our unified **data transformation layer** inspect all of the data you connect and build useful models to speed up your analysis
   1. Have something totally custom, dive in deep and configure your own custom models
3. Invite teams into **Personalized Workspaces** and let them start safely customizing their metrics, setting up monitoring and letting the system push insights to them, freeing up more time to focus on the business

## The anatomy of the Panoramic platform

When getting started using a new platform, it can often take time to “learn the ropes.” At Panoramic, we want to minimize that time so you get immediate value out of the platform. The below definitions explain how the platform is organized in an effort to help you quickly get up and running.

**BOARD -** A Board can be thought of as your “visual organizer.” A Board can consist of one or more charts. There are two types of Boards: **Featured Boards** and **Custom Boards**.

* **Featured Boards -** Part of the enterprise offering, Featured boards provide out-of-the-box report templates that appear soon after connecting your data to Panoramic. A Featured Board typically contains 5+ charts to provide you inspiration into how to analyze and visualize your marketing performance based on the data source you've connected \(i.e. Facebook Ads, Google Search, etc.\)
* **Custom Boards** - A Custom Board is a collection of charts that you, your team, or Pano’s Analytics Consultants have created which are tailored to your specific reporting needs

**DATAFRAME -** Within each board lives one or more Dataframes. A Dataframe in Pano is considered any view or your underlying data, either in the same format as it exists in the data warehouse or transformed to match your reporting needs. These Dataframes can either be presented as tables or using any of the available chart types. As you assemble your transformed data, its common to think of boards similar to schemas in a database and Dataframes as the tables within the schema.

**FIELDS -** Each Dataframe is made up of one or more fields. Fields split up into two types, dimensions or metrics. At its most basic level, metrics are fields that can be aggregated for reporting purposes and dimensions are the fields that are used to group metrics into buckets. Fields are used to populate tables and charts according to your specific needs. Most organizations have a set of key performance indicators, or KPIs, which can be used to determine the right Metrics and Dimensions to include in your Dataframes.

* **Metrics** - Measurable values that can be aggregated for reporting. Metrics are restricted to certain data types where algebraic or logical functions can be applied. Common examples include Cost Per Thousand Impressions \(CPM\), Video View Rate, Return on Ad Spend \(ROAS\), Click Through Rate \(CTR\).
* **Dimensions** - Technically defined as anything that is not a dimension, these can include entities, attributes of entities or any other non-metric breakdowns available in the data. Common examples include the ID of a customer, where they are located \(Region, Country\) or what type of audience they fell under \(Males, Ages 20-30, etc.\)

**DATASET -** The foundation of any Dataframe is the one or more Datasets that feed into it. These Datasets represent the raw data that is piped from an external API, such as Facebook Ads or The Trade Desk into your connected data warehouse. During the data modeling phase each group of tables from a single source should be defined as a Dataset. These Datasets can then be pulled into a Dataframe and blended to meet your reporting needs.

### **Overall Navigation**

![](../.gitbook/assets/2%20%281%29.png)

_**Main Menu Navigation**_

If you are an **Admin**, you will see the Main Menu, which displays three primary tabs:  
**WORKSPACES, INBOX**, and **COMPANIES.**

* **WORKSPACES -** secure areas for teams to collaborate around their data, while allowing Admins to customize permissions \(e.g. giving access to one agency for certain campaigns, sectioning off access per teams for different product lines, etc.\). Within one Company, there can be multiple Workspaces. Common examples of using more than one Workspace include separating marketing data by campaigns, product lines, store locations, or movie titles.
* **INBOX -** destination for all your message types \(Public, Private, Team-specific\) across multiple Workspaces. Inbox is especially useful if your Company uses multiple Workspaces.
* **COMPANIES -** independent entities, such as individual companies or distinct departments within a single company, that use one or more Workspaces to segment, map and visualize their data. Companies can set permissions for all Workspaces such as the **Data Glossary** or designate groups of users, also known as **Teams**.

_**Workspace Menu Navigation**_

![](../.gitbook/assets/3.png)

After creating a Workspace within your Company, the new Workspace will appear upon logging in. After selecting a Workspace, you will see the Workspace Menu, which displays five primary tabs:

**FEED, FEATURED BOARDS, CUSTOM BOARDS, GLOSSARY,** and **SETTINGS.**

* **FEED -** destination for all your message types \(Public, Private, Team-specific\) within a given Workspace.
* **FEATURED BOARDS -** as described above, these are out-of-the-box Boards that come with pre-set Charts to help you quickly visualize your marketing performance without the need for any customization or ramp-up time. Once you activate a Collection \(see here for further details\), a Featured Board connecting visuals related to your specified Data Sources will automatically appear within this tab.
* **CUSTOM BOARDS** - as described above, these are any Boards that have been customized for you from Panoramic’s Marketing Science team, or Boards that you or your organization has created \(see here on details around creating a custom Board\) will appear within this tab.
* **GLOSSARY** - any terms that Panoramic has mapped across platforms \(i.e. Ad Account in Facebook = Advertiser in The Trade Desk\) will appear here with a clear definition. In addition, any terms that you or your colleagues create that are specific to your organization will appear here \(see here for more information on Panoramic’s Glossary\).
* **SETTINGS** - here you will be able to customize your Workspace, including adding Collaborators \(Users invited at the Company level\), connect relevant Data Sources, activate Collections, re-name your Workspace, and add an image to your Workspace.

_**Inbox Main Navigation**_

![](../.gitbook/assets/4%20%281%29.png)

Just below the Workspaces tab within the Main Menu Navigation is Your Inbox. Inbox allows you to work across multiple Workspaces, combining private, public and team-specific messages in one place. After selecting Inbox, you will see the following options to hand side, which display the following groups:

* **READ STATUS**
  * **All** - displays all Read and Unread Messages
  * **Unread** - displays ONLY Unread Messages
* **MESSAGE STATUS**
  * **Active -** displays ONLY Messages that have not yet been Resolved
  * **Resolved -** displays ONLY Messages that have been Resolved
* **MESSAGE TYPE**
  * **All -** displays All types of Messages \(Public, Private, I'm Following, @Mentions\)
  * **Public -** displays ONLY Public messages \(messages that appear in your Workspace\)
  * **Private -** displays ONLY Private messages \(sent directly to you from 1+ people within your Workspace\)
  * **I'm Following -** displays ONLY messages that you are Following
  * **@ Mentions -** displays ANY messages that you are directly mentioned via the @mention. These can include both private and public messages.

_**Company Main Navigation**_

![](../.gitbook/assets/5%20%281%29.png)

After creating a Company within Panoramic, you will see the **Company Settings Menu**, which displays seven primary tabs:

**COMPANY, SHARING, WORKSPACES, USERS, TEAMS, GLOSSARY, COLLECTIONS.**

* **COMPANY -** here you can change the name of your Company should you need to.
* **SHARING -** view or share access to any other companies working with your marketing data, such as consultants or agencies
* **WORKSPACES -** displays any Workspace\(s\) that have been created under your Company
* **USERS -** displays active and inactive users within your Company. You can also add users or remove individual access here
* **TEAMS -** create teams for groups of users to easily communicate with one another.
* **GLOSSARY -** displays all mapped terms across Panoramic, as well as custom terms you have created
* **COLLECTIONS -** enable Collections to get started connecting and visualizing your data

