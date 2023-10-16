 # Interface layer (api) 

 A layer is the api service gateway of the system. 

 ## Web layer (web) 

 The web tier is a web service provided by the system. approve configuration of the web service interface provided by the platform, the user can operate the resources. 

 With the service discovery function of the system service, based on Zookeeper node monitoring mechanism, we build the service registration and discovery function of the system, so that the system can maintain high availability. 

 To avoid the problem of configuration file management in service deployment, we build the configuration center service of the system based on zookeeper. all configuration files are brushed into zookeeper approve admin server at the beginning of system startup. Each process only needs to fetch the configuration file it needs from zookeeper. The existence of these two modules ensures high availability of the system and ease of use of the service. 