stanchion
========

This role will setup the Stanchion component of Riak CS cluster on a node. It will ***not*** build a cluster.  In order to build a cluster, use one of the example playbooks defined in the riakcs role's README.md.

Requirements
------------

None

Role Variables
--------------

The following variables are available

Variables listed with "OS Specific" and "Install specific" have values defined in `vars/<ansible_os_family>.yml`.




| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| riakcs_admin.user | admin      | default Riak CS admin user name    |
| riakcs_admin.email | admin@admin.com | default email address for Riak CS admin user |
| riakcs_admin_creds.key | foo      | default admin access key    |
| riakcs_admin_creds.secret | bar | default admin secret key |
| riakcs_creds_path | /tmp/riakcs_creds.yml       | The path where Riak CS creds will be stored  |
| riakcs_creds_reset_ip| 127.0.0.1:8080| IP: port to CS node for resetting credentials|
| stanchion_auth_bypass | 'false'         | bypasses authentication mechanism |
| stanchion_bind_ip  | 0.0.0.0           | The IP address used to listen for Stanchion requests.   |
| stanchion_iface | eth0       | The interface that listens for Stanchion requests.   |
| stanchion_ip_addr| {{ hostvars[inventory_hostname]['ansible_' + stanchion_iface]['ipv4']['address'] }}"             |  shortcut for the ip address associated with stanchion_iface |
| stanchion_node_name | stanchion@{{ stanchion_ip_addr }} | node name for stanchion node |
| stanchion_port   | 8085| port which stanchion listens.|
|stanchion_package_release| 1| release of Stanchion package|
| stanchion_reset_creds| no             | Tell stanchion to obtain new credentials|
| stanchion_riak_ip | 127.0.0.1 | IP address of a Riak Node |
| stanchion_riak_port| 8087             | port of Riak Node
| stanchion_version | 1.4.3 |version of Stanchion |



Dependencies
------------
* basho.riak-common role
* Python's httplib module to interface with Riak CS's API to create users.


Playbooks
-------

This role doesn't really do much of anything by itself, it works in conjunction with Riak and Riak CS.  Please see the documention of the riakcs role for an example of how to use this role.


License
-------

Apache

Author Information
------------------

jmartin@baso.com