# zabbix-longhorn
A simple Zabbix template to monitor Kubernetes Longhorn Storage via Zabbix Proxy.

# How to use it
### Prerequisite
- Setup Zabbix proxy inside Kubernetes Cluster
- Add Zabbix proxy to Zabbix server

### Add hosts in Zabbix
1. Get longhorn API IP per nodes.
kubectl get pod -n longhorn-system -o wide |grep longhorn-manager
e.g.
10.244.254.11 node1
10.244.254.12 node2

2. Import zabbix template "zbx_longhorn_templates.yaml"
Zabbix GUI -> Configuration -> Templates -> Import -> "Upload the template"

3. Create a new host (separately for Longhorn) with template "Kubernetes Longhorn state by Zabbix Proxy"
Zabbix GUI -> Configuration -> Hosts -> Create host

4. Edit Macros, configure Longhorn API URL.
{$LONGHORN.API.URL} = 10.244.254.11

# Requirement
Zabbix 7.4
