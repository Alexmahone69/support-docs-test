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
         <td>Stand-alone operating platform</td>
         <td>JOB operation platform single instance RabbitMQ,MYSQL</td>
         <td>1</td>
         <td>Do not build NFS, only use local hard disk as storage</td>
     </tr>
     <tr>
         <td rowspan="5">Option 2</td>
         <td rowspan="5">High availability operating platform</td>
         <td rowspan="5">JOB job platform enables mirroring dual-node RabbitMQ<br>FS reliable storage and high<br>Available MySQL</td>
         <td>2</td>
         <td>Start JOB on both machines</td>
     </tr>
     <tr>
         <td rowspan="2">2</td>
         <td>FS storage service should be redundant</td>
     </tr>
     <tr>
         <td>MQ service starts on two servers each</td>
     </tr>
     <tr>
         <td rowspan="2">2</td>
         <td>Master/Slave MySQL</td>
     </tr>
     <tr>
         <td>Or solve it with MySQL middleware products</td>
     </tr>
</table>