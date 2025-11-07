# General Threat Hunting KQL Guide - starter guide [work in progress] 

## Table of Contents

### Document Purpose
*Purpose*: This guide is provide a general framework at understand how to approach a threat hunt based on adversary intention.
### The Goal of Adversaries 
An adversary will exploit system vulnerabilites for different reasons - most commonly for financial, strategic, or ideological gain. Understanding how an adversary works to accomplish is essential. 
The two most common models on how to understand how an adversary works is the [Cyber Kill Chain](https://www.sentinelone.com/cybersecurity-101/threat-intelligence/cyber-kill-chain/) and the [MITRE ATT&CK Framework](https://attack.mitre.org/). 

*You can review these frameworks at the links above.*

The motivations of an adversary directly influence the methods they use. 


### The Threat Hunt Process:
**The Environment for these queries:** 
Queries can be modified to fit a particular type of environment or situation.
Network type: Flat 

### Microsoft Defender for Endpoint and KQL Queries:
This guide is using Microsoft Defender for Endpoint
**Device Identification - Process Count**
The scope of this can vary based on what we are looking for.  We may find one suspicious device or multiple.

*Table:* DeviceProcessEvents

*KQL Query:*

```kql
DeviceProcessEvents
| where Timestamp between (datetime() ..  datetime())    
| summarize ProcessCount = count()
| order by ProcessCount asc

//Can optionally use |where Timeestamp > ago(7d), or whatever the time period 
```


**Powershell Execution - Baseline KQL**
*Table:* DeviceProcessEvents

*KQL Query:*

```kql
DeviceProcessEvents
| where Timestamp > ago(30min)
| where FileName contains "powershell"
| project Timestamp, DeviceName, ActionType, InitiatingProcessCommandLine
| order by Timestamp asc 

```
**Suspicious network activity (DeviceNetworkEvents)**


**Persistence - Scheduled Tasks**

**Persistence - Registry**

**Defense evasion via Legacy Scripting**

**Lateral Movement - Discovery (Finding the intruders next target)**


**Check for Brute Force**

*Table:* DeviceSigninEvents

*KQL Query:*















