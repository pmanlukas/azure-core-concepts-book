# Compute

Compute is a major part of the IaaS layer offered by Azure. Currently IaaS on Azure is divided into compute, networking and storage and some additional services for these three areas. In compute we offer Virtual Machines as well as Container Instances, a new kind of compute offering explicitly designed to run containers. In this chapter we talk about the details of compute on Azure, explain how VMs and CIs on Azure work and show you the best resources to get started.

## Compute offerings on Azure

## High Availability for compute on Azure

One very important aspect of compute in cloud solutions is their high availability. It is often business critical, that compute ressources are always available and can handle unplanned events like crashes or bugs. Azure has two kinds of events: planned and unplanned events. Planned Maintenance events are periodic updates made by Microsoft to the underlying Azure platform to improve overall reliability, performance, and security of the platform infrastructure that your virtual machines run on. Most of these updates are performed without any impact upon your Virtual Machines or Cloud Services (see VM Preserving Maintenance). While the Azure platform attempts to use VM Preserving Maintenance in all possible occasions, there are rare instances when these updates require a reboot of your virtual machine to apply the required updates to the underlying infrastructure [1](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability).

Unplanned maintainance events occur if Azure detects or predicts the failure of hardware or when bugs, like spectre, occur, that require a fast reaction, like an update of the hypervisor. Such 

## Storage for compute on Azure

## Helpful resources

[Azure Compute Decision Tree](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree)
[Azure Compute Documentation](https://docs.microsoft.com/en-us/azure/virtual-machines/)
[Azure Availability Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability)