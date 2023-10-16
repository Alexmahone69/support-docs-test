# System functions

|Process Name|Deployment Server|Function|
|--|--|--|
|Redis|Database server|Data buffer service, reducing the pressure of direct access to the database|
|MongoDB|Database Server|Database. Store data used in provisioning platforms |
|Zookeeper|Database Server|Service Discovery, Configuration Discovery, Language Pack Discovery|
|cmdb_webserver|backend server|handles web and frontend file requests|
|cmdb_apiserver|backend server|api web. Distribute requests to other processes for processing|
|cmdb_adminserver|Backend server|Process configuration platform initialization tasks|
|cmdb_eventserver|backend server|provides event subscription and push services|
|cmdb_hostserver|backend server|provides host-related services|
|cmdb_procserver|backend server|provides process-related services|
|cmdb_toposerver|backend server|provides topology-related services|
|cmdb_datacollection|Backend server|Collect real-time data of host|
|cmdb_auditcontroller|backend server|provides audit related services|
|cmdb_hostcontroller|backend server|provides host-related atomic services|
|cmdb_objectcontroller|backend server|provides object-related atomic services|
|cmdb_proccontroller|backend server|provides process-related atomic services|