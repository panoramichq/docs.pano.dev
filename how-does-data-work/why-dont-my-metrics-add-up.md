# Why Don't my Metrics Add Up?

When looking at total metrics, there’s a common situation that you need to be careful to watch out for.

When comparing top-level metrics with the metric broken down by dimension, a common mistake is assuming that the top-level metric and the sum of the metric broken down by dimension will equal each other.

In fact, the opposite is true, for example …

* Top level video views does not always equal the sum of video views for each gender
* Top level unique impressions does not always equal the sum of unique impressions for each keyword
* Top level spend does not always equal the sum of spend for every age group

This can be caused by a few reasons …

* Sampling
* Unique Metrics
* Real Time Update Limitations

#### Sampling

Sampling is the common data practice to measure a sample portion of a population, rather than measure the entire population. A familiar example is a political poll that samples a portion of a country’s population to understand the political affiliation of the entire country. 

Ads platforms will employ sampling because …

* They might not have complete information on every user who views the ads, and are making logical assumptions with the data they do have.
* They might be collecting so much data that sampling data is the only way they can provide accurate information in a timely manner.

If the ads platform uses sampling, the top-level metrics and the sum of metrics by breakdown can have different sampling methods that prevent the two numbers from matching.

Some additional reading:

* Facebook’s explanation to “Troubleshoot Reasons Why Ad Metrics May Not Add Up”

#### Unique Metrics

Unique metrics measure the number of unique people who did that activity. For example, unique ad group impressions are the number of unique people who saw an ad belong to that ad group at least once.

Top-level unique metrics and the sum of unique metrics by breakdown won’t match because a person will only be counted once for the top-level unique metrics, but could be counted twice or more for each breakdown.

For example, imagine and ad group that serves two ads. Only two users saw the ads …

* The first user sees both ads. The first ad was after typing the keywords “fast fashion”; the second ad after typing the keywords “dresses”.
* The second user sees one ad. Their keyword was “fast fashion” as well.

The top-level unique impressions would be 2 for each user. However, the unique impressions for each keyword …

* For “fast fashion” would be 2
* For “dresses” would be 1

… which do not add up to the top-level unique impressions because the first user saw both ads.

Some additional reading:

* Facebook’s explanation to “Troubleshoot Reasons Why Ad Metrics May Not Add Up”
* Twitter’s answer to the question “Why doesn’t top level data match the sum of all individual line items, including Keywords, Language, etc?”
* Google’s advice to “Avoid double-counting report totals”

#### Real Time Update Limitations 

Finally, some platforms have different code they use for billing than the code they use to measure performance. Depending on which code they use, the ads platform can report different numbers, especially when spend is involved.

Some additional reading:

* Twitter’s answer to the question “Why does spend for individual campaigns not add up to top line sum?”

#### What You Can Do

Here are some best practices you can use to manage these situations.

#### Source Your Data from the Correct Report

Picking the right report to download makes a huge difference. If you attempt to visualize a top-level metric but download your data from the ads manager using a breakdown dimension, your top-level metric will be inaccurate.

Make sure that …

* If you want to view top-level metrics, download from a top-level report
* Only if you want to view a breakdown dimension, download from a report that includes the breakdown dimension

Fortunately, if you’re a part of the Panoramic platform, we’ll automatically select the correct report for you based on what dimensions and metrics you’re requesting.

#### Use Breakdowns for Comparison

Be cautious when showing sums or totals for breakdowns. For example ...

* Using a stacked area or column chart to show the sum of unique impressions for all keywords would be misleading since the total doesn’t represent unique impressions for the entire entity.
* Using a pivot table to show the total number of impressions across every age bucket would also be misleading since the total might not be an accurate summary.

Instead, use breakdown dimensions to show the differences between breakdowns, so for example ...

* Using a grouped column chart to show the different in unique impressions between each keyword.
* Using a table to show the number of impressions for each age bucket

Fortunately, if you’re part of the Panoramic platform, you’ll never see a featured board with a chart that misrepresents a breakdown dimension so you never have to doubt whether the numbers are accurate.

#### Additional Reading

Want to learn more about this subject? Here’s some reading from a few of the ads managers we partner with about how this subject impacts their platforms.

[Facebook: Troubleshoot Reasons Why Ad Metrics May Not Add Up](https://www.facebook.com/business/help/1098122253564910?id=354406972049255)

[Twitter: Common analytics discrepancies](https://business.twitter.com/en/help/campaign-measurement-and-analytics/common-analytics-discrepancies.html)

[Google: Avoid double-counting report totals](https://support.google.com/admanager/answer/7642799?hl=en&ref_topic=7492017)  


