---
title: DORA metrics
description: DORA metrics are key metrics for describing a software development team's performance.
sidebar_position: 20
---

DORA (DevOps Research Assessment) identified the following key metrics that describe a software development team's performance: Deployment Frequency, Lead Time for Changes, Change Failure Rate, Time to Restore service (MTTR), and Reliability (MTBF).

SEI gives you insights into your organization's DORA metrics for a given duration. This helps you understand how your organization or team is performing and helps you get an overview of daily, weekly, and monthly trends. Furthermore, SEI gives you the flexibility to choose the integrations from which you want to derived data, such as issue management, SCM, incident managaement, and CI/CD tools, as well as the ability to select filters to refine the data used to generate your metrics.

## Deployment Frequency

Deployment Frequency represents how often an organization successfully releases software to production.


## Lead Time for Changes

Lead Time for Changes represents the amount of time it takes a commit to get into production.

The overall lead time is the sum of the average time spent in each stage configured in the workflow. This metric can help identify where the team is spending time and if the amount of time spent in each stage falls in an acceptable range.

### The SCM Lead Time widget

Use the **SCM (Source Code Management) PR Lead Time by Stage Report** widget to get insights on Lead Time for Changes.

:::info

The terms *Pull Request (PR)* and *Merge Request* are interchangeable.

:::

To add the SCM PR Lead Time widget to a dashboard:

1. Go to the dashboard where you want to add the widget. Make sure you are in the correct workspace.
2. Select **Settings**, and then select **Add Widget**.
3. Select the **SCM PR Lead Time by Stage Report** widget.
4. Configure the filters for the widget.
5. On the **Settings** tab, select the relevant **Workflow Configuration Profile**, and then select **Next: Place Widget**.

   The default workflow configuration profile for lead time has four stages:

   * PR creation time.
   * Time to first comment.
   * Approval time.
   * Merge time.

    Time spent in each stage depends on the stages that a PR actually goes through. For example, if there are no comments on the PR, then there is no time to calculate for that.

    You can reconfigure the profile based on a team's SDLC process.

6. Select where you want to place the widget on the dashboard, and then select **Save Layout**.

### Calculating lead time and its stages

Here are some examples of lead time and PR stage calculations.

These examples are based on the default workflow configuration profile with the four stages of PR creation time, time to first comment, approval time, and merge time.

When reviewing these examples, consider the following:

* `Time to first comment` helps you understand the lead time between `PR creation time` and the first review. The Lead Time widget shows the average time for all PRs. You can drill down to explore individual PRs in the widget or dashboard time frame.
* There are two ways to track the time taken for a PR approval:
  * Default `Approval Time` configuration: Time spent in the review cycle when an active reviewer is involved.
  * `Approval Time + Time to First comment`: The overall approval time, starting from PR creation.
* The overall lead time is the sum of the average time spent in each stage. This is where you can determine where teams are spending their time and whether this is an acceptable range.

<details>
<summary>Example #1</summary>

For this example, assume the following series of events occurs:

1. Contributor makes a commit (`Commit created event`).
2. Contributor creates a Pull Request (`Pull Request created event`).
3. The Pull Request is approved by an approver (`Pull Request approval event`).
4. The Pull Request is merged to the repository (`Pull Request Merged event`).

As a result the following calculations are made:

```
PR creation time = Pull Request created event - Commit created event
Time to first comment = Pull Request approval event - Pull Request created event
Approval Time = 0
Merge Time = Pull Request Merged event - Pull Request approval event
```

Approval Time is calculated as `0` because there were no review comments made on the PR.

</details>

<details>
<summary>Example #2</summary>

For this example, assume the following series of events occurs:

1. Contributor makes a commit (`Commit created event`).
2. Contributor creates a pull request (`Pull Request created event`).
3. Reviewer adds a comment (`Review1 event`).
4. The Pull Request is approved by an approver (`Pull Request approval event`).
5. The Pull Request is merged to the repository (`Pull Request Merged event`).

As a result, the following calculations are made:

```
PR creation time = Pull Request created event - Commit created event
Time to first comment = Review1 event - Pull Request created event
Approval Time = Pull Request approval event - Review1 event
Merge Time = Pull Request Merged event - Pull Request approval event
```

</details>

<details>
<summary>Example #3</summary>

For this example, assume the following series of events occurs:

1. Contributor makes a commit (`Commit created event`).
2. Contributor creates a pull request (`Pull Request created event`).
3. Reviewer adds a comment (`Review1 event`).
4. Reviewer adds a comment (`Review2 event`).
5. Reviewer adds a comment (`Review3 event`).
6. The Pull Request is approved by an approver (`Pull Request approval event`).
7. The Pull Request is merged to the repository (`Pull Request Merged event`).

As a result, the following calculations are made:

```
PR creation time = Pull Request created event - Commit created event
Time to first comment = Review1 event - Pull Request created event
Approval Time = Review3 event - Review1 event
Merge Time = Pull Request Merged event - Pull Request approval event
```

</details>

## Change Failure Rate

Change Failure Rate represents the percentage of deployments that cause a failure in production.

### Configure Change Failure Rate reporting

To enable Change Failure Rate reporting in SEI, you must set up a workflow profile, and then add the Change Failure Rate widget to a dashboard.

1. Go to **Settings** and select **Workflow Profiles**.

<!-- image (24).png -->

2. Select **Add Profile** or select an existing profile to modify.

<!-- image (22).png -->

3. If this is a new profile, on the **Workflow Profile Configuration** page, enter a name for the profile.

<!-- image.png, image (9).png -->

4.  Select **Change Failure Rate**, and select the integration to use. Configuration details vary by integration type. Default values are pre-populated, and you can change them, if desired.

   * Select factors to use to calculate failed deployments.
   * Select factors to use to calculate total deployments.
   * Select whether the failed deployment calculation should be based on items that were *updated/ended* or *created/started* within the dashboard time range.

   Here you can also select **Show absolute value** if you would rather get the absolute value than the rate (percentage).

<!-- image (6).png image (3).png image (5).png -->

5. If you want to view or change the [Workspaces and Org Units](/docs/category/workspaces-and-org-units) associated with the profile, select **Associations**. Workspace and org units are automatically derived from the integration you chose for **Change Failure Rate**.

<!-- image (12).png -->

6. Select **Save** to save the profile.
7. Go to the dashboard where you want to add the Change Failure Rate widget. Make sure you are in the correct workspace.
8. Select **Settings**, and then select **Add Widget**.

<!-- image (25).png -->

9. Select the **Change Failure Rate** widget.

10. Select **Next: Place Widget**, select where you want to place the widget on the dashboard, and then select **Save Layout**.

<!-- image (15).png, image (10).png -->

The Change Failure Rate widget is now part of your dashboard.

<!-- image (19).png -->

### Calculation and scoring

Change Failure Rate performance is ranked on the following grading scale:

* Elite: Failure rate under 15 percent.
* High: Failure rate of 16 to 30 percent.
* Medium: Failure rate of 31 to 45 percent.
* Low: Failure rate above 45 percent.

The Change Failure Rate is calculated by dividing the number of failed deployments by the total number of deployments. The actual values included in this calculation are based on the following factors:

* The integration chosen in the Workflow Profile.
  * If the integration is an issue management tool, SEI counts the number of issues deployed.
  * If the integration is an SCM tool, SEI counts the number of PRs deployed.
  * If the integration is a CI/CD tool, SEI counts the number of jobs deployed.
* Filters applied to the Workflow Profile.
* OU-level filters.
* Widget-level filters.
* Dashboard time range.

<details>
<summary>Calculation example</summary>

Consider the following Change Failure Rate configuration:

* Integration: Jira
* Filter for Failed Deployment: Status Category Equals Done
* Filter for Total Deployment: Status Category Equals Done, To do, In Progress
* Calculation parameter: Ticket resolved in Dashboard Time Range
* Time Range selected on the dashboard: Last 3 months

With this configuration, the Change Failure Rate widget shows the total number of tickets with a status of **Done** divided by the total number of tickets with a status of **Done**, **In Progress**, or **To Do**.

```
Change Failure Rate = ( Tickets in Done status ) / (Tickets in Done status + Ticket in In Progress status + Tickets in To Do status )
```

Assuming there are 45 tickets in **Done** status and 90 tickets in **Done**, **In Progress**, or **To Do** status, then the Change Failure Rate is 45 divided by 90, or 0.5 (50 percent).

```
45 / 90 = 0.5
Change Failure Rate = 50%
```

</details>

## Time to Restore Service (MTTR)

Time to Restore Service, or Mean Time to Recover (MTTR), indicates how long it takes an organization to recover from a failure in production.

MTTR is a good metric for assessing the speed of your recovery process across several areas of technology. The overall time can be analyzed stage by stage using a workflow that is implemented in the organization to recover from a failure.

## Reliability (MTBF)

Mean Time Between Failures (MTBF) measures the average amount of time a system or component operates without failing. It is expressed as a continuous operating time in hours, days, or other units of time. It is an indicator of an assets reliability, or availability, and it is useful for estimating how likely an asset is to fail and how often certain failures occur. This metric is critical for reliability engineering.
