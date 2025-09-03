# Azure Workshop

This lab guide will walk you through creating a comprehensive Azure connectivity hub that manages all ingress and egress traffic for your deployment. You'll learn how to set up resource groups, virtual networks, Azure Bastion, and FortiGate firewalls in a high-availability configuration.

## What You'll Build

!!! forti "Lab Components"
    | Component | Description |
    |-----------|-------------|
    | **Resource Group** | Organize all Azure resources in a logical container |
    | **Virtual Network** | Create the network foundation with multiple subnets |
    | **Azure Bastion** | Secure RDP/SSH connectivity without public IPs |
    | **FortiGate HA Cluster** | High-availability firewall deployment with load balancing |

---

## Creating your "Connectivity Hub"

![](images/image1.jpeg)

Do you remember that old phrase "like finding a needle in a haystack"? It alludes to something that is hard to find. You will see that Azure has several resources available to you. A resource group is used to logically organize resources such as virtual machines, virtual networks, security appliances etc. Using a resource group makes it easier to organize and find your provisioned resources in Azure. We are going to start by creating a resource group for our connectivity hub that manages all ingress and egress traffic into our deployment.

## Prerequisites

Before starting this lab, ensure you have:

- An active Azure subscription with appropriate permissions
- Access to the Azure portal
- Basic understanding of networking concepts
- Familiarity with Azure resource management

## Lab Structure

This hands-on lab is organized into the following sections:

1. **[Resource Group Setup](00-resource-group.md)** - Set up the foundational container for all resources
2. **[Network Setup](01-network-infrastructure.md)** - Create virtual networks, subnets, and Azure Bastion
3. **[FortiGate Deployment](02-fortigate-ha.md)** - Deploy high-availability FortiGate firewalls with load balancers
4. **[Testing & Validation](03-architecture-validation.md)** - Test spoke networks, virtual machines, and connectivity flows
5. **[Configuration & Ops](04-advanced-operations.md)** - Advanced configuration, troubleshooting, and operational procedures

## Expected Outcomes

Upon completion of this lab, you will have:

- ✅ A fully functional Azure connectivity hub
- ✅ High-availability FortiGate firewall cluster
- ✅ Secure remote access via Azure Bastion
- ✅ Spoke network architecture for application deployment
- ✅ Comprehensive understanding of Azure network security

## Time Estimate

- **Total Lab Time**: 3-4 hours
- **Prerequisites Setup**: 15 minutes
- **Core Infrastructure**: 2-2.5 hours
- **Testing & Validation**: 45-60 minutes
- **Advanced Configuration**: 30-45 minutes

!!! tip "Lab Tips"
    - Take your time with each section and validate configurations before proceeding
    - Screenshots are provided throughout to help verify your progress
    - If you encounter issues, refer to the troubleshooting section in Advanced Operations

---

Ready to begin? Start with **[Resource Group Setup](00-resource-group.md)** to build your Azure connectivity hub foundation.
