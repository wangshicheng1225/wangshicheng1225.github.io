---
title: Note on Justitia
date: 2022-07-29 16:26:15
tags: ["RDMA", "Data Center", "Note"]
categories:
- Notes
---

## Overview

Performance isolation (multi-tenancy) on the RDMA end-hosts.

<!-- Hardware-KBN (RDMA) has  -->
The poor Mlt-Tncy support on hardware results in **Resources Contention** and **Greedy Processing for High Utilization**.
The paper proposes a middleware on the driver to resolve it.



## Key observations 

The performance anomaly from multi-tenants of RDMA endhost cane be categorized by application types (*Throughput-*, *BW-*, and *Latency-*sensitive). The performance affect can be discussed by cases ($C_3^2$).

## Key notes

* RDMA network can be generalized into KBN or Lossless Network (SIGCOMM'21 paper)
* DCQCN provides network-angle fabric-level isolation, while the end-angel remains unobserverd.
* Provide inspiring scenarios assumptions about the sharing DC.

## Key Design Ideas

Refer to § 4.1.


