---
icon: flask
---

# Experiments and Analysis

Census makes it easy to understand the shape of the segments you're creating and how they're performing once you've synced them to your destinations.

## Setting up Split Tests

Once you've created a segment, you can take advantage of split test experiments to test how your new segment performs. A split test divides the people in your segment randomly into one or more **treatments** as well as a **control** cohort, which should be used as a baseline to compare the impact of your campaign. Each cohort has a percentage size you control, letting you set the relative sizes of each size.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-08 at 3.16.39 PM.png" alt=""><figcaption></figcaption></figure>

Split testing enables a number of marketing efforts:

* Create a simple treatment with control group and measure the increased conversion rate over users that received the treatment.
* Divide a segment into multiple treatments for different channels and compare relative conversion rates of the same segment across each.
* Use a treatment and control group to "ramp up" a very large campaign over time. Start with 10% of segment and grow the treatment once you're confident it's performing as expected.

Each cohort can be [synced to their own set of destinations](syncing-segments.md), including back to warehouse, and users appearing in each cohort are available in Warehouse Writeback (see [below](analyzing-segments.md#detailed-segment-performance)).

## Tracking Segment Size

One of the most important signals when creating segments is its size. Too big and your segment is too vague to enable effective targeting. Too small and the size may not be worth your time to target at all.

<figure><img src="../../.gitbook/assets/unnamed.png" alt=""><figcaption></figcaption></figure>

When creating segments, Census will show you the estimated segment size based the conditions you've defined. Depending on your warehouse type, Census will automatically refresh the size as more conditions are added or you can refresh it manually as well.

Once your segment has been created, you can visit the **Activity** tab at any point to understand how your segment size has changes over time, including after making changes to the segment definition.

## Previewing Members

At any point, you can also view a sample of the members of a particular segment by pressing the **Preview Results** button in the top right of the segment view. This will show the first 25 members of your segment as currently defined.

<figure><img src="../../.gitbook/assets/Artboard.png" alt=""><figcaption></figcaption></figure>

## Audience Comparisons

When it's easy to create new segments, you can end up in a world of too many segments and it's hard to tell if a new segment is unique, even if you can see what members look like. In this case, you can compare your segment against any other existing segment by visiting the **Overlap** tab on your segment.

<figure><img src="../../.gitbook/assets/760-b937f5942ce3a9913c2afc4267cebcde96975ff5.gif" alt=""><figcaption></figcaption></figure>

## Detailed Segment Performance

Create customized metrics and track segment and cohort performance over time. Our Performance reporting makes it easy to understand the impact of your experiments. Understand the lift from different offers, or learn how your segments perform across your destinations. After running your experiment for an appropriate amount of time, implement the winning variant and start another experiment.

<figure><img src="../../.gitbook/assets/Snag_2f5839b5.png" alt=""><figcaption></figcaption></figure>

For the deepest level of analysis, you can take advantage of [Warehouse Writeback](../sync-monitoring/warehouse-writeback.md), which logs all sync activity back to your data source. You can use this data to determine when users were added and removed from segments in each of the destinations your segment is synced to or the relative conversion performance of users across cohorts.

To take advantage of Warehouse Writeback for your analysis, ensure it is enabled on your warehouse connection.
