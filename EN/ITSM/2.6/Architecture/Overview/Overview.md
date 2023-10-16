# Operating environment

## Software Environment

| **Software Name** | **Version** | **Remarks** |
|--------------|----------|-------------------------------------|
| Mysql | 5.7 | The database version requires 5.6 or above, and it is recommended to upgrade to 5.7 |
| Python | 2.7.9 | Django1.8 |
| RabbitMQ | 3.1.10 | Enhanced services provided by the platform |
| NFS | | Individual deployment instances share files via NFS |
| Redis | 4.0 | Not required, helps improve performance |

## Hardware environment

<table>
     <tr>
         <th rowspan="2">Service/Module</th>
         <th colspan="7">Model</th>
     </tr>
     <tr>
         <th>CPU</th>
         <th>memory</th>
         <th>storage</th>
         <th>network card</th>
         <th>Operating System</th>
         <th>Quantity</th>
         <th>Remarks</th>
     </tr>
     <tr>
         <td>AppServer</td>
         <td>8C</td>
         <td>16G</td>
         <td>1T</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>>1</td>
         <td>Multi-machine deployment requires additional configuration of NFS services</td>
     </tr>
</table>

# System functions

| **Process Name** | **Deployment Server** | **Function** |
|----------------|---------------|--------------------------------|
| **WebServer** | AppServer | Handle all front-end requests and page rendering of users |
| **TaskServer** | AppServer | Responsible for executing process scheduling, sending notifications and other asynchronous tasks|
| **APIServer** | AppServer | Provide HTTP interface |