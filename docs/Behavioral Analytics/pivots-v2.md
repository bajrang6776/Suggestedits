---
title: Pivots 2.0
excerpt: Understand what are Pivots in CleverTap.
deprecated: false
hidden: false
metadata:
  robots: index
---
# Overview

Pivots 2.0 is an exploratory analytics capability that helps you derive meaningful insights from your user data by summarizing events in interactive tables and visualizations. It lets you break down large volumes of data across multiple dimensions, such as events, segments, properties, and time, so you can quickly spot patterns, trends, and outliers without writing complex queries.

A pivot analysis helps answer questions such as:

* Which product categories are performing best, and at what time of day?
* In which city are sales for a specific brand or product the lowest?
* How much sports content do premium users consume across different days of the week?

<Callout icon="📘" theme="info">
  #### Public Beta

  This feature is released in Public Beta. For more information about this feature or any queries, contact your Customer Success Manager or the [CleverTap Support](https://help.clevertap.com/hc/en-us/requests/new).
</Callout>

# Getting Started

Pivots has the following four important components in it's query builder when you apply for the pivot analysis query (Feedback: Very vague and unclear. Write it better)

* [Select Event](doc:pivots-v2#select-event)
* [Select Segment](doc:pivots-v2#select-segment)
* [Select Properties](doc:pivots-v2#select-properties)
* [Select Metric](doc:pivots-v2#select-metric)

## Select an Event

Start by selecting the event you want to analyze. This event forms the foundation of your pivot analysis. For example, `Product Viewed`, `Video Watched`, `Charged`, `App Launched` and so on.

<Image align="center" border={true} src="https://files.readme.io/b3cddc152ed699635284236f480f6ab6cfc94a7632f97bd04720cf16fa72aad4-image.png" className="border" />

The selected event determines:

* The dataset being analyzed
* The event properties available for pivoting
* The measurements that can be applied

## Select Segment

You can restrict the pivot analysis to a specific user segment or create a new segment from the same query builder. Segmenting helps you understand how different groups of users behave differently for the same event.

<Image align="center" border={true} src="https://files.readme.io/c3c3caf4dbbb5d3680c62c71aec1cf2f1b4fc0f67ec54f4b1958bd21e025de2b-image.png" className="border" />

For example, you can:

* Compare engagement between New Users and Returning Users
* Analyze purchases by High-Value Users
* Understand content consumption for Subscribed vs Free users

## Select Properties

Pivots allow you to analyze events across multiple dimensions. You can mix and match properties to explore different analytical angles. These properties can be used as Rows, Columns, or Axes in visualization options.

<Image align="center" border={true} src="https://files.readme.io/cc2b583f401c8525c7d35cb0d634f9070dea2f4d967e79402ada93494d778ff9-image.png" className="border" />

You can pivot on:

* **Event properties** (for example, product name, content category)
* **User profile properties** (for example, language, customer type)
* **Geographic properties** (for example, city, country)
* **Technographic properties** (for example, device type, OS)
* **App fields** (for example, app version)

## Select Metric

The metric field defines what you want to quantify for the selected event.

Pivots 2.0 supports three metric types:

* [Event Count](doc:pivots-v2#event-count)
* [Event Property](doc:pivots-v2#event-property)
* [Sum of Property](doc:pivots-v2#sum-of-property)

### Event Count

Counts how many times the selected event occurred.

Use this when you want to:

* Measure frequency or volume
* Compare activity levels across dimensions

For example, number of `Product Viewed` events per category per day

### Event Property

### Sum of Property

Aggregates the total value of a numeric event property. This is useful when the event represents a value-bearing action.

For example:

* Total revenue using the `amount` property of the `Charged` event
* Total watch time using `video_duration` for `Video Watched`

# Reading the Pivot Analysis

A pivot analysis consists of the following components:

## Available Properties

The pool of properties you selected during setup. You can dynamically assign these properties as rows, columns, or chart axes to explore different views of the same data.

## Rows and Columns

Rows and columns define how data is grouped in tabular views.

For example:

* Rows: Day of Week
* Columns: Product Category

This structure allows you to compare values across dimensions at a glance.

## Visualizations

Pivots 2.0 supports multiple visualization types to help you interpret data effectively.

You can switch between views without changing the underlying query.

## Table

Best for getting a precise, detailed overview of the data. Use tables when you want exact values or need to export results.

## Heatmaps

Heatmaps highlight intensity using color, making it easy to spot patterns.

## Table Heatmap

Best for identifying highest contributors in the dataset. For example, which product-category and day combinations generate the most revenue?

## Column-wise Heatmap

Best for identifying outliers within each column. For example, which product performs best on each day of the week?

## Row-wise Heatmap

Best for identifying outliers within each row. For example, which day performs best for each content title?

## Bar Chart

Best for comparing categorical data. Use this option to compare performance across categories such as products, regions, or languages.

## Stacked Bar Chart

Best for comparing how multiple variables contribute to a total over time or across categories. Use this option to understand composition changes across dimensions.

## Line Chart

Best for analyzing trends over time. Use this option to identify correlations or similar behavioral patterns between variables.

## Area Chart

Best for understanding part-to-whole relationships over time. Use this option to analyze contribution of individual categories to overall performance.

# Example Use Case: Content Consumption Analysis

A video streaming app wants to analyze content performance beyond just views.

Query:

* Event: `Video Watched`
* Measurement: Sum of `video_duration`
* Rows: Day of Week
* Columns: Video Name

Insights:

* Identify which shows drive the most watch time
* Understand viewing patterns across weekdays
* Optimize content promotion and scheduling

## Create a Pivot Analysis

To create a pivot analysis:

1. Navigate to _Analytics > Pivots_
2. Select the **event** you want to analyze
3. Apply **filters and segments** (optional)
4. Choose **properties to pivot on**
5. Select a **measurement** and **visualization**
6. Run the analysis to explore insights

# FAQs

This section answers common questions and helps you resolve frequent issues while using Pivots 2.0.

### Why do my numbers not match other dashboards?

Pivots may apply **data sampling** for large queries to improve performance.

Sampling applies when:

* Query contains more than **100,000 events**
* Sample rate after 100,000 events is **10%**
* Results remain **directionally accurate**

**Recommendation:** Use pivot insights for patterns, trends, and comparisons; use raw dashboards for exact totals.

### Can I pivot using multiple properties?

Yes. You can pivot using multiple dimensions by placing properties across rows and columns and exploring combinations through the table or visual view.

### What measurement should I use: Count or Sum of Property?

Use:

* **Event Count** when you want frequency/volume of an event
* **Sum of Property** when you want a total numeric value (revenue, watch time, quantity, etc.)

### Why can’t I select a property for Sum?

Only **numeric properties** (integer/float) can be used with **Sum of Property**.

If the property is a string (for example, `"USD"` or `"category"`), it will not appear in the sum list.

### Can I analyze users instead of events?

Pivots primarily measure events. However, by selecting the right event and combining segmentation filters, you can derive user-level insights such as:

* Behavior by user segment
* Events generated per segment
* Value contribution by segment

### Can I export pivot results?

If exports are supported in your deployment/version, you can export tabular views. Export behavior depends on workspace permissions and feature availability.

# Troubleshooting

### Issue: “No Data Available”

This can happen due to any of the following:

Check:

* Is the selected **event** firing in the chosen date range?
* Did you apply a segment filter that excludes all users?
* Are you using a property that has sparse or null values?

### Issue: “Property not showing in pivot options”

Possible causes:

* The property does not exist for the selected event
* The property has not been ingested in the selected date range
* You selected a measurement type that limits property selection (for example, Sum requires numeric property)

### Issue: “Results are too high / too low”

Things to verify:

* Are you viewing **event count** vs **sum**?
* Are filters and segments applied correctly?
* Is the conversion window or date range aligned with your intended analysis?

### Issue: “Charts are hard to interpret due to too many values”

Recommendations:

* Reduce dimensionality by pivoting on fewer properties
* Filter down to top-performing categories (if supported)
* Use heatmaps to quickly spot high-impact areas
* Switch to Table view when precision matters

### Issue: “Pivot takes too long to load”

Recommendations:

* Narrow the date range
* Remove high-cardinality dimensions (for example, user ID, session ID)
* Use fewer rows/columns
* Avoid combining too many breakdown properties at once
