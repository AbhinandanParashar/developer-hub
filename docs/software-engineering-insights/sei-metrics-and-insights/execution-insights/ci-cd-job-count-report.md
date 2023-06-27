---
title: CI/CD Job Count Report
description: This widget shows the number of CI/CD jobs run in a certain time frame.
sidebar_position: 10
---

The **CI/CD Job Count Report** widget shows a bar graph of all CI/CD jobs run in the selected time frame. This widget gives insights into how often jobs run and how many succeed.

## Configure the widget

When you add the **CI/CD Job Count Report** widget to a dashboard, the **Job End Date** filter is set to a relative time frame by default. The widget is ready to use with this default configuration.

### Report all jobs in dashboard time

_Dashboard time_ is the time range selected by the user viewing the dashboard. If you want a more interactive widget that reports all jobs run in the user-selected dashboard time, set **Job End Date** to **Dashboard time**.

If you want the widget to report the status (success or failure) of all jobs in dashboard time, configure the widget as follows:

* Job End Date: Dashboard time
* Metrics: Job Status
* Aggregations: Job Name

<!-- img .gitbook/assets/image (63).png - CICD Job Count Report set to all jobs in dashboard time -->

### Filter by failed jobs

If you want the widget to highlight failed jobs, set **Filter, Job Status** to **Failed**. You can use this configuration in combination with dashboard time, such as:

* Job End Date: Dashboard time
* Metrics: Job Status
* Aggregations: Job Name
* Filter, Job Status: Failed

<!-- img .gitbook/assets/image (28).png - CICD Job Count Report widget showing only failed jobs. -->
