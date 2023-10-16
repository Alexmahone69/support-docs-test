# Overview of data migration content

**Migration Overview**:

1. Versions 3.x and 4.x cannot coexist. You can upgrade on the interface after deploying version 4.x.
2. Migration operation entrance: Management -> V3 migration, you can migrate configuration and data as needed


## Migration instructions
1. Please confirm the collection items that need to be upgraded, and select the data classification corresponding to the collection items. After confirming that they are correct, click batch upgrade;
2. If you do not need to retain historical data, please check [Current data can be discarded, skip the data confirmation step and migrate directly]. The platform will be used normally after the configuration is migrated.
3. If you need to retain historical data, please ensure that the old and new collection items are in the same ES cluster. After the collection items are migrated, the platform will maintain the collection of two copies of data at the same time. Please confirm the effective dates of the newly collected items during the data confirmation stage. After confirmation, the platform will stop the old collected items and migrate the data.
  - It is recommended to maintain at least two days of collection at the same time to ensure that there is a complete day's log to compare the old and new collection items.
  - For the migrated historical data, the platform will add an index alias and modify the mapping to be compatible with the new version.
4. For the cleaning of historical data, the databus service can be retained for regular cleaning, or it can be manually cleaned according to the index rules.


# Upgrade migration details

## 1. Upgraded content

### 1. Collection items

1. When entering the page for the first time, a forced upgrade is required, based on business units.
2. On the upgrade page, the collection items to be upgraded are displayed.
3. Click "Upgrade" to create new collection items

### 2. Data migration

1. Premise: The new and old INDEX are in the same ES cluster

2. Physical index
    V3(ES-INDEX)2_result_table_20200210

    V4(ES-INDEX)2_bklog_result_table_20200211

3. Migration method
    Add an alias 2_bklog_result_table_20200210 to 2_result_table_2020021001

4. API access
    Request time: 20200210 -> 20200211

    The requested INDEX accesses both the old and new data:
    2_bklog_result_table_20200210*, 2_bklog_result_table_20200211*

### 3. Monitoring strategy


## 2. Upgrade steps

The following is a discussion of a single collection item

### 1. Upgrade collection items

- process

   1. Execute according to "Collection Item Migration Details"
   2. Perform deployment and delivery operations
   3. Read the bk_biz_id and dataid corresponding to the collection item from the log retrieval collection item record table, and obtain the collection item configuration from the data platform, call the V4 interface to create the collection item and store it in the database directly.
      2. V3 data table: bk_log_search.home_application_bizdataid
      2. V3 collection item information: /o/bk_log_search/config/get_deploy_plan_data/?&raw_data_id={data_id}&bk_biz_id={bk_biz_id}

- Problems

   - Data classification needs to be determined

   - Whether automatic deployment is required, nodeman performance pressure needs to be considered

     

### 2. Migrate historical data

- Premise

   - The new and old indexes must be in the same ES cluster

- process

   - Read the bk_biz_id and dataid corresponding to the collection item from the log retrieval collection item record table, obtain the collection item configuration information from the data platform, and add an alias to the ES index to which each dataid belongs (the information is consistent with the collection item configuration)

   1. Pull the index list
   2. Add an alias to the corresponding index
   3. Smooth upgrade: If you need to seamlessly migrate historical data, it is recommended to perform it the next day and delete the newly added index of the V4 link to avoid data duplication (you can delete the index of V4 duplicate data through the ES HTTP REST API)

### 3. Monitoring policy migration

- Premise

   - Monitoring V3.2 deployed
- process
   1. Pull and monitor the policy list under the current business of the old version

   2. Filter the policy configuration of the current collection items based on result_table_id

   3. Call the monitoring new version policy interface to create a new monitoring policy (the conversion of the old and new policy fields will be added)

### 4. Old collection items are deactivated

- Call the data platform interface to remove the configuration of the current collection item IP

  

## 3. Collection item migration details

- name
   - Chinese name
- instruction manual
   - Data source description
- Log type
   - line log file
- Data Classification - ?
   -Other-Other
- Collect targets
   - Although the mixed use of dynamic and static is supported on the interface, it is not supported in the background.
   - If mixed, an error will be reported
- Log path
   - Windows and Linux paths are merged directly
- Filter content
   - Delimiter filtering
- Field extraction
   - close
- Storage
   - Cluster - Inheritance
   - Index name - 2_bklog_original data source name
   - Expiration time - inheritance
- View permissions
   - Create users as new groups and reuse them based on MD5