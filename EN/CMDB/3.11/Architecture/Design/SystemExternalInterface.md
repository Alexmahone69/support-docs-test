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
        <td>PAAS</td> 
        <td>TCP</td> 
        <td>standard (http)</td> 
        <td></td> 
        <td>/login/?  app_id=%s&c_url=%s</td> 
    </tr> 
    <tr> 
        <td>PAAS</td> 
        <td>TCP</td> 
        <td>standard (http)</td> 
        <td></td> 
        <td>/login/accounts/get_user/?  bk_token=</td> 
    </tr> 
    <tr> 
        <td>PAAS</td> 
        <td>TCP</td> 
        <td>standard (http)</td> 
        <td></td> 
        <td>/login/accounts/get_all_user/?  bk_token=%s</td> 
    </tr> 
    <tr> 
        <td>PAAS</td> 
        <td>TCP</td> 
        <td>standard (http)</td> 
        <td></td> 
        <td>/console/?  app=bk_agent_setup</td> 
    </tr> 
 </table> 