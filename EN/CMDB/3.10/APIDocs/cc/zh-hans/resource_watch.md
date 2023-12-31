
### Request method

POST


### request address

/api/c/compapi/v2/cc/resource_watch/


### General parameters

| Field | Type | Required | Description |
|-----------|------------|--------|------------|
| bk_app_code | string | yes | application ID |
| bk_app_secret| string | Yes | The security key (application TOKEN), which can be obtained through the BlueKing Zhiyun Developer Center -> click on the application ID -> basic information |
| bk_token | string | No | Current user login status, bk_token and bk_username must be valid, bk_token can be obtained through Cookie |
| bk_username | string | No | Username of the current user, which is an application in the whitelist of the application-free login authentication, use this field to specify the current user |


### Function Description

Listen to events generated by system resource changes (v3.8 and above)


**Key features of the watch function include:**


* Provide users with a highly available data change watch service for a limited time (currently 3 hours, it may be adjusted, please do not rely on this time).


* Within a limited time, users can perform event backtracking or data tracking according to the cursor of their last event, which is suitable for abnormal data backtracking, or data supplementary recording for system changes.


* Supports backtracking of changed data based on time points, backtracking of changed data based on cursors, and data change watch from the current point in time.


* Supports the ability to watch according to event types, including addition, deletion, and modification. Events contain the full amount of data.


* Support the event watch capability of host-to-host relationship data changes.


* Adopt the design of short and long chains. When the user performs event watch through the cursor, if there is no event, the session connection will be kept, and if there is an event change within 20s, the event will be pushed back directly. Avoid continuous requests from users, and at the same time ensure that users can get changed data in a timely manner.


* Support batch event watch capability to improve system throughput.


* Support customizing the event data fields of interest to meet users' lightweight watch needs.


### Request parameters



#### Interface parameters

| Field | Type | Required | Description |
| ------------------- | -------------- | ------ | --------------------------------------------------------- |
| bk_event_types | array string | No | Event type, if filled, it means only pay attention to this type of event. The optional values are: create (new)/update (update)/delete (delete). For example, if you use create, you only pay attention to the new events of this resource. If you don't fill in the blank, you will pay attention to all. |
| bk_fields | array string | Depends | The list of fields that need to be returned in the returned event. Currently, this field is required for monitoring host resources and cannot be left blank. The host relationship can be left blank. Leave blank to return all fields by default. |
| bk_start_from | Int64 | No | The start time of monitoring events, the value is the number of seconds in unix time, that is, the total number of seconds from 0:00:00 on January 1, 1970 UTC to the time point you want to watch . |
| bk_cursor | string | No | The cursor for event monitoring, which represents the event address to start or continue watching (monitoring), and the system will return the next event or a batch of events of this cursor. |
| bk_resource | string | Yes | The resource type to be monitored, the enumeration values are: host, host_relation, biz, set, module, process, object_instance, mainline_instance, biz_set, biz_set_relation. Among them, host represents the host detailed event, host_relation represents the host relationship event, biz represents the business detailed event, set represents the cluster detailed event, module represents the module detailed event, process represents the process detailed event, object_instance represents the general model instance event, and mainline_instance represents the mainline model instance Event, biz_set represents business set event, biz_set_relation represents the relationship event between business set and business. |
| bk_supplier_account | string | yes | supplier account |
| bk_filter | object | no | filter condition |

**Note: The biz_set_relation event will be triggered when adding, deleting, and updating the "bk_scope" field of a business set and when adding, deleting, and updating a business involve changes in the relationship of a business set. The event type (bk_event_type) of all business set relationship events is update type, and the event details will return the ID of the business set whose relationship has changed and a list of all business IDs contained in the business set. When the event is triggered by a business set delete event, the business ID list in the returned event details is empty**

#### bk_filter

| Field | Type | Required | Description |
| ------------------- | -------------- | ------ | --- |
| bk_sub_resource | string | No | The sub-resource type to be monitored, only supported when bk_resource is object_instance or mainline_instance, representing the bk_obj_id of the model to be monitored |


### Request parameter example

Host:

```json
{
    "bk_app_code": "esb_test",
    "bk_app_secret": "xxx",
    "bk_username": "xxx",
    "bk_token": "xxx",
    "bk_event_types": ["create","update","delete"],
    "bk_fields": ["bk_host_innerip", "bk_mac"],
    "bk_start_from": 12345678999,
    "bk_cursor": "MQ0yDTE1ODkyMDcyODENMQ01ZWI3ZWZjNTBiOTA5ZTYyMGFmYWQzZGY=",
    "bk_resource": "host"
}

```

Generic model instance:

```json
{
    "bk_event_types": [],
    "bk_fields": ["bk_inst_id", "bk_inst_name"],
    "bk_start_from": 12345678999,
    "bk_cursor": "MQ0yDTE1ODkyMDcyODENMQ01ZWI3ZWZjNTBiOTA5ZTYyMGFmYWQzZGY=",
    "bk_resource": "object_instance",
    "bk_filter": {
        "bk_sub_resource": "xxx"
    },
    "bk_supplier_account": "0"
}

```

## return parameter

```json
{
    "result": true,
    "code": 0,
    "message": "success",
    "permission": null,
    "request_id": "e43da4ef221746868dc4c837d36f3807",
    "data": {
        "bk_watched": true,
        "bk_events": [
            {
                "bk_cursor": "MQ0yDTE1ODkyMDcyODENMQ01ZWI3ZWZjNTBiOTA5ZTYyMGFmYWQzZGY=",
                "bk_resource": "host",
                "bk_event_type": "update",
                "bk_detail": {
                    "bk_cpu": 2
                }
            },
            {
                "bk_cursor": "MQ0yDTE1ODkzNDExMDcNMQ01ZWI3ZWZjNTBiOTA5ZTYyMGFmYWQzZGY=",
                "bk_resource": "host",
                "bk_event_type": "update",
                "bk_detail": {
                    "bk_cpu": 2
                }
            }
        ]
    }
}

```

### Return result parameter description

#### response

| Name | Type | Description |
|---|---|---|
| result | bool | Whether the request was successful or not. true: the request succeeded; false the request failed |
| code | int | Error code. 0 means success, >0 means failure error |
| message | string | The error message returned by the request failure |
| permission | object | permission information |
| request_id | string | request chain id |
| data | Array | Event data details, which is an ordered array, and the event at the end of the array is a new event. |

- data data description

| Name | Type | Description |
| ---------- | ---------------- | -------------------- |
| bk_watched | bool | Whether the event has been watched, true: the event has been watched; false: the event has not been watched |
| bk_events | Details of monitored events | The list of detailed events monitored, the maximum length is 200, it may be adjusted later, please do not rely on this length. |

- bk_events data description

| Name | Type | Description |
| ------------- | ----------- | ---------------------------------------------------------- |
| bk_cursor | string | represents the cursor value of the current resource event, the caller can use this cursor to get the next event after this event |
| bk_resource | enum string | resource type corresponding to this event |
| bk_event_type | enum string | The event type corresponding to this event, the enumeration value is: create (new)/update (update)/delete (delete). |
| bk_detail | object | The detailed data of the resource corresponding to the event. Different resources have different corresponding details. |

#### host_relation resource bk_detail field data example
```json

{
	"bk_biz_id" : 1,
	"bk_host_id" : 2,
	"bk_module_id" : 3,
	"bk_set_id" : 4,
	"bk_supplier_account" : "0"
}
```

#### host resource bk_detail field data example
```json
{
	"bk_host_name" : "hostname",
	"bk_mem" : null,
	"bk_cloud_id" : 0,
	"operator" : "user",
	"bk_cpu" : null,
	"bk_mac" : "",
	"bk_host_innerip" : "10.0.0.1",	
        "bk_supplier_account" : "0",
	....
}
```

#### biz_set_relation resource bk_detail field data example
```json
{
	"bk_biz_set_id": 1,
	"bk_biz_ids": [1 ,2, 3]
}
```

- biz_set_relation resource bk_detail data description

| Name | Type | Description |
| ------------- | --------- | ----------------------------- |
| bk_biz_set_id | int | The ID of the business set whose relationship between the business set and the business has changed |
| bk_biz_ids | int array | ID list of all businesses included in this business set |


### Instructions for use

The process of using this interface:

1. Determine the initial monitoring method, which can be:

- 1.1 Specify to start listening to events from a certain time

- 1.2 Specify the current time to start listening to events

- 1.3 Specify to use the cursor bk_cursor position to start listening to events

   After confirming, initiate a request.

2. cmdb returns a list of events that meet your expectations:
    - 2.1: If bk_watched is true, it means that the event has been monitored, bk_events is a list of event details, the caller can get the cursor of the last event in the array, and proceed to the next watch with the method in step 1.3.
    - 2.2: If bk_watched is false, it means that no event has been monitored, and there is only one event in bk_events, and the cursor of this event is used for the next watch.

**Notice**:

The event has an expiration time, which is currently 3 hours. If it expires, the event will be released, and the expired cursor will also become invalid. The watch can be restarted in two ways:

1. Specify to start listening to events from a certain time
2. Specify the current time to start listening to events