 # System availability/sustainability 

 **Machine disaster recovery**: 
 The Job System is based on the Service architecture, and the service Deploy on multiple servers. The single Node outage does not affect the service. 

 **Message queue**: 
 Due to the dual-machine Deploy, the Message queue RabbitMQ queue adopts the mirror mode, and the two nodes are the master and slave of each other. The Data received by the two nodes will be synchronized with each other to ensure data redundancy and consistency. 
 In addition, Node (at least 2 nodes) are setting on the Job System to connect any node. When a node fails, the job platform will auto switch to another node to ensure high availability. 

 **Job Redo after Process restore**: 
 When One JOB Job System service hangs up, the Unfinished job that logout abnormal last time will be restore after Start Up. 