---
title: Azure networking capabilities using Microsoft Copilot in Azure (preview)
description: Learn how Microsoft Copilot in Azure can assist you in planning, designing, operating, and troubleshooting your Azure network with ease and efficiency.
ms.date: 11/08/2024
ms.topic: how-to
ms.service: copilot-for-azure
ms.custom:
  - ignite-2024
ms.author: sukishen
author: skishen505
---

# Azure networking capabilities using Microsoft Copilot in Azure (preview)

Copilot in Azure for networking can help you answer questions about Azure networking services and troubleshoot network connectivity issues. It offers contextual responses and actionable insights based on Microsoft's extensive networking knowledge and your Azure environment.

[!INCLUDE [scenario-note](includes/scenario-note.md)]
 
[!INCLUDE [preview-note](includes/preview-note.md)]

## Scenarios

The following Azure networking and network management skills are currently released in public preview.

[**Network product information queries**](#information) - This skill enables Copilot in Azure for Networking to answer questions about Azure Networking products and services using information from published documentation.

[**Network product selection and architecture guidance queries**](#selection) - This skill allows Copilot in Azure for Networking to assist with questions about product usage, product selection for your networking needs, and guidance on network planning, resilience, and migration from on-premises environments. 

In the current release, product selection guidance responses are limited to:
    
- Azure Load Balancer 
- Azure Firewall

And resiliency related queries are limited to the following networking services:

  - Azure Application Gateway
  - Azure Firewall
  - Azure Front Door
  - Azure Load Balancer
  - Azure NAT Gateway
  - Azure Private Endpoint
  - Azure Public IP
  - Azure Traffic Manager
  - Azure Virtual Network Gateways (ExpressRoute and VPN)

[**Network resource inventory, topology, traffic path queries**](#inventory) - This skill enables Copilot in Azure for Networking to discover customer network resources, network topology, and traffic paths from source to destination. Currently Copilot can respond to questions about network topology and traffic paths with topology maps and network connectivity graphs.

[**Network connectivity troubleshooting and service diagnostics queries**](#troubleshoot) - This skill enables Copilot in Azure for Networking to perform customer network troubleshooting across various connectivity, configuration, and environmental issues across your network data and control plane. Troubleshooting is supported at the network level and individual network service level. Copilot supports RBAC (Role-base access control) and only has access to resources that the user of the Copilot has.

## Sample prompts and examples

The following are some sample prompts and examples for each of the scenarios.

### <a name = "information"></a>Respond to network product information queries

Here are some sample prompts and responses for network product information queries:

- What are the different types of private network connectivity services offered by Azure?
- What is the difference between Azure Application Gateway and Azure Front Door?
- What is an Azure Firewall and how is it different from Azure Network Security Groups?

In this example, the prompt **"What is the difference between Application Gateway and Azure Front Door"** Copilot provides a detailed comparison between Azure Application Gateway and Azure Front Door.

:::image type="content" source="./media/network-management/compare-application-gateway-front-door.png" alt-text="Screenshot of Copilot describing the difference between Azure Application Gateway and Azure Front Door.":::

### <a name = "selection"></a>Respond to network product selection and architecture guidance queries

Here are some sample prompts and responses for network product selection and architecture guidance queries:

- Suggest an Azure Firewall SKU for my topology.
- Which type of load balancer should I use?
- Suggest a network architecture when migrating to Azure.
- Is my application gateway resilient?
- How to make my gateway highly available?

In this example, the prompt **"Suggest an Azure Firewall SKU for my topology"** Copilot asks you to provide more information about your use case and suggest the right Azure Firewall SKU.

:::image type="content" source="./media/network-management/firewall-sku-suggestion.png" alt-text="Screenshot of Copilot suggesting an Azure Firewall SKU for my topology.":::

In this example, the prompt **"Is my application gateway resilient?"** Copilot analyzes the selected Azure Application Gateway and suggests ways to make it more resilient.

:::image type="content" source="./media/network-management/application-gateway-resiliency.png" alt-text="Screenshot of Copilot analyzing the resiliency of an Azure Application Gateway." lightbox="./media/network-management/application-gateway-resiliency.png":::


### <a name = "inventory"></a>Network resource inventory, topology, and traffic path information

Here are some sample prompts and responses for network resource inventory, topology, and traffic path queries:

- What is the data path between my source VM and destination VM?
- Show me the data path between my VM and storage account.
- List all my Azure networking services in my subscription.
- How many flows are going through the gateway?
- How many VMs are behind the gateway?
- Help me discover my network inventory.
- How large is my network?
- Display the network resources in my subscription.

In this example, the prompt **"What is the data path between my source VM and destination VM?"** Copilot asks you to select the source and destination VMs by first presenting the resource selection choice screen from your subscription. Once you select the source and destination VMs, it then discovers the data path between the source and destination, drawing a connected graph showing all the network elements/services in the path.

:::image type="content" source="./media/network-management/trace-path-result.png" alt-text="Screenshot showing Copilot displaying the path your traffic takes from the source VM to the destination VM, including all traversed network services." lightbox="./media/network-management/trace-path-result.png":::

In this example, the prompt **"Troubleshoot my virtual network peerings"** Copilot asks you to select the Virtual Network and then analyzes the state, status, and configuration information of all the peered connections to see if there are any configuration or data path issues impacting the configured virtual network peerings and displays the findings.

:::image type="content" source="./media/network-management/troubleshooting-analysis.png" alt-text="Screenshot of Copilot analyzing the Virtual Network peering and displaying the findings." lightbox="./media/network-management/troubleshooting-analysis.png":::

### <a name = "troubleshoot"></a>Respond to network connectivity troubleshooting and service diagnostics queries

Here are some sample prompts and responses for network connectivity troubleshooting and service diagnostics queries:

- Why can't my VM connect to the internet?
- Why is my storage account not reachable from my VM?
- Why can’t I connect my on-premises VM to Azure VM?
- Why does the Azure portal show that my peering connection is established but we aren't receiving any traffic?
- Troubleshoot my virtual network peerings.
- What is the health status of my NIC and its public IP
- Why did the deployment of ExpressRoute Gateway fail?
- Is some NSG blocking my traffic to the internet from my VM in Azure?
- Why am I unable to send mail and SMTP is failing?
- Troubleshoot the virtual network to find any gateways and their associated public IPs that are missing a service tag.
- Who are the top 10 DDOS attackers from my VM
- How many times has my public IP been DDOS attacked in the past 14 days
- List the top DDOS attack vectors on my public IP
- [Has there been any malicious traffic intercepted by my Azure Firewall](/azure/firewall/firewall-copilot) 

 
In this example, the prompt **"Why can't my VM connect to the internet?"** Copilot asks you to select the source VM in Azure from where you're trying to connect to the internet. It then analyzes the path your traffic takes to the internet and identifies any configuration or data path issues that are blocking the traffic from reaching the internet.

Next, you're prompted to enter the internet destination IP address:

:::image type="content" source="./media/network-management/destination-ip-address-internet.png" alt-text="Screenshot of Copilot prompting the user to enter the  internet destination IP address for  troubleshooting." lightbox="./media/network-management/destination-ip-address-internet.png":::

Finally, Copilot analyzes the path and identifies issues impacting the connectivity:

:::image type="content" source="./media/network-management/troubeshoot-internet-result.png" alt-text="Screenshot of Copilot analyzing the path and identifying issues impacting the internet connectivity." lightbox="./media/network-management/troubeshoot-internet-result.png":::

In this example, the prompt **"Why can’t I connect from my on-premise VM to my Azure VM?"** Copilot asks you to select the ExpressRoute circuit that connects your on-premises site to Azure. It then analyzes the data path to your Azure VM to identify any configuration or data path issues that may be  blocking the traffic from reaching your Azure VM.

:::image type="content" source="./media/network-management/select-expressroute-circuit.png" alt-text="Screenshot of Copilot prompting the user to select the ExpressRoute circuit to their VM." lightbox="./media/network-management/select-expressroute-circuit.png":::

Next, Copilot asks you to select the destination VM and 
then analyzes the data path to the VM and displays the possible reasons for the connectivity issue:

:::image type="content" source="./media/network-management/expressroute-connectivity-result.png" alt-text="Screenshot of Copilot analyzing the data path to the VM and showing the possible reasons for the connectivity issue.":::

In this example, the prompt **"Why is my storage account not reachable from my VM?"** copilot asks you to select the source VM from where you're trying to connect to the storage account and the storage account this is unreachable. It then analyzes the path your traffic takes to the storage account and identify any configuration or data path issues that are blocking the traffic from reaching the storage account.


:::image type="content" source="./media/network-management/select-storage-account.png" alt-text="Screenshot showing Copilot prompting the user to select the storage account for connectivity troubleshooting." lightbox="./media/network-management/select-storage-account.png":::

Finally, Copilot analyzes the path and identifies issues impacting the connectivity to the storage account:

:::image type="content" source="./media/network-management/storage-account-analysis-result.png" alt-text="Screenshot showing Copilot analyzing the path and identifying issues impacting the connectivity to the storage account." lightbox="./media/network-management/storage-account-analysis-result.png":::

## Next steps
 
- Explore [capabilities](capabilities.md) of Microsoft Copilot in Azure.
- Learn more about [Azure Networking](/azure/networking/fundamentals/networking-overview).