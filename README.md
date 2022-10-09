# zabbix_template_sysctl_services

A Zabbix template for check linux services managed by sysctl (with agent and not agent2)
In Zabbix there is a template for monitoring services managed by systemd only using agent2.
This is a simple template with LLD for classical agent. Tested on Zabbix 6.0 and 6.2

Use:
1) copy the systemd.conf file in the agent include directory and restart zabbix agent. Include directory can be found with:
grep -i include /etc/zabbix/zabbix_agentd.conf
2) Import the zabbix_template_sysctl_services.yaml template
3) set up the macro {$SYSTEMD.NAME.SERVICE.MATCHES} with the name of the services you want to monitor.

Insert in this macro only the services interesting for you context is a good idea. It's necessary to insert the services with full name, eg:
^ssh.service|grafana-server.service|postfix.service$

There is only one item prototype and only one trigger prototype.
The trigger activates if the result is different from "active"
