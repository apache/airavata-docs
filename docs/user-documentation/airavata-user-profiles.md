## Apache Airavata User Groups

### What Are Airavata User Groups?

1. Prior to using Airavata, let's identify and understand the user groups available and their features.
2. Knowing the groups and the features of each, will assist on shaping your gateway user hierarchy.
3. There are 3 base user groups in Airavata with different set of features at each level.
	- Admin
	- Admin-Read-Only
	- Gateway-User

### Features of each User Group

1. Admin Group
	- Set up gateway Group Resource Profiles.
	- Add gateway storage resource profile.
	- Generate SSH keys for compute and storage resource SSH communications..
	- Add the generated SSH key to group resource profiles.
	- Add the generated SSH keys to authorized_keys files in each resource.
	- Create Applications and their deployments in to the gateway.
	- Manage users, add them to base groups.
<br><b>NOTE: If user hosts his own gateway; 'Gateway Admin' role will have access to create compute resources and storage resources as well.</b></br><br>
2. Admin-Read-Only
	- Can view everything in Settings but cannot Add, Edit or Delete any records from dashboard.
	- Can monitor experiments through Experiments Statistics in Experiment statistics.
<br></br>
3. Gateway User
	- Create, launch their own experiments in using available applications and compute resources.
	- Monitor progress of experiment execution.
	- Download experiment outputs from experiment summary or from the storage.
	- Upload files in to the storage for future use.
	- Group experiments by creating Projects.
	- Create own SSH keys from Credential store
	- Create Group Resource profiles to use individual HPC allocations for job submission through the gateway.
	- Password reset.


### How User Groups Work?

1. Users can belong to one or many user groups.
2. Two main categories of groups
    - Base groups - Created as default groups in the gateway at gateway deployment
    - User groups - Any user in the gateway can create user groups, and add other gateway users to the group.
3. Users in group will have one of the three roles. Three roles are:
    - Owner - Person who creates the user group
    - Admin - Person who can add other users in to the group. These users' role cannot be changed by users with admin role.
    - Member - This person can use benefits of the group, but cannot add or remove users from the group.
4. Only the owner of the group can change users' role. 
5. Adding users to base groups can be done using two interfaces.
    - Settings &rarr; Manage Users
    - Top right-hand corner dropdown menu &rarr; Groups
6. Adding users to any other group that you are an admin of or the owner of can be done using 
    - Top right-hand corner dropdown menu &rarr; Groups
7. In Manage Users page, users are listed with all the groups they are a member of.


