# Installation package

- document

job_ee-x.x.x.tgz

- File directory structure and function description

```bash
|- job_ee-1.0.0.tgz # package root directory
   |- job_ee-1.0.0.tar
     |- job # job program root directory
       |- backend # Backend program storage directory
         |- job-manage
           |- bin
             |- job-manage.sh # job-manage microservice startup and shutdown script
           |- job-manage.jar #job-manage SpringBoot.jar for microservices
         |- job-config
           |- bin
             |- job-config.sh # job-config microservice start and stop script
           |- job-config.jar #job-config SpringBoot.jar for microservices
         ...
       |- frontend # front-end program storage directory
         |- static # Front-end static file directory
         |- index.html # front-end page entry
       |- support-files
         |- sql # db upgrade script
           |- 0001_job_ee_20200101-1000_mysql.sql
         |- iam # permission access upgrade script
           |- 0001_bk_job_20190624-0000_iam.json
         |- templates # Templates that need to be deployed for rendering
           |- #etc#job#application-config.yml
           |- #etc#job#application-gateway.yml
           |- #etc#job#application-manage.yml
           |- #etc#job#application-execute.yml
           |- #etc#job#application-crontab.yml
           |- #etc#job#application-logsvr.yml
           |- #etc#job-config#job-config.properties
           |- #etc#job-gateway#job-gateway.properties
           |- #etc#job-manage#job-manage.properties
           |- #etc#job-crontab#job-crontab.properties
           |- #etc#job-execute#job-execute.properties
           |- #etc#job-logsvr#job-logsvr.properties
       |- projects.yaml # project description file
       |- README.md # job overview
       |- release.md # change history (view in background)
       |- VERSION # version number
     ...
```