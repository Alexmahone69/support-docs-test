 # Install step 

 ## Initializing Working Directory 

 ## Create a Public Directory 

 create a public directory on the service. 

 `${BK_HOME}/cmdb` 

 ## Decompressing CMDB_ee-x.x.x.tgz 

 Go to the `${BK_HOME}/CMDB` directory and extract the install package. 

 ## Install supervisord 

 Omitted, specifically in the BK Enterprise Edtion public Components will provided 

 ##Revise setting file 

 Revise the setting file in the directory `${BK_HOME}/CMDB/support-files/templates` according to the external service you depend on. Place `supervisor-cmdb-server.conf` under `{BK_HOME}/etc`, and files prefixed with server#conf#* under `${BK_HOME}/cmdb/server/conf` 

 ## Start Up CMDB service 

 execute the command as follows: 
 - Start Up the CMDB service with the supervisor: `supervisord -c ${BK_HOME}/etc/supervisor-cmdb-server.conf` 
 - Check that the 12 CMDB processes have Start Up 
 - Initialize Database: Request `{server_ip:port}/migrate/v3/migrate/enterprise/0` 
 - Open the browser Confirm that the page is Display normal 