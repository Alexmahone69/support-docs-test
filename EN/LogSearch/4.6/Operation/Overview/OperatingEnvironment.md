# Operating environment
## Software Environment

|Software name|Version|Remarks|
|--|--|--|
| Linux OS | 2.6+ | Operating system, indicating that the kernel version is not lower than 2.6, the distribution version (Ubuntu or Centos or suse) is not important. |
| Kafka | 0.10.0.1 | Apache open source message queue service, the data bus is implemented using Kafka ecological facilities |
| MySQL | 5.5 | The entire backend uses MySQL as the configuration library and to store user data |
| ElasticSearch | 5.4 | Log Service uses ElasticSearch as the main storage |

## Hardware environment

<table>
     <tr>
         <th rowspan="2">Service/Module</th>
         <th colspan="7">Model</th>
     </tr>
     <tr>
         <th>CPU</th>
         <th>Memory</th>
         <th>Storage</th>
         <th>Network card</th>
         <th>Operating System</th>
         <th>Quantity</th>
         <th>Remarks</th>
     </tr>
     <tr>
         <td>Bklog-api module</td>
         <td>8C</td>
         <td>16G</td>
         <td>100G</td>
         <td>Gigabit/Ten Gigabit</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td></td>
     </tr>
     <tr>
         <td>Kafka service</td>
         <td>8C</td>
         <td>16G</td>
         <td>1T</td>
         <td>Gigabit/Ten Gigabit</td>
         <td>centos 7/X86_64</td>
         <td>2</td>
         <td></td>
     </tr>
     <tr>
         <td>ElasticSearch Service</td>
         <td>12C</td>
         <td>32G</td>
         <td>4*2TB</td>
         <td>Gigabit/Ten Gigabit</td>
         <td>centos 7/X86_64</td>
         <td>3</td>
         <td></td>
     </tr>
</table>