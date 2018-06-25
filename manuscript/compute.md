# Compute

Compute is a major part of the IaaS layer offered by Azure. Currently IaaS on Azure is divided into compute, networking and storage and some additional services for these three areas. In compute we offer Virtual Machines as well as Container Instances, a new kind of compute offering explicitly designed to run containers. In this chapter we talk about the details of compute on Azure, explain how VMs and CIs on Azure work and show you the best resources to get started.

## Compute offerings on Azure

## High Availability for compute on Azure

One very important aspect of compute in cloud solutions is their high availability. It is often business critical, that compute ressources are always available and can handle unplanned events like crashes or bugs. Azure has three kinds of events: unexpected,planned and unplanned events. 

Planned Maintenance events are periodic updates made by Microsoft to the underlying Azure platform to improve overall reliability, performance, and security of the platform infrastructure that your virtual machines run on. Most of these updates are performed without any impact upon your Virtual Machines or Cloud Services (see VM Preserving Maintenance). While the Azure platform attempts to use VM Preserving Maintenance in all possible occasions, there are rare instances when these updates require a reboot of your virtual machine to apply the required updates to the underlying infrastructure [1](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability).

Unplanned maintainance events occur if Azure detects or predicts the failure of hardware or when bugs, like spectre, occur, that require a fast reaction, like an update of the hypervisor. When the platform predicts a failure, it will issue an unplanned hardware maintenance event to reduce the impact to the virtual machines hosted on that hardware. Azure uses Live Migration technology to migrate the Virtual Machines from the failing hardware to a healthy physical machine. Live Migration is a VM preserving operation that only pauses the Virtual Machine for a short time. Memory, open files, and network connections are maintained, but performance might be reduced before and/or after the event. In cases where Live Migration cannot be used, the VM will experience Unexpected Downtime, as described below [1](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability). 

Unexpected events are crashes of the underlying compute, storage or networking infrastructure, that affect your compute ressources. Such events can also occur on Azure. If your service crashes because of such an event, than Azure automatically tries to migrate the ressources to healty hardware and thereby heals the service. To ensure the security of your services in cases of a crash of a whole data center or region, Azure offers other solutions like Availability Zones or Azure Desaster Recovery. 

Azure Availability Sets allow you to ensure the HA of your VMs in Azure. They manage the availability in the case of unplannend or unexpected events by using Fault domains. A Fault domain ensures, that VMs inside a Fault Domain share the same networking and power supply. To ensure the HA of the VMs in a Availability Set, the VMs are spread over different Fault Domains, so that in the case of a crash, at least one VM is still available. To ensure, that during an update of the VMs, not all VMs are rebooted at the same time, there is the concept of Update domains. All VMs inside an update domain are restarted at the same time. It also ensures, that only one update domain is restarted at a time, which also ensures that during maintainance events, at least one VM is available. 

Combine the Azure Load Balancer with an availability set to get the most application resiliency. The Azure Load Balancer distributes traffic between multiple virtual machines. For our Standard tier virtual machines, the Azure Load Balancer is included. Not all virtual machine tiers include the Azure Load Balancer. For more information about load balancing your virtual machines, see Load Balancing virtual machines.If the load balancer is not configured to balance traffic across multiple virtual machines, then any planned maintenance event affects the only traffic-serving virtual machine, causing an outage to your application tier. Placing multiple virtual machines of the same tier under the same load balancer and availability set enables traffic to be continuously served by at least one instance [1](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability).

It should be mentioned, that you should use more than one Availability Set, if you are using your VMs for different purposes, like for databases, web servers, etc. While placing your virtual machines into an availability set does not protect your application from operating system or application-specific failures, it does limit the impact of potential physical hardware failures, network outages, or power interruptions. Also keep in mind, that resoureces can only be assigend to an Availability Set at creation and that this can not be changed later. We also offer [SLAs](https://azure.microsoft.com/en-us/support/legal/sla/virtual-machines/v1_0/) on Azure VMs of 99.95% and [SLAs](https://azure.microsoft.com/en-us/support/legal/sla/managed-disks/v1_0/) for the managed disks of VMs. Also VMs and their attached disks are separated and both have their own availability. So if a VM crashes, its disks will still be online and vice versa. Therefore, it is essential, that you plan the availability sets, fault and update domains already while architecting your Azure solutions.

If you need to ensure, that your VMs are also available, if a data center fails, than Azure [Availability Zones](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview) are the right offer for you.

## Scaling of compute on Azure

## Storage for compute on Azure

## Helpful resources

[Azure Compute Decision Tree](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree)
[Azure Compute Documentation](https://docs.microsoft.com/en-us/azure/virtual-machines/)
[Azure Availability Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability)