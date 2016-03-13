<properties
   pageTitle="Custom scripts on Linux VMs using templates | Microsoft Azure"
   description="Automate Linux VM configuration tasks by using the Custom Script extension with Resource Manager templates"
   services="virtual-machines-linux"
   documentationCenter=""
   authors="kundanap"
   manager="timlt"
   editor=""
   tags="azure-resource-manager"/>

<tags
   ms.service="virtual-machines-linux"
   ms.devlang="na"
   ms.topic="article"
   ms.tgt_pltfrm="vm-linux"
   ms.workload="infrastructure-services"
   ms.date="11/01/2015"
   ms.author="kundanap"/>

# Using the Custom Script extension for Linux VMs With Azure Resource Manager templates

This article gives an overview of writing Azure Resource Manager templates with the Custom Script extension for bootstrapping workloads on a Linux VM.





Ever since its launch, the Custom Script extension has been used widely to configure workloads on both Windows and Linux VMs. With the introduction of Azure Resource Manager templates, users can now create a single template that not only provisions the VM but also configures the workloads on it.

## About Azure Resource manager templates

Azure Resource Manager template allow you to declaratively specify the Azure IaaS infrastructure in Json language by defining the dependencies between resources. For a detailed overview of Azure Resource Manager templates, see the following articles:

- [Resource Group Overview](../resource-group-overview.md)
- [Deploying Templates with Azure CLI](virtual-machines-linux-cli-manage.md)
- [Deploying Templates with Azure Powershell](virtual-machines-windows-ps-manage.md)

### Prerequistes

1. Download the Azure command line tools for your operating system from [here](https://azure.microsoft.com/downloads/).
2. If the scripts will be run on an existing VM, make sure VM Agent is enabled on the VM, if not follow [the Linux](virtual-machines-linux-classic-manage extensions.md) or [Windows](virtual-machines-windows-classic-manage extensions.md) guidance to install one.
3. Upload the scripts that you want to run on the VM to Azure Storage. The scripts can come from a single or multiple storage containers.
4. Alternatively the scripts can also be uploaded to a GitHub account.
5. The script should be authored in such a way that the entry script which is launched by the extension in turn launches other scripts.

## Using the custom script extension

For deploying with templates we use the same version of  Custom Script extension thats availale for Azure Service Management APIs. The extension supports the same parameters and scenarios like uploading files to Azure Storage account or Github location. The key difference while using with templates is the exact version of the extension should be specified, as opposed to specifying the version in majorversion.* format.

## Template example for a Linux VM

Define the following extension resource in the Resource section of the template

      {
    "type": "Microsoft.Compute/virtualMachines/extensions",
    "name": "MyCustomScriptExtension",
    "apiVersion": "2015-05-01-preview",
    "location": "[parameters('location')]",
    "dependsOn": ["[concat('Microsoft.Compute/virtualMachines/',parameters('vmName'))]"],
    "properties":
    {
      "publisher": "Microsoft.OSTCExtensions",
      "type": "CustomScriptForLinux",
      "typeHandlerVersion": "1.2",
      "settings": {
      "fileUris": [ "https: //raw.githubusercontent.com/Azure/azure-quickstart-templates/master/mongodb-on-ubuntu/mongo-install-ubuntu.sh                        ],
      "commandToExecute": "shmongo-install-ubuntu.sh"
      }
    }
    }
    
In the example above, replace the file URL and the file name with your own settings.

After authoring the template, you can deploy it using the Azure CLI.

Please refer to the example below for a complete sample of configuring applications on a VM using Custom Script extension.

* [Custom Script extension on a Linux VM](https://github.com/Azure/azure-quickstart-templates/blob/b1908e74259da56a92800cace97350af1f1fc32b/mongodb-on-ubuntu/azuredeploy.json/)
