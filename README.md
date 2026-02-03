# zabbix-longhorn
A simple Zabbix template to monitor Kubernetes Longhorn Storage via Zabbix Proxy.

# How to use it
### Prerequisite
- Setup Zabbix proxy inside Kubernetes Cluster
- Add Zabbix proxy to Zabbix server

### Add hosts in Zabbix
1. Get longhorn API IP per nodes.

kubectl get pod -n longhorn-system -o wide |grep longhorn-manager

e.g. 10.244.254.11 node1 / 10.244.254.12 node2

3. Import zabbix template "zbx_longhorn_templates.yaml"

Zabbix GUI -> Configuration -> Templates -> Import -> "Upload the template"

5. Create a new host (separately for Longhorn) with template "Kubernetes Longhorn state by Zabbix Proxy"

Zabbix GUI -> Configuration -> Hosts -> Create host

7. Edit Macros, configure Longhorn API URL.

{$LONGHORN.API.URL} = 10.244.254.11

# Tested by
Zabbix 7.4.2

Longhorn 1.9.0
