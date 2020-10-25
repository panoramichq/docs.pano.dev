# Data Comparisons

Visualizing your marketing performance is great, but it can be tough if you see a cost per click \(CPC\) of $0.50 without knowing whether that’s really low or really high.

Pano provides the ability to easily compare your data against a reference dataset. Often times this reference is a company benchmark or other historical data sample that helps provide context to the analysis. Adding comparisons is easy and can be toggled on or off in your Board settings.

#### Comparing Apples to Apples

Benchmarks are helpful to compare apples to apples. We do that for your data by creating what we call the benchmark formula. It’s the list of dimensions that defines what makes two apples an “apple to apple” comparison. For example: 

* For a generic Facebook Ads campaign, we’ll compare CPC against other Facebook Ads campaigns that share the same publishers \(Instagram, Facebook, or both\) and objectives \(such as video views\).

From that simple mechanism, we’re able to deliver benchmarks to every chart in our system. Here’s how we avoid making it confusing.

#### Above all else, communicate data accurately.

To keep the “apples to apples” relationship clear at all times, when we show the performance and benchmark in the same chart, the two will always share the same color so that you can find the two, with different weights to tell the difference. For example:

* A column chart showing the CPC and the benchmark will use a Blue 400 for the performance, and a Blue 700 for the benchmark.

Tables and KPI charts that don’t plot values will use color to highlight the difference, but will also include the benchmark value, the percent difference, and a sign whether the difference is positive or negative. For example:

* A KPI chart summarizing the average CPC of $0.50 will show the benchmark of $0.78, the -35.9% below benchmark, and a green downward icon to show that a lower amount is a positive change.

#### Make the right thing easy and the wrong thing hard.

To make it easier to show a benchmark, we’ll simplify the choices to a dropdown at the top of the page for you to pick between a few simple options. For example, when evaluating the performance of a Snap Ad Squad during the last 7 days, you can choose from:

* Company Lifetime Benchmark to compare to any ad squad your company has run
* Workspace Lifetime Benchmark to compare to any ad squads inside the same workspace
* \(coming soon\) Previous Period to compare to how this ad squad did the previous 7 days

When you create a chart, we’ll assemble the correct benchmark formula for you by using our data science team’s best practice for your dataset, and seeing what dimensions you’re displaying in the chart. For example:

* For a column chart showing CPC for Twitter promoted tweets for the top 10 DMA’s, our system will auto-assemble a benchmark using other promoted tweets that share the same targeted placements, objectives, and interests.

#### If we must do the wrong thing, speed bumps not fences.

Sometimes, we won’t be able to display the benchmark for a particular metric. For example, we don’t benchmark spend or any related “magnitude” metrics as it’s impossible to have a “normal” spend when you're deciding how much to spend. In those cases, we’ll warn you that a benchmark doesn’t exist. For example:

* A line/combo chart showing impressions and likes will also show you a warning saying “Comparisons are unavailable for the following: impressions and like.” since both are dependent on how much money you spent to promote the ad.

