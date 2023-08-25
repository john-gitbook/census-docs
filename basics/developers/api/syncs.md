# Syncs

### GET /syncs

This endpoint returns a list of your syncs.

See [Pagination](./#pagination) for standard URL parameters and response data.

{% tabs %}
{% tab title="Request" %}
```
curl 'https://app.getcensus.com/api/v1/syncs' \
--header 'Authorization: Bearer [API_TOKEN]'
```
{% endtab %}

{% tab title="Response" %}
<pre class="language-json"><code class="lang-json">{
    "status": "success",
<strong>    "data": [
</strong>        {
            "id": 61,
<strong>            "label": null,
</strong>            "schedule_frequency": "never",
            "schedule_day": null,
            "schedule_hour": null,
            "schedule_minute": null,
            "cron_expression": null,
            "created_at": "2021-10-22T00:40:11.246Z",
            "updated_at": "2021-10-22T00:43:44.173Z",
            "operation": "upsert",
            "paused": false,
            "status": "Ready",
            "lead_union_insert_to": null,
            "field_behavior": "specific_properties",
            "field_normalization": null,
            "mirror_strategy": null,
            "failed_run_notifications_enabled": true,
	    "failed_record_notifications_enabled": true,
	    "failed_record_notifications_threshold_percent": 75
            "source_attributes": {
                "connection_id": 4,
                "object": {
                    "type": "model",
                    "id": 15,
                    "name": "braze_test",
                    "created_at": "2021-10-11T20:52:58.293Z",
                    "updated_at": "2021-10-14T23:15:18.508Z",
                    "query": "select cast('test@getcensus.com' as VARCHAR(2000)) as email, cast('random' as VARCHAR(2000)) as random_prop"
                }
            },
            "destination_attributes": {
                "connection_id": 15,
                "object": "user"
            },
            "triggers": {
                "dbt_cloud": {
                    "project_id": "12345",
                    "job_id": "123456"
                },
                "fivetran": {
                    "job_id": "test_job_id",
                    "job_name": "test_job_name"
                }
            },
            "mappings": [
                {
                    "from": {
                        "type": "column",
                        "data": "EMAIL"
                    },
                    "to": "external_id",
                    "is_primary_identifier": true,
                    "generate_field": false,
                    "preserve_values": false,
                    "operation": null
                },
                {
                    "from": {
                        "type": "constant_value",
                        "data": {
                            "value": "test",
                            "basic_type": "text"
                        }
                    },
                    "to": "first_name",
                    "is_primary_identifier": false,
                    "generate_field": false,
                    "preserve_values": false,
                    "operation": null
                }
            ]
        },
        {
            "id": 60,
            "label": null,
            "schedule_frequency": "never",
            "schedule_day": null,
            "schedule_hour": null,
            "schedule_minute": null,
            "cron_expression": null,
            "created_at": "2021-10-22T00:38:32.191Z",
            "updated_at": "2021-10-22T00:43:47.858Z",
            "operation": "upsert",
            "paused": false,
            "status": "Ready",
            "lead_union_insert_to": null,
            "field_behavior": "specific_properties",
            "field_normalization": null,
            "mirror_strategy": null,
            "failed_run_notifications_enabled": true,
	    "failed_record_notifications_enabled": true,
	    "failed_record_notifications_threshold_percent": 75
            "source_attributes": {
                "connection_id": 4,
                "object": {
                    "type": "model",
                    "id": 15,
                    "name": "braze_test",
                    "created_at": "2021-10-11T20:52:58.293Z",
                    "updated_at": "2021-10-14T23:15:18.508Z",
                    "query": "select cast('test@getcensus.com' as VARCHAR(2000)) as email, cast('random' as VARCHAR(2000)) as random_prop"
                }
            },
            "destination_attributes": {
                "connection_id": 15,
                "object": "user"
            },
            "mappings": [
                {
                    "from": {
                        "type": "column",
                        "data": "EMAIL"
                    },
                    "to": "external_id",
                    "is_primary_identifier": true,
                    "generate_field": false,
                    "preserve_values": false,
                    "operation": null
                },
                {
                    "from": {
                        "type": "constant_value",
                        "data": {
                            "value": "usa",
                            "basic_type": "text"
                        }
                    },
                    "to": "country",
                    "is_primary_identifier": false,
                    "generate_field": false,
                    "preserve_values": false,
                    "operation": null
                }
            ]
        }
    ],
    "next": "https://app.getcensus.com/api/v1/syncs?page=2&#x26;per_page=2",
    "pagination": {
        "total_records": 4,
        "per_page": 2,
        "prev_page": null,
        "page": 1,
        "next_page": 2,
        "last_page": 2
    }
}
</code></pre>
{% endtab %}
{% endtabs %}

| Data Property   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A list of syncs | <p>A list of your syncs. The properties of a sync are expanded on below in the POST /syncs endpoint.<br></p><p>Along with the properties mentioned above, this endpoint returns an <code>id</code>, <code>created_at</code>, <code>updated_at</code>, and <code>status</code> for each sync.<br><br>Possible values for the <code>status</code> property:<br> - "Ready": no sync history</p><p> - "Up to Date": last sync completed<br> - "Failing": last sync failed</p> |

### GET /syncs/\[ID]

This endpoint returns information on a specific sync.

{% tabs %}
{% tab title="Request" %}
```
curl 'https://app.getcensus.com/api/v1/syncs/[ID]' \
--header 'Authorization: Bearer [API_TOKEN]'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "status": "success",
    "data": {
        "id": 61,
        "label": null,
        "schedule_frequency": "never",
        "schedule_day": null,
        "schedule_hour": null,
        "schedule_minute": null,
        "cron_expression": null,
        "created_at": "2021-10-22T00:40:11.246Z",
        "updated_at": "2021-10-22T00:43:44.173Z",
        "operation": "upsert",
        "paused": false,
        "status": "Ready",
        "lead_union_insert_to": null,
        "field_behavior": "specific_properties",
        "field_normalization": null,
        "mirror_strategy": null,
        "failed_run_notifications_enabled": true,
	"failed_record_notifications_enabled": true,
	"failed_record_notifications_threshold_percent": 75
        "source_attributes": {
            "connection_id": 4,
            "object": {
                "type": "model",
                "id": 15,
                "name": "braze_test",
                "created_at": "2021-10-11T20:52:58.293Z",
                "updated_at": "2021-10-14T23:15:18.508Z",
                "query": "select cast('test@getcensus.com' as VARCHAR(2000)) as email, cast('random' as VARCHAR(2000)) as random_prop"
            }
        },
        "destination_attributes": {
            "connection_id": 15,
            "object": "user"
        },
        "triggers": {
            "dbt_cloud": {
                "project_id": "12345",
                "job_id": "123456"
            },
            "fivetran": {
                "job_id": "test_job_id",
                "job_name": "test_job_name"
            }
        },
        "mappings": [
            {
                "from": {
                    "type": "column",
                    "data": "EMAIL"
                },
                "to": "external_id",
                "is_primary_identifier": true,
                "generate_field": false,
                "preserve_values": false,
                "operation": null
            },
            {
                "from": {
                    "type": "constant_value",
                    "data": {
                        "value": "test",
                        "basic_type": "text"
                    }
                },
                "to": "first_name",
                "is_primary_identifier": false,
                "generate_field": false,
                "preserve_values": false,
                "operation": null
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

| Data Property | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A sync        | <p>Information on a sync. The properties of a sync are expanded on below in the POST /syncs endpoint.<br></p><p>Along with the properties mentioned above, this endpoint returns an <code>id</code>, <code>created_at</code>, <code>updated_at</code>, and <code>status</code> for the sync.<br><br>Possible values for the <code>status</code> property:<br> - "Ready": no sync history</p><p> - "Up to Date": last sync completed<br> - "Failing": last sync failed</p> |

### POST /syncs

This endpoint creates a sync with the given data.

{% tabs %}
{% tab title="Request" %}
```
curl --location --request POST 'https://app.getcensus.com/api/v1/syncs' \
--header 'Authorization: Bearer [API_TOKEN]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "label": "TEST 1",
    "operation": "mirror",
    "schedule_frequency": "daily",
    "destination_attributes": {
        "connection_id": 15,
        "object": "user_data"
    },
    "source_attributes": {
        "connection_id": 12,
        "object": {
            "type": "model",
            "name": "test_ads"
        }
    },
    "mappings": [
        {
            "from": {
                "type": "column",
                "data": "hashed_email"
            },
            "to": "user_identifier.hashed_email_PREHASHED",
            "is_primary_identifier": true
        },
        {
            "from": {
                "type": "column",
                "data": "list_id"
            },
            "to": "list_id",
            "lookup_object": "user_list",
            "lookup_field": "name"
        },
        {
            "from": {
                "type": "constant_value",
                "data": {
                    "value": "cohort_1",
                    "basic_type": "text"
                }
            },
            "to": "cohort"
        }
    ]
}'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "status": "created",
    "data": {
        "sync_id": 4545
    }
}
```
{% endtab %}
{% endtabs %}

| Request Property                                  | Description                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| operation                                         | <p><code>required</code>. How records are synced to the destination. Valid options:</p><ul><li><code>append</code></li><li><code>insert</code></li><li><code>mirror</code></li><li><code>update</code></li><li><code>upsert</code></li></ul>                                                                                                            |
| source\_attributes                                | `required`. Attributes used to identify the data source for this sync. The specific properties are described below.                                                                                                                                                                                                                                     |
| destination\_attributes                           | `required`. Attributes used to identify the destination for this sync. The specific properties are described below.                                                                                                                                                                                                                                     |
| mappings                                          | `required`. A list of mappings between the source and destination. The specific properties are described below.                                                                                                                                                                                                                                         |
| label                                             | A label to give to this sync.                                                                                                                                                                                                                                                                                                                           |
| schedule\_frequency                               | <p>When this sync should be run. Valid options:</p><ul><li><code>never</code></li><li><code>continuous</code></li><li><code>quarter_hourly</code></li><li><code>hourly</code></li><li><code>daily</code></li><li><code>weekly</code></li><li><code>expression</code></li></ul>                                                                          |
| schedule\_day                                     | <p>What day of the week this sync should run. Valid options:</p><ul><li><code>Sunday</code></li><li><code>Monday</code></li><li><code>Tuesday</code></li><li><code>Wednesday</code></li><li><code>Thursday</code></li><li><code>Friday</code></li><li><code>Saturday</code></li></ul>                                                                   |
| schedule\_hour                                    | What hour of the day this sync should run. Valid values are integers between 0 and 24 inclusive.                                                                                                                                                                                                                                                        |
| schedule\_minute                                  | What minute of the hour this sync should run. Valid values are integers between 0 and 59 inclusive.                                                                                                                                                                                                                                                     |
| cron\_expression                                  | If `schedule_frequency` is `"expression"`, specify what cron schedule this sync should run on. Valid value is a string containing a cron expression, such as `"* 1 * * *"`.                                                                                                                                                                             |
| paused                                            | Whether or not this sync should be paused.                                                                                                                                                                                                                                                                                                              |
| triggers                                          |  Specify dbt Cloud job id and project id and/or Fivetran job id and job name to trigger Census syncs after dbt Cloud jobs and/or Fivetran syncs/transforms successfully complete. dbt Cloud project and job ids can be found in the URL when navigated to a job in the dbt Cloud application or via API. Fivetran job name can be found in the table of `Connectors` or `Transformations` via the Fivetran application and the job id can be found in the URL when navigated to the specific connector/transform details page. These information can also be retrieved via API.                                                                                                                                                                                                                                                                              |
| field\_behavior                                   | Specify `sync_all_properties` to configure this to automatically update mappings when the source changes.                                                                                                                                                                                                                                               |
| field\_normalization                              | <p>If <code>sync_all_properties</code> is specified, specify how you would like automatic mappings to be named. Valid options are:</p><ul><li><code>start_case</code></li><li><code>lower_case</code></li><li><code>upper_case</code></li><li><code>camel_case</code></li><li><code>snake_case</code></li><li><code>match_source_names</code></li></ul> |
| high\_water\_mark\_attributes                     | Attributes used to identify the sync type. Only valid for `append` operation and source warehouse `Snowflake`The specific properties are described below.                                                                                                                                                                                               |
| validate\_only                                    | When `true`, checks if the given payload is valid to configure a sync. Does not create the sync.                                                                                                                                                                                                                                                        |
| failed\_run\_notifications\_enabled               | When `true`, will email all workspace users with email notifications enabled and all workspace additional emails when the sync fails and recovers. Default is `true`.                                                                                                                                                                                   |
| failed\_record\_notifications\_enabled            | When `true`, will email all workspace users with email notifications enabled and all workspace additional emails when the sync has more than `failed_record_notifications_threshold_percent` rejected or invalid records in the source or destination. Default is `true`.                                                                               |
| failed\_record\_notifications\_threshold\_percent | The percentage of rejected and invalid records for which failed record emails will be triggered. Default is `75`. Accepts integer values between `0` and `100` (inclusive), where `0` will alert for any failed records.                                                                                                                                |

| Source Attribute    | Description                                                                                                                                                                                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| connection\_id      | `required`. The id used to identify the source connection.                                                                                                                                                                                      |
| filter\_segment\_id | `optional`. The id used to identify the segment data source. If specified, you must define the `object` property defined immediately below with values for the segment's underlying model. Ie, `"object": {"type": "model", "id": <model id>}`. |
| object              | `required`. Attributes of the data source. Properties are expanded on immediately below.                                                                                                                                                        |
| type                | <p><code>required</code>. The type of your data source. Valid options:</p><ul><li><code>table</code></li><li><code>model</code></li></ul>                                                                                                       |
| id                  | <p><code>required</code> unless either the following are specified:</p><ul><li><code>name</code></li><li><code>table_name</code>, <code>table_schema</code>, and <code>table_catalog</code></li></ul><p>The id of the data source.</p>          |
| name                | `required` if the `type` is `model`, and the `id` is not specified. The name of the model.                                                                                                                                                      |
| table\_name         | `required` if the `type` is `table`, and the `id` is not specified. The name of the table.                                                                                                                                                      |
| table\_schema       | `required` if the `type` is `table`, and the `id` is not specified. The schema of the table.                                                                                                                                                    |
| table\_catalog      | `required` if the `type` is `table`, and the `id` is not specified. The catalog of the table.                                                                                                                                                   |

| Destination Attribute   | Description                                                    |
| ----------------------- | -------------------------------------------------------------- |
| connection\_id          | `required`. The id used to identify the destination connection |
| object                  | `required`. The full name of the destination object            |
| lead\_union\_insert\_to | Where to insert a union object (for Salesforce connections)    |

| Mapping Attribute       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| from                    | <p><code>required</code>. An object with a <code>type</code> and <code>data</code> for the source.</p><p>For hardcoded (i.e. constant) values:</p><ul><li><code>type</code> should be <code>constant_value</code>.</li><li><code>data</code> is an object with two keys.<br>1. <code>basic_type</code> - The type of this value (can be <code>boolean</code>, <code>datetime</code>, <code>number</code>, or <code>text</code>).<br>2. <code>value</code> should be a constant value.</li></ul><p>For columns from your model or table:</p><ul><li><code>type</code> should be <code>column</code>.</li><li><code>data</code> is the name of the column.</li></ul> |
| to                      | `required`. The full name of the field to sync in to. When the mapping represents an append key, this should be set to `'unique_id'`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| is\_primary\_identifier | `required` to be `true` for exactly one mapping. Whether or not this mapping is the primary identifier for this sync.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| generate\_field         | Whether or not this mapping generates a custom field.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| preserve\_values        | Whether or not an existing destination value should be overwritten.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| operation               | For arrays, whether Census should `merge` or `overwrite` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| lookup\_object          | For a reference field, the full name of the object it refers to.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| lookup\_field           | For a reference field, the field to lookup the referenced object by.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

| High Water Mark Attribute          | Description                                                                                                                             |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| use\_high\_water\_mark\_diff\_type | `true` or `false` to indicate use of high water mark diff type sync. Only valid for `append` operation and source warehouse `Snowflake` |
| column\_name                       | The name of the column in the source                                                                                                    |

| Response Property | Description                                                     |
| ----------------- | --------------------------------------------------------------- |
| status            | `created` or `error` indicating whether the sync was triggered. |
| data              | Present if successful. An object containing the `sync_id`       |
| message           | Present if error. Contains message describing the error.        |

### PATCH /syncs/\[ID]

This endpoint updates a sync with the given ID.

{% tabs %}
{% tab title="Request" %}
```
curl --request PATCH 'https://app.getcensus.com/api/v1/syncs/[ID]' \
--header 'Authorization: Bearer [API_TOKEN]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "label": "Test Sync (edited via API)",
    "schedule_frequency": "daily",
    "triggers": {
        "dbt_cloud": {
            "project_id": "12345",
            "job_id": "123456"
        }
    },
    "mappings": [
        {
            "from": {
                "type": "column",
                "data": "hashed_email"
            },
            "to": "user_identifier.hashed_email_PREHASHED",
            "is_primary_identifier": true
        },
        {
            "from": {
                "type": "column",
                "data": "list_id"
            },
            "to": "list_id",
            "lookup_object": "user_list",
            "lookup_field": "name"
        },
        {
            "from": {
                "type": "constant_value",
                "data": {
                    "value": "cohort_1",
                    "basic_type": "text"
                }
            },
            "to": "cohort"
        }
    ]
}'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "status": "updated",
    "data": {
        "id": 61,
        "label": "Test Sync (edited via API)",
        "schedule_frequency": "daily",
        "schedule_day": null,
        "schedule_hour": 0,
        "schedule_minute": 0,
        "cron_expression": null,
        "created_at": "2021-10-22T00:40:11.246Z",
        "updated_at": "2021-10-22T00:43:44.173Z",
        "operation": "upsert",
        "paused": false,
        "status": "Ready",
        "lead_union_insert_to": null,
        "field_behavior": "specific_properties",
        "field_normalization": null,
        "failed_run_notifications_enabled": true,
	"failed_record_notifications_enabled": true,
	"failed_record_notifications_threshold_percent": 75
        "source_attributes": {
            "connection_id": 4,
            "object": {
                "type": "model",
                "id": 15,
                "name": "braze_test",
                "created_at": "2021-10-11T20:52:58.293Z",
                "updated_at": "2021-10-14T23:15:18.508Z",
                "query": "select cast('test@getcensus.com' as VARCHAR(2000)) as email, cast('random' as VARCHAR(2000)) as random_prop"
            }
        },
        "destination_attributes": {
            "connection_id": 15,
            "object": "user"
        },
        "mappings": [
            {
                "from": {
                    "type": "column",
                    "data": "hashed_email"
                },
                "to": "user_identifier.hashed_email_PREHASHED",
                "is_primary_identifier": true
                "generate_field": false,
                "preserve_values": false,
                "operation": null
            },
            {
                "from": {
                    "type": "column",
                    "data": "list_id"
                },
                "to": "list_id",
                "lookup_object": "user_list",
                "lookup_field": "name"
                "is_primary_identifier": false,
                "generate_field": false,
                "preserve_values": false,
                "operation": null
            },
            {
                "from": {
                    "type": "constant_value",
                    "data": {
                        "value": "cohort_1",
                        "basic_type": "text"
                    }
                },
                "to": "cohort",
                "is_primary_identifier": false,
                "generate_field": false,
                "preserve_values": false,
                "operation": null
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

| Request Property | Description                                                                                                                                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sync parameters  | A list of parameters to update the sync with, similar to the request parameters for `POST /syncs`. The only parameters that cannot be updated are `source_attributes`, `destination_attributes`, and `operation`. |

| Response Property | Description                                                         |
| ----------------- | ------------------------------------------------------------------- |
| status            | `updated` or `error` indicating whether the sync was updated.       |
| data              | Present if successful. Returns the same object as `GET /syncs/[ID]` |
| message           | Present if error. Contains message describing the error.            |

### DELETE /syncs/\[ID]

This endpoint deletes a sync with the given ID.

{% tabs %}
{% tab title="Request" %}
```
curl --request DELETE 'https://app.getcensus.com/api/v1/syncs/96' \
--header 'Authorization: Bearer [API_TOKEN]'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "status": "deleted"
}
```
{% endtab %}
{% endtabs %}

| Response Property | Description                                                           |
| ----------------- | --------------------------------------------------------------------- |
| status            | `deleted` or `404` indicating whether the sync was found and deleted. |

### POST /syncs/\[ID]/trigger

This endpoint triggers a specific sync to run.

{% tabs %}
{% tab title="Request" %}
```
curl -X POST 'https://app.getcensus.com/api/v1/syncs/[ID]/trigger' \
--header 'Authorization: Bearer [API_TOKEN]'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "status": "success",
    "data": {
        "sync_run_id": 1234567890
    }
}
```
{% endtab %}
{% endtabs %}

| URL Argument      | Description                                                                                                                                                                |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| force\_full\_sync | If this trigger request should be a Full Sync, add `force_full_sync=true` to the request URL. Note that some sync configurations such as Append do not support full syncs. |

| Response Property | Description                                                     |
| ----------------- | --------------------------------------------------------------- |
| status            | `success` or `error` indicating whether the sync was triggered. |
| data              | Present if successful. An object containing the `sync_run_id`   |
| message           | Present if error. Contains message describing the error.        |
