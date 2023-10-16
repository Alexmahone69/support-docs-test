 # Service layer 

 The service layer is divided into two modules: Resource Management Module and Business Name Scene Module. 

 ## Resource Management Module 

 In the CMDB, we abstract the resource type, which is currently divided into three categories: Host, Process and General Object, which supports horizontal expansion. Each type of resource is managed by a type of service process. 

 ## Business Name Scenario Module 

 The Business Name Scenario module encapsulates the Apply scenario based on the atomic interface of the Resource Management module. Based on the relevance of the operation, the Business Scenario module is divided into several services [admin, event, host, topo, process, datacollection]. The admin service is responsible for reflashing system settings, writing initialization data, and other operations; the event service is responsible for the system event subscription and push services; process, topo, and host are responsible for the system process usage scene, topology model, and host data, respectively; the data collection service is responsible for receiving and writing system snapshot data. 