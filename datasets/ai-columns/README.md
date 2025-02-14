---
icon: line-columns
---

# AI Columns

AI Columns enable you to dynamically generate unique content for each row in your dataset using LLMs like OpenAI, Anthropic Claude and Google Gemini (coming soon). With AI Columns, you can define a prompt and use [liquid templating](../../basics/core-concept/liquid-templates.md) to reference values from other columns. This setup allows you to send a customized GPT prompt request for each row, with the response automatically written back to your AI Column. The AI Columns materialize in your warehouse as well.

{% hint style="info" %}
Try AI Columns for free using trial [credits](../../misc/credits.md)! No need for an API key until your trial credits run out.
{% endhint %}

{% embed url="https://youtu.be/5AxWR1QyCos" %}

#### Example Use Cases

1. Automatically generate personalized email content or messages based on customer data.
2. Generate insights or recommendations from transactional data, such as suggesting complementary products based on purchase history.
3. Sentiment analysis of email received by sales team from outbound campaign to help with categorization and reporting
4. Summarize product usage among specific features by “high” or “low” to identify upsell fits and run PLG playbooks
5. Clean up data by removing special characters from a column

checkout our [Recipe Book](prompts-recipe-book.md) for more examples and sample prompts.

#### Pre-requisites

* Dataset should have a Unique ID column

Note : You will need your API key to connect OpenAI (ChatGPT) or Claude once you run out of Census [credits](../../misc/credits.md).

* To create a new OpenAI API key, log into OpenAI and navigate to [Dashboard / API keys](https://platform.openai.com/api-keys) and generate a new Project API Key.
* To create a new Anthropic API Key, navigate to [Anthropic Console](../../) > Settings > API Keys and generate a new Key.

#### How to create a AI Column

If you are a video person, watch [how to create a GPT column](https://youtu.be/5AxWR1QyCos). Otherwise, follow the steps below.

**Step 1:** [Log into](https://app.getcensus.com/) your Census account.

**Step 2:** Navigate to the Datasets tab by clicking on `Datasets` in the left navigation panel.

**Step 3:** Choose a dataset where you want to add a new AI-based column. Make sure the Dataset has a Unique ID column assigned

**Step 4:** Select `Enrich & Enhance` on your top right corner, choose `AI` and your preferred LLM provider.

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-26 at 2.02.19 PM.png" alt=""><figcaption><p>Census Create AI Column</p></figcaption></figure>

**Step 5:** Skip this step if you have trial [credits](../../misc/credits.md). Connect to selected platform (OpenAI, Anthropic, Google) using your API Key and click Next.

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-29 at 12.34.53 PM (1).png" alt=""><figcaption><p>AI Columns Connect</p></figcaption></figure>

**Step 6:** Create a GPT prompt and fill the column name.

Refer to [Sample GPT Prompts](prompts-recipe-book.md) for inspiration on GPT based prompts

<figure><img src="../../.gitbook/assets/Screenshot 2024-12-26 at 2.12.01 PM.png" alt=""><figcaption><p>Census AI Column Prompt</p></figcaption></figure>

* Model Type - you can select from the provided list of GPT based models. We recommend `gpt-4o-mini` model to limit cost associated with the OpenAI tokens.
* The expected output type - there are several optional properties to help you guarantee data quality.
* The prompt to run against each row of your data. Your prompt can leverage [Liquid templating](../../basics/core-concept/liquid-templates.md) to reference column values.

**Step 7:** Hit the Create button and that's it. Census will generate a AI based column into your dataset.

This step can take several minutes. Behind the scene Census sets up OpenAI/Anthropic/Google as a destination and runs a sync across all your rows in the selected dataset.

The AI columns refresh every 6 hours and only process new rows.

#### Warehouse Writeback

The results generated by AI Columns are stored directly in your source warehouse. Census creates a new table within the Census schema, prefixed with `DATASET_COLUMN_GPT`, containing the AI Column.

This allows you to not only sync these AI-generated columns to your destination via Census but also explore them further within your warehouse.

{% hint style="warning" %}
AI Columns are currently supported on Snowflake, Redshift, BigQuery, Databricks, and Postgres with more warehouses coming soon.
{% endhint %}

#### Rate Limits

{% hint style="info" %}
Requests made by Census to the LLM provider (ex. OpenAI) are subject to daily rate limits, which may cause the underlying sync to stall. Rate limits can typically be increased by upgrading the tier of your organization with the LLM provider.
{% endhint %}

For more information, please see the rate limit policies for your specific LLM provider.

* [Open AI Rate Limits](https://platform.openai.com/docs/guides/rate-limits#usage-tiers)
* [Anthropic Rate Limits](https://docs.anthropic.com/en/api/rate-limits)

#### Privacy and Security

Census only sends your prompt to OpenAI. If your prompt includes specific dataset columns via liquid templates, these columns will be included as part of the prompt sent to OpenAI. No other data is shared with OpenAI or any other LLM.

OpenAI does not use the data sent via Census for training its models. For [more information](https://community.openai.com/t/does-the-openai-api-get-access-to-the-data-i-send-it-or-store-the-data/599538), please refer to OpenAI’s data usage policies.

All OpenAI calls are made through secure HTTPS channels, and only successful responses are saved to your dataset.
