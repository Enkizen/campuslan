
//for the time being
sh int switchport | begin G1/1/1

2x Hot Swap L3 Switch + SFP to Next Layer
//Begin commands For the basic commands refer to access switch manual
//I will only take note of what is different here

en
conf t
int ran G1/1/1, G1/1/2
switchport mode access  
channel-group 1 mode active   //LACP better support for diff vendors

en
conf t
int ran G1/0/1, G1/0/2
switchport mode access  
channel-group 2 mode active 

spanning-tree vlan 1 root primary  //set the default root switch for the intended switch out. I chose the core 1 switch as primary and set next priority to be backup core 1 switch.
/////////////////////
//set root guard on the rest of the ports leading to the access switches aka DP
You should have root guard enabled on:

- Core ports that are connecting to the distribution switches

- Distribution ports that are connecting to the access switches

en
conf t
int ran G1/1/1, G1/1/2 ,g1/0/1, g1/0/2             
spanning-tree guard root


/////////////////// apply at AP and RP
spanning-tree guard loop
###loopguard and rootguard cannot coexist on the same port.
With version 7.1(1) of the Catalyst software (CatOS), loop guard can be enabled globally on all ports. Effectively, loop guard is enabled on all point-to-point links. 

On which ports should the loop guard be enabled? The most obvious answer is on the blocking ports. However, this is not totally correct. Loop guard must be enabled on the non-designated ports (more precisely, on root and alternate ports) for all possible combinations of active topologies. As long as the loop guard is not a per-VLAN feature, the same (trunk) port might be designated for one VLAN and non-designated for the other. The possible failover scenarios should also be taken into account.


///////REMOVED
switchport trunk encapsulation dot1q //cannot apply straight without first setting vlan.
switchport mode trunk                     //will enforce same vlan masking, need to test more
switchport trunk allowed vlan 1,10,20    //choose the vlan to allow thru. Must create Vlan prior. Must set Vlan to port. If set the etherchn alrdy, must undo etherchn first!!!
//////////////////////////////
Remove etherchannel (port-channel)
//////////////////////////////
Switch#conf t
Switch(config)#int gix/x/x
Switch(config-if)#no channel-group x
Switch(config)#exit
Switch(config)#no interface port-channelx
Switch(config)#
////////////////
//////////////////////////////

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
