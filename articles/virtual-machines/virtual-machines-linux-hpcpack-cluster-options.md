<properties
 pageTitle="Linux HPC Pack cluster options in the cloud | Microsoft Azure"
 description="Learn about options with Microsoft HPC Pack to create and manage a Linux high performance computing (HPC) cluster in the Azure cloud"
 services="virtual-machines-linux,cloud-services"
 documentationCenter=""
 authors="dlepow"
 manager="timlt"
 editor=""
 tags="azure-resource-manager,azure-service-management,hpc-pack"/>
<tags
ms.service="virtual-machines-linux"
 ms.devlang="na"
 ms.topic="article"
 ms.tgt_pltfrm="vm-linux"
 ms.workload="big-compute"
 ms.date="02/04/2016"
 ms.author="danlep"/>

# Options to create and manage a Linux high performance computing (HPC) cluster in Azure with Microsoft HPC Pack





Take advantage of Microsoft HPC Pack and Azure compute and infrastructure services to create and manage a cloud-based high performance computing (HPC) cluster. [HPC Pack](https://technet.microsoft.com/library/jj899572.aspx) is Microsoft's free HPC solution built on Microsoft Azure and Windows Server technologies and supports both Windows and Linux HPC workloads. A cloud-based HPC Pack cluster provides a cluster administrator or independent software vendor (ISV) a flexible, scalable platform to run compute-intensive applications while reducing investment in an on-premises compute cluster infrastructure.

## Run an HPC Pack cluster in Azure VMs

### Azure templates


* (Marketplace) [HPC Pack cluster for Linux workloads](https://azure.microsoft.com/marketplace/partners/microsofthpc/newclusterlinuxcn/)

* (Quickstart) [Create an HPC cluster with Linux compute nodes](https://azure.microsoft.com/documentation/templates/create-hpc-cluster-linux-cn/)


### Azure VM images

* [HPC Pack on Windows Server 2012 R2](https://azure.microsoft.com/marketplace/partners/microsoft/hpcpack2012r2onwindowsserver2012r2/)



### PowerShell deployment script

* [Create an HPC cluster with the HPC Pack IaaS deployment script](virtual-machines-linux-classic-hpcpack-cluster-powershell-script.md)

### Tutorials

* [Tutorial: Get started with Linux compute nodes in an HPC Pack cluster in Azure](virtual-machines-linux-classic-hpcpack-cluster.md)

* [Tutorial: Run NAMD with Microsoft HPC Pack on Linux compute nodes in Azure](virtual-machines-linux-classic-hpcpack-cluster-namd.md)

* [Tutorial: Run OpenFOAM with Microsoft HPC Pack on a Linux RDMA cluster in Azure](virtual-machines-linux-classic-hpcpack-cluster-openfoam.md)



### Cluster management

* [Submit jobs to an HPC Pack cluster in Azure](virtual-machines-windows-hpcpack-cluster-submit-jobs.md)



## Create RDMA clusters for MPI workloads

* [Tutorial: Run OpenFOAM with Microsoft HPC Pack on a Linux RDMA cluster in Azure](virtual-machines-linux-classic-hpcpack-cluster-openfoam.md)

* [Set up a Linux RDMA cluster to run MPI applications](virtual-machines-linux-classic-rdma-cluster.md)

