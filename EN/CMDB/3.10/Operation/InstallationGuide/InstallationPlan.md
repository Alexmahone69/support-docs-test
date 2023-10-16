# Installation scheme

<table>
     <tr>
         <th>serial number</th>
         <th>User needs</th>
         <th>Deployment module</th>
         <th>number of machines</th>
         <th>Recommended deployment scheme</th>
     </tr>
     <tr>
         <td>Option 1</td>
         <td>Stand-alone configuration platform</td>
         <td>Configuration Platform<br>MongoDB<br>Zookeeper<br>Redis</td>
         <td>1</td>
         <td>All services are built on one machine</td>
     </tr>
     <tr>
         <td rowspan="4">Option 2</td>
         <td rowspan="4">High availability configuration platform</td>
         <td>CMDB Configuration Platform</td>
         <td>2</td>
         <td>Start CMDB on both machines</td>
     </tr>
     <tr>
         <td>High availability redis</td>
         <td>3</td>
         <td>Redis cluster service</td>
     </tr>
     <tr>
         <td>High availability zookeeper</td>
         <td>3</td>
         <td>Zookeeper Cluster</td>
     </tr>
     <tr>
         <td>High availability MongoDB</td>
         <td>2</td>
         <td>MongoDB Cluster</td>
     </tr>
</table>