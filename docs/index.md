# Azure Connectivity Hub Lab Guide

## Overview

This lab guide will walk you through creating a comprehensive Azure connectivity hub that manages all ingress and egress traffic for your deployment. You'll learn how to set up resource groups, virtual networks, Azure Bastion, and FortiGate firewalls in a high-availability configuration.

![](images/image1.jpeg)

Do you remember that old phrase "like finding a needle in a haystack"? It alludes to something that is hard to find. You will see that Azure has several resources available to you. A resource group is used to logically organize resources such as virtual machines, virtual networks, security appliances etc. Using a resource group makes it easier to organize and find your provisioned resources in Azure. 

We are going to start by creating a resource group for our connectivity hub that manages all ingress and egress traffic into our deployment.

## What You'll Build

<div class="grid cards" markdown>

-   :material-cloud-outline: **Resource Group**

    ---

    Organize all Azure resources in a logical container

-   :material-lan: **Virtual Network**

    ---

    Create the network foundation with multiple subnets

-   :material-security: **Azure Bastion**

    ---

    Secure RDP/SSH connectivity without public IPs

-   :material-shield-check: **FortiGate HA Cluster**

    ---

    High-availability firewall deployment with load balancing

</div>

## Prerequisites

Before starting this lab, ensure you have:

- An active Azure subscription with appropriate permissions
- Access to create resource groups and virtual networks
- Understanding of basic networking concepts
- FortiGate licensing tokens (FortiFlex)

## Estimated Time

- **Total Duration**: 2-3 hours
- **Resource Group Setup**: 15 minutes
- **Network Infrastructure**: 45 minutes  
- **FortiGate HA Deployment**: 60 minutes
- **Architecture Validation**: 30 minutes
- **Advanced Configuration**: 30 minutes

---

Ready to begin? Start with [Creating Your Resource Group](01-resource-group.md) to set up the foundation for your connectivity hub.