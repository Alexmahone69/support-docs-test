# Operating environment
## Software Environment

| **Software Name** | **Version** | **Remarks** |
|--------------|----------|---------------------------------------------------------------------|
| Linux OS | 2.6+ | Operating system, specify that the kernel version is not lower than 2.6, the distribution (Ubuntu or Centos or SUSE) does not matter|
| JDK | 1.8 | Virtual machine, the operating platform is a service program running on Java, which requires jdk1.8 support |
| RabbitMQ | 3.3+ | A message queuing service provided by an integrated platform |
| Redis | 2.8.19 | Job Platform Distributed Cache |
| Mysql | 5.5 | Job Platform Data Master Storage Database |

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
         <td>JOB job platform background server</td>
         <td>12C</td>
         <td>32G</td>
         <td>500M</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>3+</td>
         <td>JOB service program under deployment operation platform</td>
     </tr>
     <tr>
         <td>NFS job execution log and file upload storage server</td>
         <td>8C</td>
         <td>16G</td>
         <td>1T</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td>The two are used as a high-availability solution for mutual NFS. Enterprises can also use their own other storage solutions, not necessarily NFS. </td>
     </tr>
     <tr>
         <td>RabbitMQ</td>
         <td>4C</td>
         <td>8G</td>
         <td>100M</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td>RabbitMQ mirror mode deployment</td>
     </tr>
<tr>
         <td>Redis</td>
         <td>4C</td>
         <td>16G</td>
         <td>100M</td>
         <td>K/10G</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td>Redis sentinel deployment mode</td>
     </tr>
</table>

- Note: RabbitMQ/Redis is recommended to be deployed separately from microservices