---
title: Note on Freeflow [NSDI'19]
tags:
  - RDMA
  - Data Center
  - Note
  - Virtulization
categories:
  - Notes
date: 2022-07-29 20:20:43
---


## Intro

A virtualization framework supporting container in RDMA network

## Motivation

* Containerized cloud provides lightweight *Isolation*, *Portability* and *Controllability* (Sec. Intro.)
* The kernel-bypass paradigm of RDMA puts difficulty on virtulization
  * `It is difficult to modify the control plane states (e.g., routes) in hardware in shared cloud environments, while it is also hard to control the data path since traffic directly goes between RAM and NIC via PCIe bus`
  * `when they run in shared clouds, they have to fundamentally eschew the performance benefits afforded by RDMA. Naturally, using dedicated clusters to run an application is, however, not cost efficient both for providers or for customers.`
  * Current public cloud (Azure, even AWS) usually sell nearly bare-metal RDMA instances. (What about Aliyun eRDMA?)
* Propose a tranparent and high-performance virtulization framework for containerized RDMA network.
  
## Background

### Virtulization

* *Host mode* networking containers 
  Containers use their host’s IP and port space, and communicate like an ordinary process in the host OS. Poor isolation and portability.
* *Virtual mode* networking.
  * VSwitch (hardware-offloaded or on software) on a physical device.
  * Strawman SR-IOV RDMA Vswitch has fundamental portability limitations (hard configuration migration).
    {% asset_img SR-IOVvirtulization.png SR-IOV RDMA Vswitch 100 100 %}

## Key design

### Overview

The key design can be easily get through the architecutre figure.

{% asset_img fig2.png Overveiw 100 100 %}

{% asset_img fig4.png Architecture 100 100 %}
<!-- ![Overveiw](fig2.png) -->


### Transparency

Key insight: Containers are essentially processes, and they can easily share resources like memory and file descriptors with FreeFlow.
Intercept the **verb** to consturct a **mapping** on the Freeflow.

### High-performance

Leverage a zero-copy design for throughput (§4.3), and a shared memory inter-process channel with CPU spinning for latency (§5.2 and Fig.6 in the paper)

### Communication between FFL and FFR

FFR intercepts the calls between Verbs library and NIC drivers by proposing a file descriptor lib.
Propose a *fast path* using polling with a dedicated CPU.

{% asset_img figtb.png Communication 100 100 %}

## Reviews

1. Propose a virtulization framework for container level RDMA
2. No security issues such as leaking the data or mem key to other containers.
3. No consideration on performance isolation. Only container-level isolation for portable control problem.