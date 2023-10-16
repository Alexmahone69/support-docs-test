 # System external interface 

 <table> 
    <tr> 
        <th rowspan="2">system interface</th> 
        <th colspan="2">communication protocol</th> 
        <th rowspan="2">Communication frequency (times/min)</th> 
        <th rowspan="2">remark</th> 
    </tr> 
    <tr> 
        <th>TCP/UDP/Other</th> 
        <th>standard/customize</th> 
    </tr> 
	 <tr> 
        <td>Inquire the details of the job execution scheme according to the ID of the Job Plan</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_job_detail</td> 
    </tr> 
	 <tr> 
        <td>Inquire Job Plan List</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_job_list</td> 
    </tr> 
	 <tr> 
        <td>Inquire Business Name Script List</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_script_list</td> 
    </tr> 
	 <tr> 
        <td>Inquire Public Script List</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_public_script_list</td> 
    </tr> 
	 <tr> 
        <td>Inquire Script detail</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_script_detail</td> 
    </tr> 
	 <tr> 
        <td>Inquire the execute Account under the Business Name</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_os_account</td> 
    </tr> 
	 <tr> 
        <td>This API is used to Query the list of database Account for which the user has auth.</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_own_db_account_list</td> 
    </tr> 
    <tr> 
        <td>Quick Script execute</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>fast_execute_script</td> 
    </tr> 
    <tr> 
        <td>Expedited distribution of file</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>fast_push_file</td> 
    </tr> 
    <tr> 
        <td>Quick SQL Execution</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>fast_execute_sql</td> 
    </tr> 
    <tr> 
        <td>Start Up Job Interface</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>execute_job</td> 
    </tr> 
    <tr> 
        <td>job instance Operation</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>operate_job_instance</td> 
    </tr> 
	 <tr> 
        <td>job Step instance Operation</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>operate_step_instance</td> 
    </tr> 
	    <tr> 
        <td>Inquire the job Execution Log based on the job Instance ID</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_job_instance_log</td> 
    </tr> 
    <tr> 
        <td>Inquire job execute Status based on job Instance ID</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_job_instance_status</td> 
    </tr> 
	 <tr> 
        <td>Inquire scheduled job information under Business Name</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>get_cron_list</td> 
    </tr> 
    <tr> 
        <td>Revise Scheduled Job status</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>change_cron_status</td> 
    </tr> 
    <tr> 
        <td>add or Update a Cron</td> 
        <td>TCP</td> 
        <td>standard (HTTP)</td> 
        <td></td> 
        <td>save_cron</td> 
    </tr> 
 </table> 