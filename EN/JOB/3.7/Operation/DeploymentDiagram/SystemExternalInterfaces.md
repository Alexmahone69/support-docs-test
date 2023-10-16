# System external interface

<table>
     <tr>
         <th rowspan="2">System interface</th>
         <th colspan="2">Communication protocol</th>
         <th rowspan="2">Communication frequency (times/minute)</th>
         <th rowspan="2">Remarks</th>
     </tr>
     <tr>
         <th>TCP/UDP/Other</th>
         <th>Standard/Custom</th>
     </tr>
<tr>
         <td>Query the details of the job execution plan according to the job execution plan ID</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_job_detail</td>
     </tr>
<tr>
         <td>Query the list of job execution plans</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_job_list</td>
     </tr>
<tr>
         <td>Query business script list</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_script_list</td>
     </tr>
<tr>
         <td>Query public script list</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_public_script_list</td>
     </tr>
<tr>
         <td>Query script details</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_script_detail</td>
     </tr>
<tr>
         <td>Query the execution account under the business</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_os_account</td>
     </tr>
<tr>
         <td>Query the list of DB accounts that the user has permission</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_own_db_account_list</td>
     </tr>
     <tr>
         <td>Execute scripts quickly</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>fast_execute_script</td>
     </tr>
     <tr>
         <td>Quickly distribute files</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>fast_push_file</td>
     </tr>
     <tr>
         <td>Execute SQL quickly</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>fast_execute_sql</td>
     </tr>
     <tr>
         <td>Start job interface</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>execute_job</td>
     </tr>
     <tr>
         <td>Job instance operations</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>operate_job_instance</td>
     </tr>
<tr>
         <td>Job step instance operation</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>operate_step_instance</td>
     </tr>
<tr>
         <td>Query the job execution log according to the job instance ID</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_job_instance_log</td>
     </tr>
     <tr>
         <td>Query the job execution status according to the job instance ID</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_job_instance_status</td>
     </tr>
<tr>
         <td>Query the scheduled job information under the business</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>get_cron_list</td>
     </tr>
     <tr>
         <td>Modify scheduled job status</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>change_cron_status</td>
     </tr>
     <tr>
         <td>Create or update a scheduled task</td>
         <td>TCP</td>
         <td>Standard (HTTP)</td>
         <td></td>
         <td>save_cron</td>
     </tr>
</table>