Per Server<br />
Gigabit Ethernet Network Module CGE x 2 (Future considerations 1FGE)<br /> 
2 Cat 6 Copper Ethernet cable (FC: Cat 7 or 8) <br />

STS (Static Transfer Switch) if the switch only has 1 power supply.

Hardening
https://www.cisco.com/c/en/us/support/docs/ip/access-lists/13608-21.html#anc14

Access Switch Config
//Login Password Retry Lockout

//No Service Password-Recovery
In Cisco IOS Software Release 12.3(14)T and later, the No Service Password-Recovery feature does not allow anyone with console access to insecurely access the device configuration and clear the password. It also does not allow malicious users to change the configuration register value and access NVRAM.

aaa new-model
aaa local authentication attempts max-fail 7 <max-attempts>
aaa authentication login default local

no service password-recovery

// clock issues not settled.
https://www.cisco.com/c/en/us/support/docs/smb/switches/cisco-small-business-300-series-managed-switches/smb5584-configure-system-time-settings-on-a-switch-through-the-comma.html


//Begin commands

en
