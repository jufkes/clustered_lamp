# clustered-lamp playbook

DESCRIPTION: 
This is playbook will provision a clustered lamp stack with public IP address in the CenturyLink Cloud. The public address will only pass 80 and 443 traffic. This playbook performs the following
-- provisions servers and groups (1 HAProxy and 2 LAMP by default)
-- installs and configures HAProxy with LAMP server addresses
-- installs and configures Apache with default parameters
-- installs and configures Mysql with replication
-- deploys content if included

DEPENDENCIES:
-- Place your public key in the 'keys/ssh-rsa-key.pub' file

TYPICAL OVERRIDES: 
-- key_loc: specify a file (absolute path) to your public key (default == keys/ssh-key.pub)
-- datacenter: the datacenter to deploy the solution (default == VA1)
-- lamp_group_name: the name of the group for the clustered lamp servers (default == LAMP)
-- lamp_server_name: the base name for the LAMP servers (default == LAMP)
-- lamp_server_count: the number of servers to provision for the LAMP group (default == 2)
-- haproxy_group_name: the name of the group for the HAProxy server (default == HAPROXY)
-- haproxy_server_name: base name for the HAProxy server (default == HAPXY)
-- lampuser: user for access to the mysql database *recommend changing* (default == lamp)
-- lamppass: password for lampuser *recommend chaning* (default == lamp)
-- mysqldatabase: database for content (default == lamp)
-- mysqlpassword: password for replication *recommend changing* (default == lamp)

RECOMMENDED: 
- Pull the playbook down 
- add your public key to the keys.ssh-rsa-key.pub file
- push your pages to the roles/content/files
- specify the pages in the roles/content/vars/main.yml file
- activate the 'content' role in the site.yml (uncomment it)
- push to git 
- run it through the CLC Automation engine