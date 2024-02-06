# Setup SNMP on RHEL 9 Servers via Ansible Playbook
Playbook will do the followings:
- Check if SSH port 22 is open
- Check if net-snmp package is installed, If Installed, Skip every next step
- If not installed, Install net-snmp package
- Backup original snmpd.conf to /etc/snmp/snmpd.conf_{date and time}_before-install_backup
- Commenting out these existing lines in snmpd.conf
  
syslocation Unknown (edit /etc/snmp/snmpd.conf)

syscontact Root <root@localhost> (configure /etc/snmp/snmp.local.conf)

- Append snmp.conf file with following lines, so that you can change the parameters


SNMP community id HERE

Target Host HERE

syslocation TYPEHERE

syscontact TYPHERE


- Start and enable snmpd service
- Whitelist ports if firewalld is running and Reload firewalld
161/udp
162/udp
161/tcp
162/tcp
