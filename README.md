# campuslan
Self-directed project to design and config a campus wired lan with industry best practices using packet tracer.

Mission
SGUS only introduce the concepts of networking on the surface level.
To hone skills enough to design and manage a real-world network


##Must have##
<b>Traditional 3 layer hierarchy Architecture (Not the spine and leaf)</b>

1. Topology diagram
+
DHCP
DNS
DMZ


2. Documented config and the reasoning

3. Macros for QoS config
The result of using Layer 3 to interconnect the two core layers is: 
• A resilient Layer 3 interconnect with rapid failover. 
• A logical separation of change control for the two core networks. 
• A LAN core that provides a scalable interconnect for LAN, WAN, and Internet Edge. 

• A data center core that provides interconnect for all data center servers and services. 
• Intra-data center Layer 2 and Layer 3 traffic flows between servers and appliances that are switched locally on the data center core. 
• A data center that has a logical separation point for moving to an offsite location while still providing core services without redesign


//Limitations
All the models of routers and switches in packet tracer are outdated and end of support already.
Packet tracer cannot create power distribution unit. I will ignore terminal console server cos pt doesnt support terminal console server.

In-band management
Out-band Management
