# Amazon Ads DSP (AMC)

## 🏃‍♀️ Getting Started

Connecting to your Amazon Ads account is straightforward.

1. From the [Destinations](https://app.getcensus.com/destinations) page, click **New Destination** and select Amazon Ads from the menu.
2. You'll first need to specify your desired **Region** by providing one of the following values:
   * North America: `www.amazon.com`
   * European Union: `eu.account.amazon.com`
   * Asian Pacific: `apac.account.amazon.com`
3. Complete the OAuth flow. Make sure your are signed into a user account that has permissions to both view all of your accounts, as well as submit data to them (read only accounts will not work).
4. Select the Ads account you wish to use with Census. If you'd like to sync to multiple accounts, you will need to add each as its own destination.

## 🔀 Supported Objects and Behaviors <a href="#supported-objects-and-behaviors" id="supported-objects-and-behaviors"></a>

<table data-header-hidden><thead><tr><th width="184.6600566572238"></th><th width="137"></th><th width="154"></th><th></th></tr></thead><tbody><tr><td><strong>Object Name</strong></td><td><strong>Supported?</strong></td><td><strong>Sync Keys</strong></td><td><strong>Behaviors</strong></td></tr><tr><td>Conversion Event</td><td>✅</td><td>Event Unique ID</td><td>Append</td></tr><tr><td>Audiences</td><td>🔜</td><td></td><td></td></tr></tbody></table>

### Conversion Events

Conversion Events are an [events.md](../basics/data-models-and-entities/defining-source-data/events.md "mention")sync within Census and so operate like most other Event Syncs. They do have some unique terminology and requirements. Visit [their documentation](https://advertising.amazon.com/API/docs/en-us/dsp-conversion-builder#tag/Conversion-Event-Data/operation/dspAmazonIngestConversionData) for more details.

* Like other event syncs, Amazon requires an **Event Name** and a **Timestamp**.
* **Conversion Definition ID** - Amazon requires that you define all of your conversions types beforehand as Conversion Definitions.
* **Country Code** - Must be the two-letter country code described in [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/List\_of\_ISO\_3166\_country\_codes).
* **Match Key** - This is the identifier to associate the event with. Amazon Ads currently only supports Email as a match key but may support additional options in the future. If you are going to provide Census with a pre-hashed value, must follow this format:&#x20;
  * Lowercase
  * Remove all non-alphanumeric characters \[a-zA-Z0-9] and \[.@-]
  * Remove any leading or trailing whitespace
  * Then apply SHA-256

There are also several optional fields available.

* **Currency Code** - This only applies to Off Amazon Purchase conversion definition type. This is the three letter currency code associated with the value of the event in [ISO-4217 format](https://en.wikipedia.org/wiki/ISO\_4217#List\_of\_ISO\_4217\_currency\_codes). If not provided, the currency setting on the conversion definition will be used.
* **Data Processing Options** - Currently, the only accepted value is `LIMITED_DATA_USE` which will cause Amazon to ignore this event.&#x20;
* **Units Sold** - This only applies to Off Amazon Purchase conversion definition type and represents the number of items purchased. If not provided on the conversion event, a default of 1 will be applied.
* **Value** - This has two modes depending on the conversion definition type.&#x20;
  * For Off Amazon Purchase, this represents a monetary value. Must be a minimum of 0 and must not exceed 2 decimal points. If not provided, the static value provided on the conversion definition will be used.&#x20;
  * For any other type, this represents a non-monetary value based on a scale of your choosing. Can be negative and must not exceed 2 decimal points. If not provided, the static value provided on the conversion definition will be used.

Census will send the Sync Key you specify as the unique identifier for your event sync to Amazon using the **Client Dedupe Id** property. This property has no function to Amazon other than giving them a way to ensure a single event is recorded multiple times.&#x20;

## 🚑 Need help connecting to Amazon Ads DSP?

You can send our [support team an email](mailto:support@getcensus.com) at support@getcensus.com or start a conversation from the in-app chat.
