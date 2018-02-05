---
title: System Requirements
summary: "Examples of systems running the Avalon Media System and simple statistics highlighting their throughput."
last_updated: January 2, 2017
sidebar: avalon6_sidebar
permalink: avalon6_system_requirements.html
folder: avalon6
---

There are no hard and fast system requirements for running Avalon, but you will want to choose your system depending on your collection size, expected usage, and desired responsiveness.  Below are several examples of systems currently running Avalon and simple statistics highlighting their throughput.

## Avalon Demo Server

* CPU: 4 cores
* RAM: 16 GB RAM
* Disk Space: 500 GB Disk
* This system uses Indiana University's Adobe Media Server instance.  

## Northwestern University Production System

Northwestern's Avalon System uses 4 machines (3 VM and 1 hardware): 

1. Avalon web application (VM):  
   * CPU: Xeon E5-2640 @ 2.50GHz, 2 cores, 4 threads
   * RAM:  8GB
   * Disk Space: 25GB local storage plus NFS storage
2. Fedora, MySQL and the Solr indexer (VM):  
3. Transcoding (Matterhorn) (physical box):  
   * CPU: Xeon E5-2690 v2 @ 3.00GHz 20 cores, 40 threads
   * RAM: 128GB
   * Disk Space: 4TB local storage plus NFS storage
4. Adobe Media Server:  External campus enterprise streaming server

## Indiana University Production System

1. Avalon web application, Fedora, Solr:
   * CPU: Intel(R) Xeon(R) CPU E5-2690 v2 @ 3.00GHz
   * RAM:  24GB
   * Disk Space: 40GB local storage plus 250GB NFS storage
2. MySQL:  External service
3. Transcoding (Matterhorn) (physical box):  
   * CPU: Intel(R) Xeon(R) CPU E5-2697 v2 @ 2.70GHz, 12 cores, 24 threads
   * RAM: 128GB
   * Disk Space: 12TB
4. Adobe Media Server:  External campus enterprise streaming server

## Distributed OVA

* CPU: 1 Virtual CPU
* RAM: 3GB
* Disk Space: 500GB (virtual, auto-expanding)

{% include links.html %}


