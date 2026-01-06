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
## Prerequisites

Before starting this lab, ensure you have:

- An active Azure subscription with appropriate permissions
- Access to the Azure portal
- Basic understanding of networking concepts
- Familiarity with Azure resource management

## Lab Structure

This hands-on lab is organized into the following sections:

1. **[Create a Connectivity Hub](00-Task1-Create-the-Hub.md)** - Set up the foundational container for all resources
3. **[FortiGate Deployment](02-task2-fortigate-ha.md)** - Deploy high-availability FortiGate firewalls with load balancers
4. **[Testing & Validation](03Task3: Routing.md)** - Test spoke networks, virtual machines, and connectivity flows
5. **[Configuration & Ops](05-advanced-operations.md)** - Advanced configuration, troubleshooting, and operational procedures

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


## Considerations

When setting up your FortiGate lab in Azure, it’s important to use a personal or test Azure subscription rather than your company’s production account. This avoids unnecessary costs, security risks, or accidental conflicts with corporate resources. Additionally, always remember to spin down or delete lab resources when you’re not actively using them—virtual machines, storage, and networking services continue to incur charges as long as they’re running, even if idle. This practice keeps your lab environment cost-efficient and prevents surprises on your bill.

---

Ready to begin? Start with **[Create the Connectivity Hub](00-Task1-Create-the-Hub.md)** to build your Azure connectivity hub foundation.
