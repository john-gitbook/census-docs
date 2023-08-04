---
description: This page describes how to use Census with Marketo.
---

# Marketo

## 🏃‍♀️ Getting Started

In this guide, we will show you how to connect Marketo to Census and create your first sync.

### Prerequisites

* Have your Census account ready. If you need one, [create a Free Trial Census account](https://app.getcensus.com/) now.
* Have your Marketo account ready, with admin access to create API-only users and API credentials.
* Have the proper credentials to access to your data source. See our docs for each supported data source for further information:
  * [Azure Synapse](../sources/azure-synapse.md)
  * [Databricks](https://docs.getcensus.com/sources/databricks)
  * [Elasticsearch](https://docs.getcensus.com/sources/elasticsearch)
  * [Google BigQuery](https://docs.getcensus.com/sources/google-bigquery)
  * [Google Sheets](https://docs.getcensus.com/sources/google-sheets)
  * [MySQL](https://docs.getcensus.com/sources/mysql)
  * [Postgres](https://docs.getcensus.com/sources/postgres)
  * [Redshift](https://docs.getcensus.com/sources/redshift)
  * [Rockset](https://docs.getcensus.com/sources/rockset)
  * [Snowflake](https://docs.getcensus.com/sources/snowflake)
  * [SQL Server](https://docs.getcensus.com/sources/sql-server)

### 1. Create a Marketo API User

Before setting up API credentials for Census, you'll first need a Marketo Role with API Access, as well as a user with that role.

#### API Access Role

None of the default Marketo Roles have API access so if this is your first API integration, you'll first need to create an API access role. [Marketo's documentation walks through creating a new API Access role](https://developers.marketo.com/rest-api/custom-services/) as well as your first user.

You can view/edit role permissions in **Admin, Users & Roles**, then clicking the **Roles** tab.

Whether you're using an existing role or creating a new one, please make sure it has at least the following permissions: **Read-Write People** and **Read-Write Named Accounts**. To use Custom Objects, we'll also need **Read-Write Custom Object** and **Read-Write Custom Object Type**.

{% hint style="warning" %}
Note: Even though your Marketo instance may support Custom Objects, the Custom Object Metadata API is not an out-of-the-box feature on Select Plans at Marketo and doesn’t automatically come with Custom Objects. If you still don't see Custom Objects in Census, you may need to contact your Marketo Account Manager to make sure you have access to the Custom Object Metadata API.
{% endhint %}

#### API Only User

We recommend you create a new Marketo API User so that you can track changes made by your Census syncs. Either way, the user must be marked **API Only** during creation.

### 2. Gather Marketo API Credentials

To connect Census to Marketo, you'll need to collect three pieces of information:

* Endpoint URL
* Client ID
* Client Secret

Back in **Admin**, expand the **Integrations** menu on the left and select the **Web Services** option. Scroll down to the **REST API** section. Copy and paste the **Endpoint URL** (you can excluding the `/rest` part).

![](../.gitbook/assets/screely-1618889215086.png)

Next we'll create a new LaunchPoint Service. Click on **LaunchPoint** and select **New** > **New Service.**

Your new service should have the following properties:

* Display Name: Census
* Service: **Custom**
* Description: Census Data Integration
* API Only User: _\[The user you created in step 1]_

Once created, you'll see your new service in the list of services. Click on **View Details**. You will need to copy the **Client ID** and **Client Secret** here.

![](../.gitbook/assets/screely-1618889197214.png)

### 3. Adding Credentials to Census

With all three pieces of information, return to Census and visit the **Destinations** tab. Click on the **New Destination** button and select **Marketo** from the menu. Copy and paste the values into the dialog and hit save. You should be clear to create a new sync!

![](../.gitbook/assets/screely-1618889184718.png)

## 🗄 Supported Objects

Census currently supports syncing to the following Marketo objects.

<table data-header-hidden><thead><tr><th width="236.33333333333331" align="right"></th><th width="214" align="center"></th><th></th></tr></thead><tbody><tr><td align="right"><strong>Object Name</strong></td><td align="center"><strong>Supported?</strong></td><td><strong>Identifiers</strong></td></tr><tr><td align="right">Lead</td><td align="center">✅</td><td>Object ID, any Text/Number</td></tr><tr><td align="right">Named Account</td><td align="center">✅</td><td>Object ID, any Text/Number</td></tr><tr><td align="right">Custom Objects</td><td align="center">✅</td><td>Object ID, any Text/Number</td></tr><tr><td align="right">Static List Membership</td><td align="center">✅</td><td></td></tr><tr><td align="right">Custom Activities</td><td align="center">✅</td><td></td></tr></tbody></table>

[Contact us](mailto:support@getcensus.com) if you want Census to support more objects for Marketo.

## 🔄 Supported Sync Behaviors

{% hint style="info" %}
Learn more about all of our sync behaviors on our [Core Concepts page](../basics/core-concept/#the-different-sync-behaviors).
{% endhint %}

<table data-header-hidden><thead><tr><th width="182.33333333333331" align="right"></th><th width="146" align="center"></th><th align="center"></th></tr></thead><tbody><tr><td align="right"><strong>Behaviors</strong></td><td align="center"><strong>Supported?</strong></td><td align="center"><strong>Objects</strong></td></tr><tr><td align="right"><strong>Update or Create</strong></td><td align="center">✅</td><td align="center">Lead, Named Account, Custom Objects</td></tr><tr><td align="right"><strong>Update Only</strong></td><td align="center">✅</td><td align="center">Lead, Named Account, Custom Objects</td></tr><tr><td align="right"><strong>Append</strong></td><td align="center">✅</td><td align="center">Custom Activities</td></tr><tr><td align="right"><strong>Mirror</strong></td><td align="center">✅</td><td align="center">Lead, Static List Membership, Custom Objects</td></tr></tbody></table>

{% hint style="warning" %}
Please be aware that Update Only and Mirror make use of less efficient Marketo APIs and will result in more API usage for the same number of records.
{% endhint %}

[Contact us](mailto:support@getcensus.com) if you want Census to support more Sync behaviors for Marketo.

## 🚑 Need help connecting to Marketo?

[Contact us](mailto:support@getcensus.com) via support@getcensus.com or start a conversation with us via the [in-app](https://app.getcensus.com) chat.
