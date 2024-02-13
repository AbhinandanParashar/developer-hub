---
title: Manage access control
description: Manage SSCA Roles and Permissions with RBAC.
sidebar_position: 80
---

# Manage SSCA Access Control

Harness's RBAC system enables you to precisely manage the user access to specific features or resources and the scope of actions they are permitted to perform. To delve deeper into the specifics of RBAC within Harness, refer to the documentation on [Role-based Access Control (RBAC)](https://developer.harness.io/docs/platform/role-based-access-control/rbac-in-harness/).


## RBAC for Remediation Tracker

The configuration of RBAC for the Remediation Tracker is possible at three levels: Account, Organization, and Project.

Here's a guide to creating a role or managing permissions for the Remediation Tracker at the account level:



1. Navigate to **Account Settings** > **Access Control** > **Roles** within your Harness Account.
2. Add a new role or select an existing one to modify.
3. Within the role, select Supply Chain Assurance. This action will display the SSCA Permissions.



![SSCA RBAC](./static/ssca-rbac.png "SSCA RBAC")


The Remediation Tracker is governed by the following permissions:



* **View**: Grants users the ability to view trackers in a read-only mode.
* **Create/Edit**: Enables users to create new trackers and edit existing ones.
* **Close:** Allows users to close any trackers.

For the Organization level, open the same account settings and proceed to **Organizations**. Choose your organization and under **Organization Level Access Control and Audit Trail**, select **Access Control**. Here, configure the roles and permissions at the organization level in a manner similar to the account level process.

To set roles and permissions at the Project level, navigate to the **Project** section from the module navigation bar, and select **Access Control**. Follow similar steps as above to establish the roles and permissions for the project level.

