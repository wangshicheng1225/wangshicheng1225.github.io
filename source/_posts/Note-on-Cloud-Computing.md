---
title: Note on 软硬件融合:超大规模云计算架构创新之路
date: 2022-07-27 18:30:04
tags: [CloudComputing, DataCenter, Note, Review]
categories: 
- Notes
---

## Intro

Reviews and notes on book《软硬件融合:超大规模云计算架构创新之路》
<!-- 
## Chap 1: 云计算场景

对场景有个感性了解，认识一些数量级。 -->

## Properties of cloud computing

* Large scale Millions of servers. AWS 22 Region and 69 AZ, 400 M servers.Thus highly dedicated hardware, server and center
  
* Data volume 175 ZB in 2025.
  * Core, edge, endpoint.

* Multi-tenancy: HP IaaS. Performant virtulizaion and isoation on IaaS。
  * Diverse requiremnt: computaion, sotrage, communication.
* Complexity in network
  * BW: 25Gb->100Gb. Mellanox CX6 supports 200/400G.
  * Low latency :Akami: Page load latency + 1s .....<!-- * 就会导致转化率平 均下降7%，页面浏览量下降11%，用户满意度下降16%。在金融行业 中，即使1ms的延迟也会对高速交易算法的性能产生巨大影响 -->
    * OLTP: South-North
    * Explosive East-West traffic: A single request leads to thousands of internal requests.
  * Isolation and trans-zone access.
  * High-dynamical network
    * 10k Servers in a DC. Failure, upper-layer transactions, tenants and their applicaitons, reschedule the resources and network.
    * Locate the failure. (performance, failure, security issue) x (location, diagnosis, forensics).
  
## Security issues

Paper: `M. Ali, S. U. Khan, and A. V. Vasilakos, “Security in cloud computing: Opportunities and challenges,” Information Sciences, vol. 305, pp. 357–383, Jun. 2015.`
Actually the serutiy issues in this book is only a translation of this paper.

* External communication security issues: South-north traffic
  * DoS (spoofing, vo), MIM, etc.
  * **Solution** Similar to traditional network: IDS, IPSec, SSL, encryption, etc.
  * What can be the *differences*?
* Internal communication: East-west traffic
  * shared infrastructure: Multi-tenancy
    * Runtime, isolation, security
    * security mis-configuration
* Architectural security issues:
  * VM isolation, evasion, ....

## Virtulization

* CPU Vir
* Mem VIr
* Network V
  * VXLAN
* I/O
  * SR-IOV
* Container Vir
  * Docker and k8s

## S/H interface

* Virtio
* RDMA: network
* NVMe: memory access

## Network performance optimization

### Network layer

* Underlay: Physical infrastructure
* Overlay
* APP: EIP, CLB, etc...
  
### Importacne

* communciation
* complexity: DC-level, large-scale topo.
* failure hurts! Millions server x 1% failure ratio = 100 failures.
* clusterized application are deployed in larger scale -> performance requirment and EW trafifc.

Performant in multi-metric, stable, 

### Optimization

1. fundatmental physical or protocols

1. **Hardware acceleration & offloading**

    Offloading some protocols (eg. VXLAN ) or applications/transactions (OVS) on hardware.  
    What else (more fundamental or lowlevel) to offload?

1. **H/S interface**
    Middleware, hypervisor, os or some else.

1. **Transport control**

    Eg., CC.
    HPCC with INT is the best solution or a overkiller? HPCC requires endhost FPGA NIC, and less deployability.

    A network-based solution on security?

## Hardware 

Flexbility:
CPU > GPU > NPU/DPU > FPGA > ASIC

## Some cases

AWS EFA and SRD

* Out-of-order packet arrival: Reassembly in EFA
* ECMP: Packet level?
* lossy and fast drop-reaction


## Thoughts

Does security really make sense in HPDC?

<!-- ![Datavolume](Note-on-Cloud-Computing/image1-3.png) -->

<!-- {% asset_img image1-3.png Datavolume 100 100 %} -->
