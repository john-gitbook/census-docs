---
description: >-
  Census Enrichment makes it easy to enrich Person and Company data with
  third-party data and sync them to any business apps. The outcome also
  materializes in your data warehouse.
icon: chart-simple-horizontal
---

# Enrichment Columns

Census connects with third party data providers like Clearbit (Now Hubspot Breeze), Apollo and others

### Challenges with Enrichments CRM-based Enrichments

Enriching first party data, in your data warehouse or CRM systems, with third party data (e.g. company size, address, etc) is challenging for a number of reasons:

* Running enrichments directly on CRM eats up your API quota
* CRM based enrichments are not easily accessible across other business apps like marketing tools or outreach tools
* A single enrichment provider is not sufficient because no single solution has all the correct data
* You still have to dance around combining first party data, third party data, and manual edits to make these enrichments useful for personalized campaigns

Historical, enrichment flow includes hitting an API directly on top of a CRM tool, storing it in the CRM tool, sending it to your warehouse, run sql to combine the company or person data, then sync this data back to CRM or marketing automation destinations. Along the way, this leads to race conditions, duplicated records and unnecessary enrichment cost.

**Census Enrichment simplifies this entire workflow. With just a few clicks, you can enrich your warehouse (and CRM ) data, combine it seamlessly with your existing datasets, and sync enriched insights to any business app—all in minutes.**

### Setup Enrichments

To set up enrichments, you can follow our [quick start guide](quick-start.md).

Once your enrichment is configured, Census will start querying your enrichment service and populating results.

You can immediately start using the new enrichment-powered attributes on your datasets within Census Segments and Syncs. Note that you'll see an indication in syncs and segments if the enrichment is still actively running but data will be backfilled in future sync runs if enrichment data is not immediately available at sync time.

{% hint style="info" %}
Enrichments is currently supported on Snowflake, Redshift, BigQuery, Databricks, and Postgres with more warehouses coming soon!
{% endhint %}

### Warehouse Writeback

The outcome of Enrichment Columns materializes in your data warehouse under Census Schema. Census Datasets join your enriched columns with your first party data to help you visualize, explore and sync to any destination.

### Supported Enrichment Services

Here are the list of services Census currently integrations to provide data enrichment and this list is constantly growing. Looking for a particular service, [let us know](mailto:support@getcensus.com)!

#### Clearbit

Look up person and company data based on an email or domain. Sync fresh and reliable data across your systems in real time with over 100 attributes on more than 44 million companies and 350 million contacts.

Keep in mind:

* Census uses the Clearbit API **Secret Key**, not the Publishable Key. This should be available in the [Clearbit API](https://dashboard.clearbit.com/api) section.
* Enriching does use API credits. Please see your [Clearbit Dashboard](https://dashboard.clearbit.com/dashboard) to track your usage.

| Data Category | Identifier | Data Points                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Person        | email      | id, name.givenName, name.familyName, name.fullName, location, timeZone, utcOffset, geo.city, geo.state, geo.country, geo.lat, geo.lng, bio, site, avatar, employment.name, employment.title, employment.role, employment.subRole, employment.seniority, employment.domain, facebook.handle, github.handle, github.id, github.avatar, github.company, github.blog, github.followers, github.following, twitter.handle, twitter.id, twitter.followers, twitter.following, twitter.location, twitter.site, twitter.statuses, twitter.favorites, twitter.avatar, linkedin.handle, googleplus.handle, fuzzy, emailProvider, indexedAt                                                                                                                                                                                                                                                                                                                          |
| Company       | domain     | id, name, legalName, domain, domainAliases, site.phoneNumbers, site.emailAddresses, tags, category.sector, category.industryGroup, category.industry, category.subIndustry, category.sicCode, category.naicsCode, description, foundedYear, location, timeZone, utcOffset, geo.streetNumber, geo.streetName, geo.subPremise, geo.city, geo.state, geo.stateCode, geo.postalCode, geo.country, geo.countryCode, geo.lat, geo.lng, identifiers.usEIN, metrics.raised, metrics.alexaUsRank, metrics.alexaGlobalRank, metrics.employees, metrics.employeesRange, metrics.marketCap, metrics.annualRevenue, metrics.estimatedAnnualRevenue, metrics.fiscalYearEnd, facebook.handle, linkedin.handle, twitter.handle, twitter.id, twitter.bio, twitter.followers, twitter.following, twitter.location, twitter.site, twitter.avatar, crunchbase.handle, logo, emailProvider, type, phone, tech, techCategories, parent.domain, ultimateParent.domain, indexedAt |

#### Apollo.io (coming soon)

### Need help with data enrichment?

having issues with Enrichments or have feedback for us? [Contact us](mailto:support@getcensus.com) via support@getcensus.com or start a conversation with us via the [in-app](https://app.getcensus.com) chat.
