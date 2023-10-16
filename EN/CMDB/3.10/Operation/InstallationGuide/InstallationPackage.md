# Installation package

Installation package name: cmdb_ee-x.x.x.tgz

```bash
+--- errors ---- error code language pack
+--- server
| +--- bin ---- cmdb binary
| +--- conf ---- cmdb configuration file
+--- support-files
| +--- templates ---- configuration file templates
| | +--- #etc#admin.conf
| | +--- #etc#nginx#cmdb.conf
| | +--- #etc#nginx.conf
| | +--- #etc#supervisor-cmdb-server.conf
| | +--- server#conf#apiserver.conf
| | +--- server#conf#auditcontroller.conf
| | +--- server#conf#datacollection.conf
| | +--- server#conf#eventserver.conf
| | +--- server#conf#host.conf
| | +--- server#conf#hostcontroller.conf
| | +--- server#conf#migrate.conf
| | +--- server#conf#objectcontroller.conf
| | +--- server#conf#proc.conf
| | +--- server#conf#proccontroller.conf
| | +--- server#conf#topo.conf
| | +--- server#conf#webserver.conf
+--- VERSION ---- Installation package version information file
+--- web ---- Frontend UI files
```