##Useful
/filter            //linux command in cisco cli

At global config mode // not available on packet tracer
shell processing full
end
// this will turn on grep which allows filter in linux
show ip int brief | grep keyword | grep -v (not show keyword) | grep -v (exclude keyword)

show ip int brief | include    //grep is able to do more than include !!!! It can do exclude.

show run | grep 1.1

//other commands
show shell function //list all of the linux command available here

//Can even pipe
sh run > shrun.cfg

uname -a
uname -s

//for the time being
sh int switchport | begin G1/1/1

2x Hot Swap L3 Switch + SFP to Next Layer
//Begin commands For the basic commands refer to access switch manual
//I will only take note of what is different here

en
conf t
int ran G1/1/1, G1/1/2
switchport trunk encapsulation dot1q
switchport mode trunk                     //seems like default already auto trunking
switchport trunk allowed vlan 1,10,20    //choose the vlan to allow thru. Must create Vlan prior. Must set Vlan to port. If set the etherchn alrdy, must undo etherchn first!!!
//////////////////////////////
Remove etherchannel (port-channel)

Switch#conf t
Switch(config)#int gix/x/x
Switch(config-if)#no channel-group x
Switch(config)#exit
Switch(config)#no interface port-channelx
Switch(config)#
////////////////

https://www.cisco.com/c/en/us/support/docs/smb/switches/cisco-small-business-300-series-managed-switches/smb5653-configure-port-to-vlan-interface-settings-on-a-switch-throug.html

channel-group 4 mode on
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


en
conf t
int ran G1/1/1, G1/1/2
switchport trunk encapsulation dot1q
switchport mode trunk                   
channel-group 4 mode on


//end of shorten version
