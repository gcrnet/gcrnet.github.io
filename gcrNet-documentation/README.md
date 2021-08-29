# The gcrNet

## Introduction:

### What is The gcrNet:
Gate City Research Network (gcrNet) is a multi-institutional Science-DMZ created by UNC Greensboro
and North Carolina A&amp;T State University for the purpose of supporting data intensive research. The
gcrNet is supported by the National Science Foundation Office of Advanced Cyber Infrastructure and is
available to faculty at UNC Greensboro, NC A&amp;T, and their research collaborators. <br>
The gcrNet is designed to build upon the Science DMZ architecture developed by the Energy Sciences
Network (ESnet) to meet the needs of high performance science applications in a network that is shared
by multiple institutions. Whereas the science DMZ network is designed to facilitate the transfer of big science data across wide
area networks (WANs), typically at rates of 10 Gbps and above.

## Features:

A Science DMZ provides a network environment customized to the demands of high-performance science applications, such as massive data transfers, distant experiment control, and data visualization. It solves typical network performance issues for participating research institutes.
The main characteristics of a Science DMZ are the deployment of a friction-free path between end devices across the WAN, the use of DTNs, the active performance measurement and monitoring of the paths between the Science DMZ and the collaborator networks, and the use of access-control lists (ACLs) and ofﬂine security appliances.

1. Friction-free network path
The path has no devices that may add excessive delays or cause the packet to be delivered out of order; e.g., ﬁrewall, IPS, NAT. The rationale for this design choice is to prevent any packet loss or retransmission which can trigger a decrease in TCP throughput. Data Transfer Nodes (DTNs) are connected to remote systems, such as collaborators’ networks, via the WAN. The high-latency path is composed of routers and switches which have large buffer sizes to absorb transitory packet bursts and prevent losses.

2. Dedicated high-performance DTNs
These devices are typically Linux devices built and conﬁgured for receiving WAN transfers at high speed. They use optimized data transfer tools such as Globus, gridFTP. General-purpose applications (e.g., email clients, document editors, media players) are not installed. Having a narrow and speciﬁc set of applications simpliﬁes the design and enforcement of security policies.

3. Performance measurement and monitoring point
Typically, there is a primary high-capacity path connecting the Science DMZ with the WAN. An essential aspect is to maintain a healthy path. In particular, identifying and eliminating soft failures in the network is critical for large data transfers. <br> When soft failures occur, basic connectivity continues to exist but high throughput can no longer be achieved. Examples of soft failures include failing components and routers forwarding packets using the main CPU rather than the forwarding plane. Additionally, TCP was intentionally designed to hide transmission errors that may be caused by soft failures. <br> The performance measurement and monitoring point provides an automated mechanism to actively measure end-to-end metrics such as throughput, latency, and packet loss. The most used tool is perfSONAR.

4. ACLs and ofﬂine security appliances
The primary method to protect a Science DMZ is via router’s Access Control Lists (ACLs). Since ACLs are implemented in the forwarding plane of a router, they do not compromise the end-to-end throughput. Additional ofﬂine appliances include payload-based and ﬂow-based intrusion detection systems (IDSs).

![image](https://i.imgur.com/ta2jAwM.png)



## Get Started:
* Accessing The gcrNet
* Accessing the Data Transfer Node(DTN) through Globus
* Accessing the network performance-measurement tools.
* Accessing Shared storage (Can researchers mount it on their device?)
* Layout of the gcrNet (Final diagram from network and systems)

### Background:

A Science DMZ has the following elements as described by the US Department of Energy’s Energy Sciences Network ([ESnet](https://www.es.net/)):

* High-speed, low-latency network with equipment, configuration, and security policies that are optimized for high-performance scientific applications, rather than for general-purpose business systems.
* Dedicated high-performance data transfer nodes that optimize the transfer of large datasets over long distance.
* Performance-measurement nodes.
* Access to shared storage
    
## Roles and Responsibilities:
This is still to be defined but below are examples
* Help select system/network hardware and software
* Develop specifications for new equipment
* Configure hardware, software, and operating systems
* Optimize the network stack for high-speed data transfer
* Provide consultation services for how to connect to the Science DMZ or Data Center hosting
* Provide an estimate for one-time and ongoing costs for direct connection to the Science DMZ, for connections outside the Data Center
    
### Client Responsibilities
1. Learn how to use Globus
2. Move data to the DTN
3. [Review ESnet usage policy](https://fasterdata.es.net/science-dmz/science-dmz-users/)
4. Maintain your hosts in accordance with security best practices
5. Review related services.
6. Follow Prescribed security best practices at all times.

## Availability
 *Change Management and maintenance calendar to come!*
Because the Science DMZ is not a normal administrative or production network, but rather a research-driven service, changes are deployed in a more dynamic/agile manner than a regular network. High availability is not expected. Support is provided during business hours. Users will also be added to an event email list and notified of changes that impact services. 

## Data Security
* We have said this is for open science
*  Sensitive data will go somewhere else

## Cost



## Related services
* [HPC]()

## More about The Science DMZ
* Get more information on Science DMZ [here](https://fasterdata.es.net/science-dmz/)
* [The Science DMZ: A Network Design Pattern for Data-Intensive Science](https://ieeexplore.ieee.org/document/6877518) access to IEEE content is available from the UCSC campus network or VPN.
* [Josh Sonstroem’s presentation: "Of Mice and Elephants: The Science DMZ and You"](https://prezi.com/h356ads5aaa_/of-mice-and-elephants-dco/)
* [UC IT Blog: Helping Scientists Understand Research Cyber Risks using the Open Science Cyber Risk Profile tool ](https://cio.ucop.edu/helping-scientists-understand-research-cyber-risks/)


## Policy Information


## Standards


## Get Help
The Science DMZ team will provide best-effort support, including configuration and troubleshooting for:
* Transfer issues for large dataset.
* Remote-transfer techniques, including using Globus
* Using perfSONAR to monitor end-to-end network performance
If you have a use case you think might not be covered by these services, we’d still like to hear about what you need. Researchers’ needs will be used to shape these services in the future.
Contact the Science DMZ [team](j_fossot@uncg.edu).
