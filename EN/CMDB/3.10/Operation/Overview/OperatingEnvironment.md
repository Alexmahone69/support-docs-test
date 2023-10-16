# Operating environment
## Software Environment

| Software Name | Version | Remarks |
|------------|--------|---------------|
| Linux | 2.6+ | Operating system, indicating that the kernel version is not lower than 2.6, and the distribution (Ubuntu or Centos or suse) does not matter. |
| Zookeeper | 3.4.11 | Service Discovery, Configuration Discovery |
| Redis | 3.2.11 | Configure platform cache, save session |
| MongoDB | 2.8.0 | Configure Platform Database |
| Redis | 1.4.4 | Configure platform data, session storage |
| Supervisor | 3.3.1 | Process hosting |

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
         <td>BlueKing configuration platform server</td>
         <td>8C</td>
         <td>16G</td>
         <td>500G</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td>Deployment configuration platform web, api, cli services</td>
     </tr>
     <tr>
         <td>Redis</td>
         <td>8C</td>
         <td>64G</td>
         <td>500G</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>3</td>
         <td>Three sets build a redis cluster</td>
     </tr>
     <tr>
         <td>MongoDB</td>
         <td>4C</td>
         <td>8G</td>
         <td>1T</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td>MongoDB master and slave service construction</td>
     </tr>
     <tr>
         <td>Zookeeper</td>
         <td>4C</td>
         <td>8G</td>
         <td>500G</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>3</td>
         <td>Zookeeper Cluster</td>
     </tr>
</table>