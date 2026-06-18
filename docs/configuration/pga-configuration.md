## PGA Configuration
### You Need to Have
1. Airavata & PGA installed and running.
2. Tenant created in WSO2 IS hosted by you or Airavata team.
3. Administrator privileges to the gateway. (How do you know? - Can you view Admin Dashboard and view buttons to create applications)
<br>
<br>
### Apache Airavata Component Configuration
1. For this we use 'Admin Dashboard'
2. Gateway Admin needs to configure;<br>
	- <a href="#CompResource">Compute Resources</a><br>
	- <a href="#StoreResource">Storage Resources</a><br>
	- <a href= "#Preference">Gateway Management</a><br>
	- <a href= "#AppCatalog">Application Catalog</a><br>
		- Application Module<br>
		- Application Interface<br>
		- Application Deployment<br>
	- <a href= "#Credentials">Credential Store</a>
		- Generate Credential Store Token + SSH Key.
		- Add these to authorized key files and into resource preferences.
	- <a href= "#Notices">Notices</a>
		- Notices for all active gateway users.
	- <a href= "#ISConfiguration">Identity Management</a>	

<b>NOTE</b>: for gateways hosted by SciGaP gateway admins/PIs not required to register the compute resources and storage resource. Please skip the 1st and 2nd and go to Gateway Management section.
<br>
###Compute Resources
1. Navigate to Admin Dashboard &#8658; Compute Resources &#8658; Register
2. Add Host Name, Description and create the resource.
<br>Hint: host name is used when ssh to the resource from airavata.
3. Then keep adding information on rest of the appeared tabs.
	- Queues (Queue name is unique and cannot be updated. Can delete and create new if required)
	- File Systems (This is only for information capturing for future use. Currently this information is not used. So can skip if you want)
	- Job Submission Interfaces
	- Data Movement Interfaces
5. Similarly you can add multiple compute resources into your gateway by selecting 'Register' from the left-hand-side menu.
6. To view the added compute resources navigate to Admin Dashboard &#8658; Compute Resource &#8658; Browse
7. All the resources will be listed. Gateway admin can view, edit, delete and enable and disable them.
<br>
<br>
###Storage Resources
1. Navigate to Admin Dashboard &#8658; Storage Resources &#8658; Register
2. Add Storage Name, Description and create the resource.
3. Then add data storage information in
	- Data Movement Interfaces
4. Similarly you can add multiple storage resources into your gateway by selecting 'Register' from the left-hand-side menu.
5. To view the added resources navigate to Admin Dashboard &#8658; Storage Resources &#8658; Browse
6. All the resources will be listed. Gateway admin can view, edit, delete them. 
7. Although enable and disable can be done in registration its functionality is not yet implemented.
<br>
<br>
###Gateway Management of Resources
1. Navigate Admin Dashboard &#8658; Gateway Management
2. Both compute resource and storage resource specific preferences are defined here.
3. To add compute resource related preferences click "Add a Compute Resource Preference" and select the resource from the drop-down list.
4. Add/select preferred options and click "Set preferences".
<br>Repeat this for all the resources used within the gateway.
4. For each compute resource, gateway admin need to specify;
  	- Preferences can be overridden by Airavata - Yes/No?
  	- Resource login name
  	- Preferred job submission protocols
  	- Preferred data movement protocols
  	- Preferred queue
  	- Scratch location
  	- Project allocation number
  	- Resource specific credential store token <br>(When added Base Credential Store Token is not valid for the specific resource)
  	- Gateway ID for usage reporting <br>(This field will only appear if the compute resource registration is set to report usage details back to the resource)
  	- Quality of service
  	- Reservation name
  	- Reservation start and end date time
5. For adding storage resource preference click "Add a Storage Resource Preference", and rest is similar to adding a compute resource preference.
6. For a gateway currently when a storage resource is selected, that resource ID need to be added into the pga_config.php file in config folder of the hosted gateway.
7. For storage resource preference, gateway admin need to add;
	- Login username
	- File System Root Location
	- Resource Specific Credential Store Token
8. Apart from adding preference the same interface is used to assign a 'Base Credential Store Token'. If this is added this is the token used across the gateway for communication with all the compute resources and storage resource.
<br>
<br>
###Application Catalog
1. Users in Admin group can add applications into the gateway.
2. Adding an application involves adding details into the three tabs - Details, Interface and Deployments.
4. What each tab means and capture?
	- <b class="blue">Application Module</b>
		- Navigation: Admin Dashboard &#8658; App Catalog &#8658; Module
		- This is the simple introduction of the application; Name, Version and Description.
		- Click 'Create a New Application Module', provide information and create. On creation Application Module ID will be generated for the module.
		- All existing modules are listed; Search by name is available for a particular module.
		- Gateway admin can edit, delete existing modules.
		- Deleting a module will be restricted if it has application interfaces and deployments linked.
	- <b class="blue">Application interface</b>
		- Navigation: Admin Dashboard &#8658; App Catalog &#8658; Interface
		- Application interface defines the required inputs, outputs produced and their characteristics.
		- Click on 'Create a New Application Interface', provide information and create. On creation Application Interface ID will be generated for the module.
        - All available interfaces are also listed; admin has the option of searching for a particular interface by providing the name in the search.
        - Gateway admin can edit, delete existing interfaces.
        - Gateway admin can also clone an existing interface in order to create a new similar interface with slight changes.
	- <b class="blue">Application deployment</b>
		- Navigation: Admin Dashboard &#8658; App Catalog &#8658; Deployment
			- Application deployment describes application deployment details on a specific resource.
			- For an application for each resource there is a separate deployment.
			- A single application can be deployed in multiple resources.
			- Multiple application modules can be deployed in a single resource. E.g: Gaussian09 and Gaussian16 both exist in bridges.psc.edu and they both use same application interface.
<br>
<br>
###Credential Store
1. Navigation: Settings &#8658; Credential Store
2. This interface is used to generate SSH key + token pairs.
3. These generated keys can be added into the authorized key files in each resource for SSH key based communication.
4. Generated key can be either assigned at gateway level or/and at individual resource allocation level; one key + token pair  for all the resources OR have separate key for each resource.
5. SSH keys are used for communication with compute resources and storage resources.

###Keycloak Configuration
<Will be added Soon!>
