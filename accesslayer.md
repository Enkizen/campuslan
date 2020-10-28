Per Server<br />
Gigabit Ethernet Network Module CGE x 2 (Future considerations 1FGE)<br /> 
2 Cat 6 Copper Ethernet cable (FC: Cat 7 or 8) <br />

STS (Static Transfer Switch) if the switch only has 1 power supply. <br />

2x Hot Swap L3 Switch + SFP to Next Layer 1 L2 Switch <br />

Hardening
https://www.cisco.com/c/en/us/support/docs/ip/access-lists/13608-21.html#anc14

Access Switch Config
//Login Password Retry Lockout

//No Service Password-Recovery
In Cisco IOS Software Release 12.3(14)T and later, the No Service Password-Recovery feature does not allow anyone with console access to insecurely access the device configuration and clear the password. It also does not allow malicious users to change the configuration register value and access NVRAM.

//For router
aaa new-model
aaa local authentication attempts max-fail 7 <max-attempts>
aaa authentication login default local

no service password-recovery

// clock issues not settled.
https://www.cisco.com/c/en/us/support/docs/smb/switches/cisco-small-business-300-series-managed-switches/smb5584-configure-system-time-settings-on-a-switch-through-the-comma.html

//possible external server that handles user account

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
wr
//end of shorten version
