---
description: This page describes how to use Census with HubSpot.
---

# HubSpot

## 🏃‍♀️ Getting Started

In this guide, we will show you how to connect HubSpot to Census and create your first sync.

{% embed url="https://www.youtube.com/watch?v=pkbmg-TmTiY&feature=emb_title" %}

### Prerequisites

* Have your Census account ready. If you need one, [create a Free Trial Census account](https://app.getcensus.com/) now.
* Have your HubSpot account ready.
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

### 1. Connect HubSpot

* Once you are in Census, Navigate to [Destinations](https://app.getcensus.com/destinations)
* Click the **New Destination** button
* Select HubSpot in the Add Destination menu and click **Connect**

![](../.gitbook/assets/screely-1651800460992.png)

Follow HubSpot OAuth flow to connect HubSpot. Your end state should look something like this below.

![](../.gitbook/assets/screely-1651800471783.png)

### 2. Create your first Sync

Before you create your first sync, you'll also need to connect your data source. Once you've done that, head to the [Sync page](https://app.getcensus.com/syncs) and click the **Add Sync** button

In the " **What data do you want to sync?"** section

* For the **Connection**, select the data warehouse you connected in step 2
* For the **Source,** select the model you created in step 3

Next up is the **"Where do you want to sync data to?"** section

* Pick HubSpot as **the Connection**
* For Object, pick the one you want to sync data to; Contact or Company.

For the " **How should changes to the source be synced?"** section

* Select your desired Sync Behavior from **Update or Create**, **Update Only, or Mirror**
* Pick the right mapping key, it could be Email for Contacts, Domain for Companies but we recommend you use your own internal id if possible

Finally, select the fields you want to update in the Mapper in the **"Which Fields should be updated?"** section

* Here simply map the field from your HubSpot instance to the column from your model.

The end result should look something like this

![](../.gitbook/assets/screely-1659718450629.png)

Click the **Next** button to see the final preview which will have a recap of what will happen when you start the sync

### 3. Confirm the data is in HubSpot

Now go back to your HubSpot and go view a record type (Contact or Company) that should have been updated. If everything went well, you should see your data in HubSpot

![](https://s3.amazonaws.com/helpscout.net/docs/assets/5bb7d5d0042863158cc71f7e/images/5f656c764cedfd00176363f8/file-aQC3QWxxq7.png)

That's it, in just a few steps, you've connected Census to HubSpot and started syncing data from your warehouse to HubSpot 🎉

## 🏎 Sync Speed

Census connects to HubSpot using their "Connected App" model, which are not subject to the daily HubSpot API call limit, only to the burst limit (100 requests/10 sec). Your Census syncs will not impact your HubSpot daily API limits or nor any other HubSpot integrations. For more information, see [HubSpot docs](https://legacydocs.hubspot.com/apps/api\_guidelines).

{% hint style="warning" %}
The choice of your sync identifier and behavior can have _**very drastic**_\*\* \*\* performance impacts to your sync.

Using a HubSpot Object ID or Contact Email as identifiers in HubSpot is fast, but using all other fields as identifiers is _**very**_ slow. That means that any syncs that create new records in HubSpot (other than Contacts by Email) will be slow. We're working with HubSpot to try and increase the speed of their APIs in order to improve our HubSpot sync speed.
{% endhint %}

| **Service**                 | Public API rate limit | **Records sync / Minute** |
| --------------------------- | --------------------- | ------------------------- |
| HubSpot (Free & Start Plan) | 600 calls / min       | \~600                     |
| HubSpot (Pro & Enterprise)  | 900 calls / min       | \~900                     |
| API Boost Add-on            | 1,200 calls / min     | \~1,200                   |

Please be aware that with Custom Objects require extra API calls and are even slower as a result (about 1/3 the speed).

## 🗄 Supported Objects

[Contact us](mailto:support@getcensus.com) if you're looking for Census to support other HubSpot objects!

|         **Object Name** | **Supported?** | **Sync Keys**                   |
| ----------------------: | :------------: | --------------------------------- |
|                 Company |        ✅       | Object ID, any Text/Number        |
|                 Contact |        ✅       | Object ID, Email, any Text/Number |
|   Contact & Static List |        ✅       | Email                             |
|                    Deal |        ✅       | Object ID, any Text/Number        |
|                 Product |        ✅       | Object ID, any Text/Number        |
|               Line Item |        ✅       | Object ID, any Text/Number        |
|           Custom Object |        ✅       | Object ID, any searchableProperty |
| Custom Behavioral Event |        ✅       | Unique Event ID                   |
|                   Email |        ✅       | N/A                               |

### Custom Objects

Custom Objects are available on HubSpot Enterprise plans.

As of March 2021, only properties in the searchableProperties set are usable as sync identifiers to HubSpot Custom Objects. This is a bit confusing as this label only appears in the HubSpot API. A searchable property can be added to a Custom Object via HubSpot's API. The calls to make this update can be found in HubSpot's [Custom Objects API Docs](https://t.sidekickopen08.com/s3t/c/5/f18dQhb0S7kF8cFC2RW1K7Z1759hl3kW7\_k2841CXdp3VP16Md1G7ysXW2dykfC1TtC07101?te=W3R5hFj4cm2zwW3H4THp3ZZnXLW49Rd2x4hCWyFW43X00w43T4NTW43P1-Z3zfPd7W3FcKxL3FcKxJW3Fd-wl43T4CBw3C9Ryyb7l2\&si=8000000004039937\&pi=71ef6659-f8eb-4943-8de6-e67c9ea6453c) > Object Schema Tab > searchableProperties.

Additionally, HubSpot has some apps available in their marketplace like [Dotsquares](https://hubspot.dotsquares.com/easy-custom-objects-setup/) that can assist with Custom Object management.

If you need a hand making one of your existing Custom Object fields as searchable, please contact Census's Support team and we can walk you through it!

### Managing Object Associations

HubSpot supports an advanced method of defining relationships between objects they call [Associations](https://knowledge.hubspot.com/crm-setup/create-and-use-association-labels). Associations have a number of different properties:

* They're supported between all HubSpot object pairs, including custom objects.
* They can represent one-to-many and many-to-many relationships.
* Associations can be labeled or unlabeled. HubSpot Professional and Enterprise plans also support custom labels.

Many-to-many associations can be updated in Census syncs on either side of the associations, while one-to-many associations can only be set on the child or many side.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-01 at 2.54.52 PM.png" alt=""><figcaption><p>Census Company/Contact Association</p></figcaption></figure>

#### Labeled Associations

Labels in HubSpot are a bit strange and Census provides some advanced configuration to make updating and removing labels a bit more straightforward.

When creating a labeled association between two objects in HubSpot, HubSpot will also automatically create an unlabeled association. Additionally, when creating an association from a contact to a company, HubSpot will create another association labeled Primary. That means that adding a labeled association with a Census sync may actually create up to three actual associations.



<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption><p>Hubspot Labeled Association</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-08-01 at 2.39.44 PM.png" alt=""><figcaption><p>Census Labeled Association Sync Mapping</p></figcaption></figure>



Unfortunately, HubSpot does not offer a way to remove these default associations when they're no longer necessary when removing the labeled association Census created. These associations may have actually been created intentionally so Census also cannot delete them automatically.

To navigate this, Census provides an advanced configuration for HubSpot syncs: **Automatically clean up orphaned default associations when removing any associations**.

![](../.gitbook/assets/screely-1659672959589.png)

When this behavior is enabled and a Census sync removes a labeled association, we'll also check to see if the remaining associations are only the unlabeled and Primary labeled associations, if so, we'll automatically remove those associations as well.

By default, this feature is not enabled to avoid accidentally deleting associations that were created outside the sync and should still exist.

### Custom Behavioral Events

Custom Behavioral Events require a little bit of prep work. You'll first need to jump into HubSpot and create your Custom Behavior Event (see [HubSpot's instructions for how to do that](https://knowledge.hubspot.com/analytics-tools/create-custom-behavioral-events)).

You'll need to both create the event AND add all of the custom properties beforehand. Once you've done so, copy and paste HubSpot's internal name for object, you'll need to provide that to the `Event Name` property during the Census sync.

Note: The custom fields you've added will not show inside Census, you'll need to use the `New Custom Field` option to create the matching fields on Census, make sure they're named exactly the same (keep in mind, names are case sensitive!).

## 🔄 Supported Sync Behaviors

{% hint style="info" %}
Learn more about what all of our sync behaviors on our [Core Concept page](../basics/core-concept/#the-different-sync-behaviors).
{% endhint %}

|        **Behaviors** | **Supported?** |    **Objects**   |
| -------------------: | :------------: | :--------------: |
| **Update or Create** |        ✅       | All except Email |
|      **Update Only** |        ✅       | All except Email |
|           **Mirror** |        ✅       | All except Email |
|           **Append** |        ✅       |       Email      |

[Contact us](mailto:support@getcensus.com) if you want Census to support more Sync Behaviors for HubSpot.

## 🔑 Require Permissions

Census requires that the connecting HubSpot user have Super Admin permissions in order to access all supported HubSpot objects. If you have limited permissions and still want to connect Census to HubSpot, contact the [contact the Census support team](mailto:support@getcensus.com).

## 🚑 Need help connecting to HubSpot?

[Contact us](mailto:support@getcensus.com) via support@getcensus.com or start a conversation with us via the [in-app](https://app.getcensus.com) chat.
