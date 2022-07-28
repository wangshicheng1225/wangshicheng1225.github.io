---
title: Note on Survey of Security in HPC Cloud
date: 2022-07-28 13:49:56
tags:
categories:
---

## HPC vs. Vanilla DC

HPC also has the trend of becoming cloud-like: `(e.g., resource pooling, rapid elasticity, on-demand self-service), or interacting with the cloud (e.g., bursting), security will become a greater concern at an accelerating rate. (Howard, 2020, p. 19)`

More harsh environment in HPC, and more violent contradiction between **performance** and **security.**

`As we increasingly see cases of pure HPC bare metal infrastructure interacting with the cloud (such as I/O interfaces and processes), it brings along more ‘opportunities’ for malicious attacks. While this should be considered and integrated into security policies and guidelines, performance faces the peril of being compromised as precious resources are carved out for security protocols and processes.(Howard, 2020, p. 19)`

## Key findings

- Deep concerns about the cyber threats (66.7%)
- Budgetary constraints and Lack of awareness hinders security practices.
- `About half of the respondents are offering cloud-based HPC services.(Howard, 2020, p. 19)`
- Slightly more than 50% of respondents’ organizations do not tap industry guidelines / standards for cybersecurity.
- A dominating concern specific to the HPC sector impeding cloud adoption is performance tradeoff (80%). Interestingly, only 10% of respondents cited not meeting security requirements as a barrier to cloud adoption.

## Specific findings

- Only 1-5% performance loss is acceptable when improving the security.
- Security measurements are **insufficient?**  
  - most put security measurements on  external communication (e.g., FW/IDS)
- Half are offering **cloud-based HPC services.**
- Cloud is becoming a trend?

  - reasons putting on cloud: 1. “Industry guidelines for HPC Cloud” (Howard, 2020, p. 19) . 2.“Technical Expertise to deploy into the cloud” (Howard, 2020, p. 19)
- “The availability of cybersecurity standards for HPC workloads in the cloud and industry guidelines for HPC cloud ranks highly (~75%) in influencing organizations to adopt cloud.” (Howard, 2020, p. 19)
- 80% thought it is necessary to seucre the HPC Infra.

## Conclusions

- HPC cloud is becoming a trend
  - cost/guidelines/…..
- The requirement on the performance and cost of security produces is more harsh
- Security issues are well recognized.
- Are current security practices **sufficient?**
