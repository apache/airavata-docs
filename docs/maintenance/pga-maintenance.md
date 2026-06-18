## PGA Maintenance


1. <a href="#FAILED">Investigate FAILED experiments/jobs</a></br>
2. <a href="#unavailable">Handling unavailable Compute Resources</a></br>
3. <a href= "#GtwyAccessI">Managing User Accounts</a></br>
4. <a href= "#GtwyAccessII">Changing roles is not providing proper access</a></br>
5. <a href= "#Allocation">Community account ran out of SUs</a></br>
6. <a href="#PrePostCommands">Add Pre and Post Job Commands for an Application</a></br>
7. <a href="#SampleApp">Add Environment Variables for an Application Deployment</a></br>
8. <a href= "#Resources">Register your Compute & Storage Resources</a></br>
9. <a href= "#Preference">Gateway Preference Management</a></br>
10. <a href= "#Notices">Communication with Gateway Users</a></br>
11. <a href= "#Traffic">Monitor Gateway Traffic</a></br>
12. <a href= "#Secure">Using Credential Store</a></br>

<b class="blue" id="FAILED">Q1.</b> One of my gateway users wants me to investigate his FAILED experiment. How should I proceed?
<br><b class="blue">Answer:</b> To investigate a specific FAILED experiment or failed experiment within a time frame,<br>
1. Navigate to AdminDashboard &#8658; Experiment Statistics <br>
2. Search the experiment by using the experiment ID. <br>
OR
3. Search by providing the creation time period. You can further filter by giving <br>
        - Gateway username<br>
        - Application<br>
        - Compute Resource <br>
4. You could also use pre-defined selection criteria ('Get Experiments from Last 24 Hours' OR 'Get Experiments from Last Week')<br/>
5. Once the experiment/s listed click on the 'Check Stats'
6. Experiment task breakdown is listed and as the admin you could locate which task failed. Advise the gateway user accordingly.

<b class="blue" id="unavailable">Q2.</b> One of the resources used by my gateway is not available for the day. How to stop user job submissions?
<br><b class="blue">Answer:</b> To temporarily stop users submitting jobs to a particular resource...<br>
1. Navigate to AdminDashboard &#8658; Compute Resources (Browse)<br>
2. Un-check the  'Enabled' box for the specific resource. This disables job submissions for the resource<br>
3. To enable job submission simply check the box and you are back on track!<br>
NOTE: In order to enable disable resources you require super admin rights to the gateway. If not you need to contact SciGaP admins.

<b class="blue" id="GtwyAccessI">Q3.</b> How to upgrade access for a gateway user?
<br><b class="blue">Answer:</b> User access can be upgraded or downgraded by changing the assigned user role.<br>
1. Navigate to Admin Dashboard &#8658; Users (Browse)<br>
2. Search for the specific user and click 'Check All Roles'<br>
3. From this you can remove/add roles.<br>
4. For each modification user will receive an email with 'Your Privileges Have Changed!'<br>

<b class="blue" id="GtwyAccessII">Q4.</b> Gateway users who has role 'gateway-user' cannot access experiment creation. Seems like privileges are not accessible.!
<br><b class="blue">Answer:</b> User roles are given through PGA Admin Dashboard. If the roles are set correctly then check pga_config.php<br>
1. To check the config file use
<pre><code>vi /var/www/html/airavata-php-gateway/app/config/pga_config.php</code></pre>
2. Roles attached to users should exist in the config file against correct role attribute type
<pre><code>
        /**
         * Admin Role Name
         */
        'admin-role-name' => 'admin',
        /**
         * Read only Admin Role Name
         */
        'read-only-admin-role-name' => 'admin-read-only',
        /**
         * Gateway user role
         */
        'user-role-name' => 'airavata-user',
</code></pre>

NOTE: In order to view and change config file you require access to PGA backend. If not you need to contact SciGaP admins.

<b class="blue" id="Allocation">Q5.</b> I have run out of allocation for my current community account used in gateway for a resource. What should I do?
<br><b class="blue">Answer:</b><br> 
1. If you have another community account you could update the information in Admin Dashboard &#8658; Gateway Profile under Compute Resource Preferences.<br>
2. Select the resource and modify account information and save.<br>
3. Login to the resource as the new user and update the authorized_keys with the public key assigned to the resource.<br>

<b class="blue">Q6.</b> I want to send notices to my gateway users. How?
<br><b class="blue">Answer:</b><br>
1.  Navigate to Admin Dashboard &#8658; Notices <br>
2. Use 'Create a New Notice' button add a new notice. <br>
3. Based on the published date you provided it will be available for users as a Notice !

<b class="blue">Q7.</b> How to open the gateway to any user who create a user account? In the gateway not required to enable/activate user accounts.
<br><b class="blue">Answer:</b><br>
1. Gateway admin can switch between options of opening the gateway to all account creations OR gateway admin to activate accounts after creation.<br>
2. In order to do open the gateway to all,<br>
        - If the gateway is hosted by Airavata team, please request from them <br>
        - If you are hosting the gateway, navigate to <pre><code>vi /var/www/html/airavata-php-gateway/app/config/pga_config.php</code></pre> Then change the initial user role to 'gateway-user' <br>
        <pre><code>
                /**
                 * Initial user role. This is the initial user role assigned to a new
                 * user. Set this to one of the three roles above to automatically
                 * grant new users that role, or set to some other role ('user-pending')
                 * to require admin approval before users have access.
                 */
                'initial-role-name' => 'gateway-user',
        </code></pre>
        
<b class="blue">Q8.</b> I want my gateway users to use their own compute resource allocation to submit jobs through the gateway. How to do this?
<br><b class="blue">Answer:</b><br>
1. Users can add their own allocation account details. <br>
2. In order to do so first login to the gateway.<br>
3. Then Go to User Settings &#8658; Compute Resources<br>
4. Click the 'Add a Compute Resource Account' and enter all the details and save.<br>

After at experiment creation,edit and clone<br>
1. When you select the compute resource which has your account defined in the gateway, default option is to submit the job using user's own account.<br>
2. User has the option of selecting community account for job submission as well.<br>