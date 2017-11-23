---
title: "Módulos de Azure para Node.js"
description: "Introducción a los módulos de servicio y de administración de Azure para Node.js"
keywords: "Azure, Node.js, SDK, API, administración, cliente, servicios"
author: TomArcher
ms.author: tarcher
manager: douge
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 56dc4f4f36d4e0e9a2d40b38ff8f0b1f9690818c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-modules-for-nodejs"></a><span data-ttu-id="f8f5a-104">Módulos de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="f8f5a-104">Azure modules for Node.js</span></span>

<span data-ttu-id="f8f5a-105">Administre los recursos de Azure y conecte con los servicios desde sus aplicaciones Node.js con los módulos de Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-105">Manage Azure resources and connect to services from your Node.js applications with the Azure modules for Node.js.</span></span> <span data-ttu-id="f8f5a-106">El código está disponible como [módulos npm](node-sdk-azure-install.md) para su uso en los proyectos.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-106">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="f8f5a-107">Administración de recursos de Azure</span><span class="sxs-lookup"><span data-stu-id="f8f5a-107">Manage Azure resources</span></span>

<span data-ttu-id="f8f5a-108">Los módulos de administración se utilizan para crear y consultar los recursos de las aplicaciones o para crear las propias herramientas de automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-108">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="f8f5a-109">Por ejemplo, para crear una máquina virtual Linux usando una interfaz de red existente, debe escribir el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="f8f5a-109">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="f8f5a-110">Revise las [instrucciones de instalación](node-sdk-azure-install.md) para obtener una lista completa de los módulos y el [artículo de introducción](node-sdk-azure-get-started.md) para configurar la autenticación y ejecutar código de ejemplo para crear y actualizar los recursos en su propia suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-110">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="f8f5a-111">Conexión a los servicios de Azure</span><span class="sxs-lookup"><span data-stu-id="f8f5a-111">Connect to Azure services</span></span>

<span data-ttu-id="f8f5a-112">Además de utilizar los módulos de Azure para crear y administrar recursos en Azure, también puede utilizar paquetes para conectarse a los servicios en la nube de Azure en las aplicaciones y a utilizarlos.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-112">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="f8f5a-113">Por ejemplo, puede actualizar una tabla de SQL Database o cargar archivos en Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-113">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="f8f5a-114">Seleccione el paquete que necesita para un servicio determinado en la [lista completa](node-sdk-azure-install.md) y visite el [Centro para desarrolladores de Node.js](https://azure.microsoft.com/develop/nodejs/) para ver tutoriales y código de ejemplo para aprender a usar los módulos en las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-114">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [Node.js developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="f8f5a-115">Por ejemplo, para imprimir el contenido de cada blob en un contenedor de Azure Storage:</span><span class="sxs-lookup"><span data-stu-id="f8f5a-115">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="f8f5a-116">Código de ejemplo y referencia</span><span class="sxs-lookup"><span data-stu-id="f8f5a-116">Sample code and reference</span></span>

<span data-ttu-id="f8f5a-117">Los ejemplos siguientes incluyen las tareas comunes con los módulos de administración de Azure y tienen código listo para usar en sus propias aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="f8f5a-117">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="f8f5a-118">Máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="f8f5a-118">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="f8f5a-119">Aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="f8f5a-119">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="f8f5a-120">SQL Database</span><span class="sxs-lookup"><span data-stu-id="f8f5a-120">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="f8f5a-121">Hay disponible una [referencia](https://docs.microsoft.com/nodejs/api) para todos los módulos tanto de los módulos de servicio como de las bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="f8f5a-121">A [reference](https://docs.microsoft.com/nodejs/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="f8f5a-122">Las nuevas características, cambios importantes e instrucciones de migración desde versiones anteriores están disponibles en las [notas de la versión](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="f8f5a-122">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>