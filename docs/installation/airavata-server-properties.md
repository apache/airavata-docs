## Apache Airavata Server Properties

1.  API Server Registry Configuration
	- Comment out the derby DB properties
	- Change MySQL configurations
		- registry.jdbc.url=jdbc:mysql://localhost:3306/experiment_catalog (replace 'localhost' with correct server name if the DB is in a different server)
		- registry.jdbc.user=airavata
		- registry.jdbc.password=airavata
		- enable.sharing=true (This will set sharing within the gateway to be enabled. This is the advised mode)
		- default.registry.gateway=php_reference_gateway (Give the gateway name you prefer. Default exists in the file)
		- super.tenant.gatewayId=php_reference_gateway (Since you are hosting your own gateway this is the ID of your own gateway)
2.  Application Catalog DB Configuration
   	- Comment out the derby DB properties
   	- Change MySQL configurations
   		- appcatalog.jdbc.url=jdbc:mysql://localhost:3306/app_catalog
        - appcatalog.jdbc.user=airavata
        - appcatalog.jdbc.password=airavata
3.  Replica Catalog DB Configuration
    - Comment out the derby DB properties
    - Change MySQL configurations
    	- replicacatalog.jdbc.url=jdbc:mysql://localhost:3306/replica_catalog
        - replicacatalog.jdbc.user=airavata
        - replicacatalog.jdbc.password=airavata
4.  Workflow Catalog DB Configuration
	- Comment out the derby DB properties
    - Change MySQL configurations
		- workflowcatalog.jdbc.url=jdbc:mysql://localhost:3306/workflow_catalog
      	- workflowcatalog.jdbc.user=airavata
      	- workflowcatalog.jdbc.password=airavata
5. Sharing Catalog DB Configuration
	- Comment out the derby DB properties
		- sharingcatalog.jdbc.url=jdbc:mysql://localhost:3306/sharing_catalog
		- sharingcatalog.jdbc.user=airavata
		- sharingcatalog.jdbc.password=airavata
6. Sharing Registry Server Configuration
	- 
7. User Profile MongoDB Configuration
	- 
8. Server Module Configuration
	- Make sure all servers required to start are added as given
		- servers=credentialstore,apiserver,orchestrator,gfac
9. API Server Configurations

10. API Server SSL Configurations
	- Give the correct path for key generation file. This is in the bin directory and it is shipped default with Airavata.
		- apiserver.keystore=/home/airavata/LocalAiravata/apache-airavata-server-0.16-SNAPSHOT/bin/airavata.jks
11. Orchestrator Server Configurations

12. GFac Server Configurations

13. Registry Server Configurations

14. Airavata Workflow Interpreter Configurations

15. Job Scheduler can send informative email messages.........

16. Credential Store module Configuration
	- Add the path to SSH key generation file
		- E.g.: credential.store.keystore.url=/home/airavata/LocalAiravata/airavata-sym.jks
	- Comment out the derby DB properties
    - Change MySQL configurations
        - credential.store.jdbc.url=jdbc:mysql://localhost:3306/credential_store
        - credential.store.jdbc.user=airavata
        - credential.store.jdbc.password=airavata
		- credential.store.keystore.url=/home/airavata/production-deployment/airavata_sym.jks
17. Monitoring Module Configuration
    - Add your email address, username and password for email monitoring. This is the email account the job status change emails will be received from compute resources.
	- email.based.monitor.host=imap.gmail.com
	- email.based.monitor.address=jobs@sample.org
	- email.based.monitor.password=SamplePassword
18. AMQP Notification Configuration
	- Users can use RabbitMQ as 'Guest' users. This is the easy method. For this uncomment
		- rabbitmq.broker.url=amqp://localhost:5672
	- To use as a 'Production' user
		- Navigate to RabbitMQ bin folder.
		- Make sure the RabbitMQ server is running. For production use <pre><code>rabbitmq-server -detached</code></pre> to start.
		- Create a virtual-host and user with a password. Follow documentation in <a href="http://blog.dtzq.com/2012/06/rabbitmq-users-and-virtual-hosts.html" target="_blank">RabbitMQ Users & VirtualHost</a>
		- To create a user; <pre><code>rabbitmqctl add_user Username Password</code></pre>
		- To create a virtual-host <pre><code>rabbitmqctl add_vhost vhostauthvhost</code></pre>
		- Provide permission to the created 'Username'  to the created vhost <pre><code>rabbitmqctl set_permissions -p messaging airavata ".*" ".*" ".*”</code></pre>
		- Uncomment rabbitmq.broker.url=amqp://Username:Password@localhost:5672/Vhost. Add the created username, password and Vhost in the URL.
		- If you need to stop RabbitMQ use <pre><code>rabbitmqctl stop</code></pre>
		- If the RabbitMQ server stopped then the above user creation, vhost creation and permission granting commands need to run again after restarting the servers.
19. Zookeeper Server Configuration
	- For 'Production' scenario make;
		- embedded.zk=false
20. Aurora Scheduler Configuration


21. API Security Configuration
	- Make sure
		- api.secured=false
		- TLS.enabled=false
