# Deployment directory description
## General directory
```bash
|- /data/bkee # BlueKing root directory
   |- job # job deployment program directory
   |- etc # BlueKing configuration file general directory
     |- job # job configuration file directory
```

## Program directory
```bash
|- /data/bkee/job # program main directory
   |- frontend # Stored static resource directory published by the front end
   |- backend # Backend service storage directory
     |- job-manage
       |- job-manage.sh # job-manage microservice startup and shutdown script
       |- boot-job-manage.jar # SpringBoot.jar for job-manage microservices
     |- job-config
       |- job-config.sh # job-config microservice start and stop script
       |- boot-job-config.jar # SpringBoot.jar for job-config microservices
     ...
```
## Configuration file directory
```bash
|- /data/bkee/etc # General directory of BlueKing configuration files
   |- job # job configuration file directory
     |- job-manage # job-manage service configuration directory
       |- job-manage.properties
...
```

# Log

- Base directory: `${BK_HOME}/logs/job/${SERVICE_NAME}`

    - ${SERVICE_NAME}.log: background program log. Named as: microservice name.log, such as manage.log, execute.log, logsvr.log

    - esb_job.log: ESB API request log
   
    - esb_client.log: Job calls the third-party system request log through ESB

    - error.log: error log