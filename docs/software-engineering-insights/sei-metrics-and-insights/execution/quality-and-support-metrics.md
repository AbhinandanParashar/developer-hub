---
title: Quality and support metrics
description: Learn about quality and support metrics and widgets.
sidebar_position: 40
---

This topic describes quality and support metrics, as well as configuration options for widgets associated with these metrics.

## Issues Report

Use the Issues Report to examine metrics related to various tickets/work items (epics, stories, bugs, tasks, and so on) in your issue management system. The report aggregates data based on selected attributes, such as priority, status, labels, components, or any other field. This report helps you create comparisons based on various fields and draw conclusions to make decisions.

### Configure the Issues Report widget

The following options are available when configuring the Issue Report widget.

#### Filters

Select an attribute to use to filter the Issues Report data. You can use multiple filters together.

Select an attribute from the **Add Filter** dropdown menu, and then configure the filter values.

Depending on the selected attribute, you can:

* Select one or more filter values.
* Select values to exclude.
* Use pattern matching rather than strict values.

#### Metrics

Select a metric to use for the Y-axis. The Issues Report widget supports the following metrics:

* **Number of Tickets**
* **Sum of Story Points**

#### Aggregations

* **X-axis:** Select the attribute to use for the X-axis. For example, if you selected the **Number of Tickets** metric for the Y-axis, you could select **Issues Resolved by week** for the X-axis. Additional examples of X-axis dimensional attributes include **Project**, **Assignee**, **Labels**, **Priority**, and so on.
* * **Stacks:** Select how you want to group data in each X-axis dimension. For example, if you select **Priority** for the X-axis and stack by **Status Category**, then data in each X-axis column are grouped by status.

<!--Figure 1: An Issues Report widget configured to show <b>Ticket count</b> on the Y-axis and <b>Priority</b> across the X-axis. For each Priority, the issues are stacked by <b>Status</b>.-->
<!-- mg spaces%2FEb01tnHrNFJhZsvID4IW%2Fuploads%2Fgtbk8giItf7dlTVo92h9%2Fimage.png - Issues Report widget example-->

#### Settings

* Select the issue management system to use for this widget. Available options are based on your configured [connectors](/docs/category/connectors-and-integrations).
* Select how you want to sort X-axis data, such as ascending or descending.
* Select the maximum number of values to show on the X-axis.
* Select the visualization style for the widget:
  * Bar chart
  * Donut Chart
  * Multi-Line chart
  * Percentage stacked bar chart

## Issue Bounce Report

_Bounce_ describes tickets that are reassigned to a previous assignee. The Issue Bounce Report shows the number of times a ticket "bounced" between assignees. Bounce can occur if an issue isn't triaged correctly initially, or if the issue doesn't have enough information to be assigned correctly. Excessive bounce can potentially cause missed SLAs and unnecessary resource utilization.

The Issue Bounce Report widget is usually configured to observe the median number of bounces by component, project, or initiative. This widget can highlight issues that are being bounced around to different resources.

Instances of reassignment to new assignees are captured by the [Issue Hops Report](#issue-hops-report).

## Issue Hops Report

_Hops_ describes the number of times a ticket is reassigned to a new assignee (someone who has never been assigned to that issue before). The Issue Hops Report shows the number of times a ticket "hopped" to new assignees. Hops can occur if an issue isn't triaged correctly initially, or if the issue doesn't have enough information to be assigned correctly. Excessive hops can potentially cause missed SLAs and unnecessary resource utilization.

The Issue Hops Report widget is usually configured to observe the median number of hops by component, project, or initiative. This widget can highlight issues that are reassigned multiple times.

Instances of reassignment to a previous assignee are captured by the [Issue Bounce Report](#issue-bounce-report).

## Issue Hygiene Report

The Issue Hygiene Report widget shows a list of _hygiene misses_ in the designated time frame. Each hygiene miss is tallied against a score of 100. A score of 100 indicates that no tickets were submitted with missing hygiene points.

Scores are calculated using the following formula:

```
Category Score = ( Number of Tickets Missing Hygiene / Total Number of Tickets in Time Frame ) * Weight

Total Score = Sum of Category Scores
```

<!--image .gitbook/assets/image (72).png - Active Sprint Hygiene Insights widget-->

### Configure the Issue Hygiene Report widget

:::info Prerequisites

Before adding the Issue Hygiene Report widget to Insights, you must configure **Custom Hygiene Misses** in your [connectors](../../sei-integrations/sei-integrations-overview.md).

:::

The following options are available when configuring the Issue Hygiene Report widget:

* **Filters:** Filters can be blank or filtered down to a desired ticket type or time frame.
* **Weights:** Configure the weight for each **Hygiene Criteria**. A lower weight causes a criterion to have a lower impact on the overall score, and a higher weight causes a criterion to have a larger impact on the overall score. Make sure the total of all weights equals 100.

<!--image - .gitbook/assets/image (71).png -- Issue Hygiene Report widget config - Weights tab-->

* **Settings:** Select the issue management system to use for this widget. Available options are based on your configured [connectors](/docs/category/connectors-and-integrations).

:::tip

The Issue Hygiene Report is often used in conjunction with the **Issue Hygiene Trend Report** to show a history of hygiene scores.

:::

#### Example configurations

Here are some examples of configurations for the Issue Hygiene Report widget.

<details>
<summary>Active sprint hygiene</summary>

You can configure the widget to show your team's current sprint only. To do this, go to the **Filter** tab, select **Sprint**, and then select **Includes Active Sprints Only**.

<!--img .gitbook/assets/image (55).png - Configure issue hygiene report -- filters tab - include active sprints only-->

</details>

<details>
<summary>Dashboard time hygiene</summary>

_Dashboard time_ is the time range selected by the user when viewing Insights. You can configure the widget to show the hygiene score for all tickets created in the user-selected dashboard time. To do this, go to the **Filter** tab, select **Issue Created In**, and then select **Use Dashboard Time**.

<!--img .gitbook/assets/image (33).png - Configure issue hygiene report -- filters tab - use dashboard time-->

</details>

<details>
<summary>Issues in progress hygiene</summary>

You can configure the widget to show the hygiene score for all in-progress tickets. To do this, go to the **Filter** tab, select **Status**, and then select the statuses that correspond to in-progress tickets.

<!--img .gitbook/assets/image (64).png - Configure issue hygiene report -- filters tab - filter by in progress tickets-->

</details>

<details>
<summary>Issues in backlog hygiene</summary>

You can configure the widget to show the hygiene score for all tickets in your backlog. To do this, go to the **Filter** tab, select **Status**, and then select the statuses that correspond to backlog tickets.

<!--img .gitbook/assets/image (47).png - Configure issue hygiene report -- filters tab - filter by status "to do"-->

</details>

## Issue Resolution Time Report

The Issue Resolution Time Report is a bar graph showing the number of tickets closed along with the average time it took to close those tickets, based on the time the tickets were created. This report can help answer questions like:

* Is my team getting faster at delivering features or fixing issues?
* Is the resolution times for a project or component decreasing over time?
* On average, how long does it take fix customer issues? Are we able to meet the SLA timeline?

<!-- img .gitbook/assets/image (76).png - issue resolution time report widget example -->

### Configure the Issue Resolution Time Report widget

By default, the Issue Resolution Time Report widget is filtered by issues closed (**Last closed date**) within a selected time range. Usually, the time range is set to **Use Dashboard Time**, which allows the user to select a time range when viewing Insights.

<!-- img .gitbook/assets/image (56).png - issue resolution time report widget config - filters tab - last closed date and dashboard time -->

On the **Aggregations** tab, you can select the dimension, from your issue management system, to use for the X-axis, such as **Assignee**, **Story Points**, **Ticket Category**, **Issue Closed Last Time Period**, and so on. This determines what you want the widget to focus on. For example, focusing on **Category** or **Component** can show you the issue resolution time for different work areas; whereas, focusing on **Assignee** can show you issue resolution time by developer.

<!-- img .gitbook/assets/image (59).png - issue resolution time report widget config - aggregations tab - x axis dropdown -->

On the **Settings** tab, you can:

* Select the issue management system to use for this widget. Available options are based on your configured [connectors](/docs/category/connectors-and-integrations).
* Select how you want to sort X-axis data, such as ascending or descending.
* Select the maximum number of unique values to show on the X-axis.

#### Example configurations

The primary way to modify the Issue Resolution Time Report widget is to change the X-axis dimension on the **Aggregations** tab. Here are some examples of other configurations for this widget.

<details>
<summary>Average time to issue closed by assignee</summary>

This configuration produces a bar graph showing which assignees are taking the most time to close issues within the selected time frame.

1. On the **Aggregations** tab, select **Assignee** for the X-axis dimension.
2. On the **Settings** tab, sort the X-axis by **Value, High --> Low**, and set the **Max X-Axis Entries** high enough so that it can show all team members.

<!-- img /.gitbook/assets/image (53).png - Issue Resolution Time Report widget config - settings tab - sort xaxis high to low and 20 max entries -->

</details>

<details>
<summary>Story point estimation accuracy</summary>

This configuration produces a bar graph showing how well your story points are estimated. Good estimation is evidenced by a graph showing linear progression, with higher point issues taking longer to resolve than lower ones.

<!-- img .gitbook/assets/image (30).png - Story point estimation accuracy bar graph w linear progression -->

1. On the **Aggregations** tab, select **Story Points** for the X-axis dimension.
2. On the **Filters** tab, exclude backlog stages by adding an **Exclude Time In Status** filter, and set the filter value to your backlog status(es), such as **To Do** or **Backlog**.

   <!-- img .gitbook/assets/image (29).png - exclude time in status filter example config -->

3. On the **Settings** tab, sort the X-axis by **Label, Low --> High**.

</details>

<details>
<summary>Time to close issue by last time period</summary>

This configuration produces a bar graph showing a historical record of the average time it took to close all issues within the selected time frame.

<!-- img .gitbook/assets/image (38).png - time to close issue by last time period bar graph example -->

1. On the **Aggregations** tab, select **Issue Last Closed (Week, Month, Quarter)** for the X-axis dimension.
2. On the **Filters** tab, add filters to demonstrate [MTTR](#mttr-and-mtbf) or [Lead Time For Changes](./dora-metrics.md#lead-time-for-changes) trends:

   * For MTTR: Add an **Issue Type** filter, and set the filter value to **Bugs**.
   * For Lead Time For Change: Add an **Issue Type** filter, and set the filter values to **Tasks** and **Stories**.

3. On the **Settings** tab, sort the X-axis by **Label, Low --> High**.

</details>

## MTTR and MTBF

Mean Time To Recover (MTTR) measures the average amount of time it takes to resolve an incident or failure, from the moment it is detected to the moment it is fully resolved.

Mean Time Between Failures (MTBF) measures the average amount of time a system or component operates without failing. It is expressed as a continuous operating time in hours, days, or other units of time.

For more information about MTTR, MTBF, and other DORA metrics, go to [DORA metrics](./dora-metrics.md).

## SCM Files Report

Use the SCM Files Report to identify code areas with a high frequency of changes. This is useful for ensuring that your hottest code areas have good test coverage.

:::info

Several tools-based metrics are available with SEI, such as SonarQube code complexity reports, Testrails test reports, PagerDuty incident reports, Junit test reports, and many more.

:::
