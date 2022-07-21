---
layout: post
title: Science DMZ FAQs
feature-img: "assets/img/pexels/computer.jpeg"
date: July, 20 2022
---
## General

What is the gcrNet?
> It is a Science DMZ, a network or a portion of network, designed to facilitate the transfer of  big science data.

How can I access the gcrNet?
> Access to the gcrNet is granted by the gcrNet technical team. The first round of network drops were installed based on a list compiled during the proposal development. Future access will require an application to be submitted to our technical team. If selected to receive a gcrNet network attachment a network port will be installed in your office or lab and you will need a 10GbE Network Interface Card (NIC).

I still have questions. How do I contact you?
> You may contact us using Phone 336-256-8324 and email 6tech@uncg.edu

## Technical

What are the minimum system requirements?
> Unless you have a high-performance workstation chances are your hardware is not immediately compatible with the gcrNet. Users may need to upgrade their systems to include a disk system capable of transfer speeds over the standard 1 Gigabit per second. The 10GbE network enables speeds of up to 1.25 Gigabytes per second. Standard SATA hard drives see speeds of around 150 Megabytes per second, or about 1/10th of the available gcrNet bandwidth.
> The following is a list of must-haves for your system:
> * A workstation with an available PCIe 2.0 x8 slot
> * 10GbE Network Card
> * Storage system capable of high bandwidth transfers
>   * Single SSD drive
>   * Array of SATA/SSD disks

What software is necessary to leverage the gcrNet?
> Traditional file transfer protocols do not support the increased bandwidth available to users on the gcrNet.
> There are two programs commonly used to move large datasets over high-bandwidth networks:
> * [Globus](https://docs.globus.org/)
> * [bbcp](https://www.slac.stanford.edu/~abh/bbcp/)         
> Both your local workstation and the remote data source will need matching software.

How can I verify the gcrNet speeds?
> Several network performance diagnostics tools will be available to test connectivity speeds.
> * [perfSONAR Dashboad](http://uncg-mcnuttperf01.gcrnet.org/maddash-webui/) perfSONAR is the *perf*ormance *S*ervice-*O*riented *N*etwork monitoring *AR*chitecture, a network measurement toolkit designed to provide federated coverage of paths and help to establish end-to-end usage expectations. 
> * [iPerf/iPerf3](https://iperf.fr) iPerf3 is a tool for active measurements of the maximum achievable bandwidth on IP networks. It supports tuning of various parameters related to timing, buffers and protocols (TCP, UDP, SCTP with IPv4 and IPv6). For each test, it reports the bandwidth, loss, and other parameters.
> * [One-Way Ping (OWAMP)](http://software.internet2.edu/owamp/) OWAMP is a command-line client application and a policy daemon used to determine one-way latencies between hosts.
> For additional information regarding the use of these tools, you may contact us using Phone 336-256-8324 and email 6tech@uncg.edu

Can I connect to the gcrNet with an Apple computer?
> Yes. Apple computers can connect to the gcrNet provided they have a Thunderbolt port and an [external network card](https://store.apple.com/us/product/HC294LL/A/atto-thunderlink-nt1102-thunderbolt-to-10-gbits-ethernet-desklink-device)
> Please review the minimum workstation system requirements to determine if a hardware upgrade will be required.

## Security

Can my gcrNet workstation be physically connected to the GCN Enterprise Network simultaneously?

> No. Your gcrNet workstation may only connect to the gcrNet.


Can I access resources on the Science DMZ from outside the network?

> Yes, services within the Science DMZ will be available outside the network.

