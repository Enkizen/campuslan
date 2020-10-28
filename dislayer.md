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

2x Hot Swap L3 Switch + SFP to Next Layer
//Begin commands For the basic commands refer to access switch manual
//I will only take note of what is different here

en
conf t

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
