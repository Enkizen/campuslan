2x Hot Swap L3 Switch + SFP to Next Layer

//Begin commands

en
conf t
en secret WithPride!!$@&WeLead
username admin7 privilege 15 secret WithPride!7!$@&WeLead
line vty 0 4
transport input ssh
login local
exit

###By default, when you configure a Cisco device, you have to use the console cable and connect directly to the system to access it. Follow the steps mentioned below, which will enable SSH access to your Cisco devices. Once you enable SSH, you can access it remotely using PuTTY or any other SSH client.

First, make sure you have performed basic network configurations on your switch. For example, assign default gateway, assign management ip-address, etc. If this is already done, skip to the next step.

In the following example, the management ip address is set as 192.168.101.2 in the 101 VLAN. The default gateway points to the firewall, which is 192.168.101.1
###
//ip management of switch

ip default-gateway 192.168.101.1

interface vlan 101
ip address 192.168.101.2 255.255.255.0                  
exit
hostname sswitch
ip domain-name enkizen.com
crypto key generate rsa
2048
ip ssh version 2

//login banner

banner login #
Only authorized people and services are allowed to proceed.
Monitoring is active on this system and your access has been logged.
By proceeding, you accept to the terms and liable for any criminal or negligence activity.
#
//login banner not available on packet tracer

banner motd #
Only authorized people and services are allowed to proceed.
Monitoring is active on this system and your access has been logged.
By proceeding, you accept to the terms and liable for any criminal or negligence activity.
#
//portfast
int ran g2/1,g3/1,g4/1,g5/1,g6/1,g7/1,g8/1,g9/1
spanning-tree portfast
spanning-tree bpduguard enable

end
wr

//shorten version
en
conf t
en secret WithPride!!$@&WeLead
username admin7 privilege 15 secret WithPride!7!$@&WeLead
line vty 0 4
transport input ssh
login local
exit
int ran g2/1,g3/1,g4/1,g5/1,g6/1,g7/1,g8/1,g9/1
spanning-tree portfast
spanning-tree bpduguard enable
exit

ip default-gateway 192.168.101.1

interface vlan 101
ip address 192.168.101.2 255.255.255.0                  
exit
hostname sswitch
ip domain-name enkizen.com
crypto key generate rsa
2048
ip ssh version 2
banner motd #
Only authorized people and services are allowed to proceed.
Monitoring is active on this system and your access has been logged.
By proceeding, you accept to the terms and liable for any criminal or negligence activity.
#
end
copy run start
//end of shorten version
