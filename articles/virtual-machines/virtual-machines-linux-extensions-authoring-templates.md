<properties
   pageTitle="Authoring templates with Linux VM extensions | Microsoft Azure"
   description="Learn about authoring Azure Resource Manager templates with extensions for Linux VMs"
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
   ms.date="09/01/2015"
   ms.author="kundanap"/>

# Authoring Azure Resource Manager templates with Linux VM extensions
## Overview of Azure Resource Manager templates

Azure Resource Manager templates allow you to declaratively specify the Azure IaaS infrastructure in Json language by defining the dependencies between resources. For a detailed overview of Azure Resource Manager Templates, please refer to the article below:

[Resource Group Overview](../resource-group-overview.md)

## Sample template snippet for VM extensions
Deploying VM extensions as part of an Azure Resource Manager template requires you to declaratively specify the extension configuration in the template.
Here is the format for specifying the extension configuration.

      {
      "type": "Microsoft.Compute/virtualMachines/extensions",
      "name": "MyExtension",
      "apiVersion": "2015-05-01-preview",
      "location": "[parameters('location')]",
      "dependsOn": ["[concat('Microsoft.Compute/virtualMachines/',parameters('vmName'))]"],
      "properties":
      {
      "publisher": "Publisher Namespace",
      "type": "extension Name",
      "typeHandlerVersion": "extension version",
      "settings": {
      // Extension specific configuration goes in here.
      }
      }
      }

As you can see from the above, the extension template contains two main parts:

1. Extension name, publisher and version
2. Extension Configuration.

## Identifying the publisher, type, and typeHandlerVersion for any extension

Azure VM extensions are published by Microsoft and trusted 3rd party publishers and each extension is uniquely identified by its publisher,type and the typeHandlerVersion. These can be determined as following:  

From Azure CLI, run the following commnad:

      Azure VM extension list

This command returns the publisher name, extension name and version as following:

      Publisher                   : Microsoft.Azure.Extensions  
      ExtensionName               : DockerExtension
      Version                     : 1.0

These three properties map to "publisher", "type", and "typeHandlerVersion" respectively in the above template snippet.

>[AZURE.NOTE]It's always recommended to use the latest extension version to get the most updated functionality.

## Identifying the schema for the extension configuration parameters

The next step with authoring an extension template is to identify the format for providing configuration parameters. Each extension supports its own set of parameters.

To look at sample configurations for Linux extensions, click the documentation for see [Linux eExtensions samples](virtual-machines-linux-extensions-configuration-samples.md).

Please refer to the following to get a fully complete template with VM Extensions.

[Custom script extension on a Linux VM](https://github.com/Azure/azure-quickstart-templates/blob/b1908e74259da56a92800cace97350af1f1fc32b/mongodb-on-ubuntu/azuredeploy.json/)

After authoring the template, you can deploy it using the Azure CLI.
