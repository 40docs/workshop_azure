# Azure Workshop

This lab guide will walk you through creating a comprehensive Azure connectivity hub that manages all ingress and egress traffic for your deployment. You'll learn about resource groups, set up virtual networks, Azure Bastion, and FortiGate firewalls in a high-availability configuration.

## What You'll Build

!!! forti "Lab Components"
    | Component | Description |
    |-----------|-------------|
    | **Resource Group** | Organize all Azure resources in a logical container |
    | **Virtual Network** | Create the network foundation with multiple subnets |
    | **Azure Bastion** | Secure RDP/SSH connectivity without public IPs |
    | **FortiGate HA Cluster** | High-availability firewall deployment with load balancing |

---
## Prerequisites

Before starting this lab, ensure you have:

- Your pod assignment number from your instructor
- The supplied username and password for the Azure portal
- Basic understanding of networking concepts
- Familiarity with Azure resource management

## Lab Structure

This hands-on lab is organized into the following sections:

1. **[Create a Connectivity Hub](00-Task1-Create-the-Hub.md)** - Set up the foundational container for all resources
2. **[FortiGate Deployment](02-task2-fortigate-ha.md)** - Deploy high-availability FortiGate firewalls with load balancers
3. **[Testing & Validation](03Task3: Routing.md)** - Test spoke networks, virtual machines, and connectivity flows
4. **[Create Firewall Rules](04-Task 4:-Create-firewall-rules.md)** - Configure firewall policies and routes for north-south and east-west traffic

## Expected Outcomes

Upon completion of this lab, you will have:

- ✅ A fully functional Azure connectivity hub
- ✅ High-availability FortiGate firewall cluster
- ✅ Secure remote access via Azure Bastion
- ✅ Spoke network architecture for application deployment


## Time Estimate

- **Total Lab Time**: 3-4 hours
- **Prerequisites Setup**: 15 minutes
- **Core Infrastructure**: 2-2.5 hours
- **Testing & Validation**: 45-60 minutes

!!! tip "Lab Tips"
    - Take your time with each section and validate configurations before proceeding
    - Screenshots are provided throughout to help verify your progress

---

Ready to begin? Start with **[Create the Connectivity Hub](00-Task1-Create-the-Hub.md)** to build your Azure connectivity hub foundation.
