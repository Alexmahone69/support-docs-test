# System functions

| process name | deployment server | function |
| -- | -- | -- |
| WebServer | Deployment server | Handle all front-end requests and page rendering of users, display process templates, task records, business configuration, etc. |
| TaskServer | Deployment server | Responsible for maintaining task queues and assigning tasks to celery workers according to priority |
| APIServer | Deployment Server | Provides HTTP API|
| Mysql | Deployment server | Database, persistent storage system data|