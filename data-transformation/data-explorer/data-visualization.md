# Data Visualization

## What is data visualization?

Data visualization is a huge industry on its own. There are College courses, 1000's of research papers published and a large set of available resources to help present data so that it tells a story.

At Panoramic we try to follow the approach taken by The Grammar of Graphics where the data is the starting point for a visualization and....

Our goal with visualizations is to help you, the user and any other consumer of your transformation understand the data, we are not designing to be a presentation tool. This means we do not focus on the ability to customize colors and fonts in a chart. Instead we pick the colors for you based on research that shows which colors are the most easily interpretable by the consumer of a visual. If the data should not be presented in a line chart, then we disable the line chart. Our goal is to make it easier for new data visualizers to publish transformations that tell a story, and reduce the possibility of them making a mistake by presenting the data in a confusing manner.

Here are some good resources to learn more about data visualization:

* [https://www.springer.com/gp/book/9780387245447](https://www.springer.com/gp/book/9780387245447)
* [https://www.datavisualizationsociety.com/](https://www.datavisualizationsociety.com/)
* [https://observablehq.com/@d3/learn-d3](https://observablehq.com/@d3/learn-d3)



## What’s our mantra?

Sounds great, but building software is making hundreds of small decisions constantly. It’s easy to get distracted, and what started as “simple” turns into “complicated” pretty quickly.

To help us keep focused, we had three mantras we repeated to ourselves.

1. Above all else, communicate data accurately.
2. Make the right thing easy and the wrong thing hard.
3. If we must do the wrong thing, speed bumps not fences.

Let’s break each of those down.

#### Above all else, communicate data accurately.

Our platform is here to transform your marketing data. It should at least be accurate. Even if it means making charts less “visually appealing.”

To be clear, we don’t like ugly charts! But take 3D charts as an example. They might look cool, but they’ve got a few problems:

* Scientific research shows that humans have a hard time perceiving volume \*
* 3D charts introduce a forced perspective that can make different shapes look the same depending on the viewing angle \*\*

If we really mean accuracy above all else, that means that 3D charts have got to go away!

\* Cleveland and McGill’s 1984 classic study [Graphic Perceptions](https://www.jstor.org/stable/2288400)

\*\* Paul Reiman’s article [3D Pie Charts are Evil](https://www.getnerdyhr.com/3d-pie-charts-are-evil/)

#### Make the right thing easy and the wrong thing hard.

Anyone who’s ever opened a spreadsheet knows that assembling data can get complicated quick. And it should be, building a great data visualization should have a lot of thought behind it.

So instead of skipping the complexity, we take the “right” way of making charts, and make it feel like the carpool lane at rush hour. 

“Right” can mean a lot of things, so we’re lucky to build upon the work of a lot of great thinkers ahead of us:

* The Financial Times’ [Visual Vocabulary](https://github.com/ft-interactive/chart-doctor/tree/master/visual-vocabulary)
* Pratap Vardhan’s [Visual Vocabulary Vega Edition](https://gramener.github.io/visual-vocabulary-vega/#)
* Dr. Andrew Abela’s [Chart Chooser Diagram](https://extremepresentation.typepad.com/files/choosing-a-good-chart-09.pdf)

And if that means that doing anything outside of what’s suggested is a little more difficult \(still possible, just more difficult\), we think that’s the right tradeoff.

#### If we must do the wrong thing, speed bumps not fences.

The wrong thing is hard, but it’s still possible. And that means, if you’re new to data visualizations, you might make a chart that is accidentally misleading.

To deal with that, we won’t stop you from doing the “wrong” thing. After all, it might be a simple difference in opinion. But if you’re a beginner, then we’ll warn you that you’re heading into danger territory so that you’re always aware of the risk.

Let’s say you’re running marketing on Facebook Ads.

* You have some campaigns with an APP\_INSTALLS objective, and other campaigns with a VIDEO\_VIEWS objective.
* Now you build a chart, but your mind is thinking about a different workspace, and you filter to show campaigns that have either the VIDEO\_VIEWS or LINK\_CLICK objectives.

Wait a minute! The account only had APP\_INSTALLS and VIDEO\_VIEWS. If you were looking quickly, you might mistake the chart to include both objectives.

Instead, we’ll warn you that you don’t have any campaigns with LINK\_CLICKS. You can still save the filter and carry on, but now we know you’re not walking away with a mistaken impression.

## Using charts to express insights

## Choosing the best chart type

[https://coggle.it/diagram/Wyv1oFsxfvA1VCe4/t/what-chart-do-i-use/e18b54ede487b04ad15823adaf4f135007e84eeaec889f43ec03e9011235b024](https://coggle.it/diagram/Wyv1oFsxfvA1VCe4/t/what-chart-do-i-use/e18b54ede487b04ad15823adaf4f135007e84eeaec889f43ec03e9011235b024)

## Using Panoramic Charts

[![mceclip9.png](https://panoramic-e054c097e46a.intercom-attachments-1.com/i/o/195602710/dfbf30db4b089a8b47f8ede2/mceclip9.png)](https://panoramic-e054c097e46a.intercom-attachments-1.com/i/o/195602710/dfbf30db4b089a8b47f8ede2/mceclip9.png)

## Colors in Charts

Color is a really useful tool in our design toolkit. 

* It can rapidly draw our focus to a specific spot.
* It can quickly highlight differences.
* It can trigger an emotional response and convey meaning.

But color comes with some pretty big drawbacks.

* Small difference in color \(specifically hue-saturation-density\) are the most difficult thing for humans to perceive \*
* Using color as the only method to convey meaning can exclude the approximately 5% of the population that is color blind. \*\*
* People can get attached to the “right” color. What looks like a clean and classy cyan to one person can look like a crass and unprofessional baby blue.

Our challenge on how to include color in charts was to take advantage of what color is capable of without falling into any of the three traps. Fortunately, our mantras were there to guide the way.

\* Cleveland and McGill’s 1984 classic study [Graphic Perceptions](https://www.jstor.org/stable/2288400)

\*\* Rich Staats’ article [Designing UI with Color Blind Users in Mind](https://www.secretstache.com/blog/designing-for-color-blind-users/)

#### Picking the Right Hues

Our first step is to make sure we have a collection of colors that can work for every situation. We relied heavily on Google’s [Material Design](https://material.io/design/color/the-color-system.html). Invented to help Google maintain a consistent design language across all of their apps from web to Android to iOS and everything in between, the Material Design system includes a color system with pre-set colors and accessibility tools to “help create a color theme that is harmonious, ensures accessible text, and distinguishes UI elements and surface from one another.

From that system, we picked out 12 colors that help us cover the entire spectrum of colors: Red, Pink, Purple, Indigo, Blue, Cyan, Teal, Green, Amber, Orange, Deep Orange, Brown. \*

The system includes weights from 50 to 900 that define how light or dark they are.

With this in palette in place, we started applying our rules.

\* Google’s [Material Design Color Tool](https://material.io/resources/color)

#### Above all else, communicate data accurately.

To communicate data accurately, we don’t use color to convey meaning without a few alternative cues. For example:

* Pivot tables when comparing performance with a benchmark will use red/green conditional formatting to highlight if the difference is positive or negative, but only when it’s also accompanied with a label to explain the difference.

If we’re stuck in a situation where we can’t use a label, we’ll switch to a color contrast against white so it works regardless of ability to perceive color. For example:

* Heatmaps don’t include a label, so the cell will be shaded white/blue based on the magnitude.

If a chart needs multiple colors, we sequence our colors so that any color will sharply contrast against any background, whether white, black, or another color in the chart. For example:

* A donut pie chart with 5 segments will sequence: Blue 400, Orange 400, Green 400, Red 400, and Purple 400. 
* The 400 weight was chosen because it passes the WCAG AA standard for a white or black background for Graphical Objects and UI Components.\*
* By jumping around the color spectrum, we keep as much contrast as possible between unique colors. Blue and orange may be jarring, but are easier to perceive than between red and pink.

\* Tested using WebAIM’s [Contrast Checker](https://webaim.org/resources/contrastchecker/)

#### Make the right thing easy and the wrong thing hard.

Of course, these rules don’t mean much if they’re not consistently applied across all the charts that can exist on the Panoramic platform. So to make the right thing easy and the wrong thing hard, we include our color sequence for you. For example:

* If you create your own column chart to see the average CPM for your 5 objectives, you’ll see the same Blue 400, Orange 400, Green 400, Red 400, and Purple 400 sequence for high-contrast.
* Color choices will be maintained inside the existing palette and at the same sequence to prevent accidental low-contrast designs that break accessible and inclusive designs.

Conditional formatting that require red/green styling will automatically change based on the metric. For example:

* Marketers want to prioritize a low cost per click \(CPC\). So lower CPC’s will be labeled as positive and marked green, while higher CPC’s will be labeled as negative and marked red.
* But markerters want to prioritize a high click through rate \(CTR\). So lower CTR’s will be labeled as negative and marked red, while higher CTR’s will be labeled as positive and marked red.

Comparing your performance against a benchmark \(or previous period, or another comparison\) will share the same color so you know what the benchmark is for, but will use a high-contrast weight to make it clear what’s the performance versus the benchmark. For example:

* A column chart showing the CPC and the benchmark will use a Blue 400 for the performance, and a Blue 700 for the benchmark.

#### Colorful Charts, not Confusing Charts

## Chart Types

Ask any data scientist how they feel about radar charts, and you’re going to get a strong reaction. Good or bad depends on the person, but it’s one of the few topics that will always inspire data people to pick sides.

But if data is not a full time job for you, you might be more concerned about skipping to the end of the chapter and using the best charts.

\* Maciej Bukczynsk’s article [Radar: More Evil Than Pie?](https://www.darkhorseanalytics.com/blog/radar-more-evil-than-pie)

#### The Right Chart for the Right Situation

We at Panoramic believe in the power of charts, and we like trying new ones all the time. The problem is in our research, when visualization software present the user with too many options, the paradox of choice is real and 55% of the time a user compromises and builds a table.

With plenty of other options out there, we built a tool to encourage to express the full visual vocabulary of available charts.

#### Above all else, communicate data accurately.

Of course, presenting more charts was only allowed, if it was in service to communicate data more accurately.

To help us curate the \(seemingly\) infinite number of chart types our there, we started with a couple of collections we liked: 

* The Financial Times’ [Visual Vocabulary](https://github.com/ft-interactive/chart-doctor/tree/master/visual-vocabulary)
* Pratap Vardhan’s [Visual Vocabulary Vega Edition](https://gramener.github.io/visual-vocabulary-vega/#)
* Dr. Andrew Abela’s [Chart Chooser Diagram](https://extremepresentation.typepad.com/files/choosing-a-good-chart-09.pdf)

By building off the work of esteemed others, we could make sure we were sticking with charts that had wide consensus in the community of being effective. For example:

* We’re aware of Funnel charts. But all three collections don’t include Funnel charts. Instead, they suggest that Waterfall is how you communicate the flow between different series. 
* So Funnel is out, and Waterfall is in.

But even then, those collections have a lot of charts, so we limited to only charts that displayed their data from a unique perspective. For example:

* A calendar Heatmap and a Column charts both show change over time in different ways. But you can’t say the same as a Seismogram, since it’s the same as a bar chart aligned center instead of aligned left. 
* So Heatmap and Column are in, and Seismogram are out.

Finally, if two charts did the same thing, we used research on which data encoding methods were the most accurate for humans as our tie breaker.

![](https://lh5.googleusercontent.com/aB10mvEeuaLdaSwSRr5fQfZgCVUds5E--wy_sIyrufbfBuO7G3PtF9JrSLbfLJmfFJBWMWX3nwIeFAjcIC6KPQ1ij4pqk6HIxZzeyJGVqsfr68Es5jUUQGuesEWFE-nclvDG9bhl)

For example:

* A Dot Strip Plot and a Barcode Plot chart do similar things. But research showed that multiple lines close to each other was easier for humans to perceive than the color saturation of overlapping dots. 
* So Barcode Plot is in, and Dot Strip Plot is out.

#### Make the right thing easy and the wrong thing hard.

Now that’s a lot of rules to keep in mind, so our chart builder tool has a few tricks to make it easy for you to do the right thing.

First, when you pick your dimensions and metrics, you’ll only be allowed to load charts that are compatible with what you’ve chosen. And if it’s not quite right, we’ll tell you why. For example:

* If you’ve picked objective, placement, and impressions, we’ll let you pick a column chart, but line/combo charts will be locked away. Ask us why, and the tool will remind you that line/combo charts only work with date since a line chart require a “continuous” dimension in order to show the change over time.

Second, we’ll draw the chart based on the order you’ve selected your dimensions and metrics. For example:

* If you’ve picked objective, placement, and impressions with a column chart, we’ll draw the chart with objective on the x-axis, and different color columns for each placement.

Third, the order we draw your dimensions and metrics is based on progressive enhancement, which means we’ll always try to draw the chart, even if you have one less dimension or metric.\* For example:

* If you’ve picked ad name, click through rate, share rate, and impressions with a scatterplot chart, then we’ll draw the chart with a bubble for every ad name, with CTR on the x-axis, share rate on the y-axis, and impressions as the bubble size.
* But remove the impression, then we’ll keep drawing the chart with a dot for every ad name, with CTR on the x-axis and share rate on the y-axis.

\* Sam Dwyer’s article [Progressive Enhancement: What It Is, And How To Use It?](https://www.smashingmagazine.com/2009/04/progressive-enhancement-what-it-is-and-how-to-use-it/)  


#### A Chart for Every Occasion

With these rules in place, any marketer can feel empowered to make charts that use right visualization for any data. Try your first chart in a custom board today!  


