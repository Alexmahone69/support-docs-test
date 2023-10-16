 # Operating environment 
 ## Software environment 

 | **version**|**remark**|**remark**                                                                    | 
 |----------|----------------------------------------------------------------------------|----------------------------------------------------------------------------| 
| Linux OS | 2.6+ | Operating system, specify that the kernel version is not lower than 2.6, the distribution (Ubuntu or Centos or SUSE) does not matter|
  | JDK | 1.8 | Virtual machine, the operating platform is a service program running on Java, which requires jdk1.8 support |
  | RabbitMQ | 3.3+ | A message queuing service provided by an integrated platform |
  | Redis | 2.8.19 | Job Platform Distributed Cache |
  | Mysql | 5.5 | Job Platform Data Master Storage Database |

 ## Hardware environment 

 <table> 
    <tr> 
        <th rowspan="2">service/module</th> 
        <th colspan="7">model</th> 
    </tr> 
    <tr> 
        <th>CPU</th> 
        <th>Memory</th> 
        <th>Storage</th> 
        <th>Network card</th> 
        <th>The operating system</th> 
        <th>Quantity</th> 
        <th>remark</th> 
    </tr> 
    <tr> 
        <td>Job System background service</td> 
        <td>12C</td> 
        <td>32G</td> 
        <td>500M</td> 
        <td>Kilo/terabyte</td> 
        <td>centos 7/X86_64</td> 
        <td>3+</td> 
        <td>JOB Service program unde Deploy Job System</td> 
    </tr> 
    <tr> 
        <td>NFS job Execution Log and File Upload Storage service</td> 
        <td>8C</td> 
        <td>16G</td> 
        <td>1T</td> 
        <td>Kilo/terabyte</td> 
        <td>centos 7/X86_64</td> 
        <td>2</td> 
        <td>As a high-availability solution for mutual NFS, enterprises can also use their own Other Storage solutions, not necessarily NFS.  </td> 
    </tr> 
    <tr> 
        <td>RabbitMQ</td> 
        <td>4C</td> 
        <td>8G</td> 
        <td>100M</td> 
        <td>Kilo/terabyte</td> 
        <td>centos 7/X86_64</td> 
        <td>2</td> 
        <td>RabbitMQ mirror mode Deploy</td> 
    </tr> 
	    <tr> 
        <td>Redis</td> 
        <td>4C</td> 
        <td>16G</td> 
        <td>100M</td> 
        <td>Kilo/terabyte</td> 
        <td>centos 7/X86_64</td> 
        <td>2</td> 
        <td>Redis sentinel Deploy model</td> 
    </tr> 
 </table> 

 - RabbitMQ/Redis is recommended to be Deploy separately from service 