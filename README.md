Nagios
================
Overview
-----------------
Nagios monitoring and alert server that watches services. ansible setups a central nagios server based on the nagios group in your host file. Then any thing you run this role against will have nrpe install on it and the correct config files added to the nagios server

Requirements
----------------------
-     epel repository
-     centos 5,6,7
      
Ansible Variables
---------------------
- htaccessuser=nagiosadmin                     || user for login to nagios via htaccess (only need for server in nagios group)
- htaccesspass=pickabetterpasswordthenthis     || password used for that user (only need for server in nagios group)
- nagiosemail=test@gmail.com                   || email to send notifications to (only need for server in nagios group)
      
Files
-------------------------
- /etc/nagios/                  || configuration diretory for nagios
- /etc/nagios/hosts             || nagios config files. to disable a monitor must be moved out of the hosts folder.
- /etc/nagios/cgi.cfg           || config that controls htaccess users access level
- /usr/lib64/nagios/plugins/    || plugins directory. you can manualy test plugins by running them from here
- /etc/nagios/objects/commands.cfg || contains System User Check which is set by what hostgroup the server is in.
- /etc/nagios/hosts/commands.cfg   || The different commands the services run to check server status
- /etc/nagios/hosts/contacts.cfg   || List of people to email about issues specifically for hosts
- /etc/nagios/hosts/groups.cfg     || The groups hosts are grouped into. cosmetic mostly but has to be set correctly or every thing breaks. pulls from ansible_host groups
- /etc/nagios/hosts/templates.cfg  || default templates used in the hosts folder

Ports
----------------------------
  tcp in/out on port 5666 for nrpe traffic
  tcp in/out on port 25 for mail alerts
  tcp in/out on port 80 for http

Nrpe
=====================
Files
-------------------
- /etc/nagios/nrpe.cfg || config file
- /var/log/messages    || nrpe log entries

Overview
--------------------
interfaces with the nagios server to run local plugins on the system

Ports
--------------------
- tcp in/out port 5666 for nrpe traffic

Requirements
--------------------
- epel repository

