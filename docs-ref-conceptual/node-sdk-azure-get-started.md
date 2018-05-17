---
title: Introducción a los módulos de Azure para Node.js
description: Empezar a trabajar con la autenticación y la administración de recursos con los módulos de Azure para Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="b8f4f-103">Introducción a los módulos de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="b8f4f-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="b8f4f-104">Esta guía le ayudará a instalar los módulos de Node.js de Azure, a autenticarse en Azure con una entidad de servicio y a ejecutar código de ejemplo que cree recursos en su suscripción de Azure y permita conectarse a los servicios en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8f4f-105">requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b8f4f-105">Prerequisites</span></span>

- <span data-ttu-id="b8f4f-106">Una cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-106">An Azure account.</span></span> <span data-ttu-id="b8f4f-107">Si no tiene una, [obtenga una versión de evaluación gratuita](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="b8f4f-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="b8f4f-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="b8f4f-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="b8f4f-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) o [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="b8f4f-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="b8f4f-110">Preparación del entorno</span><span class="sxs-lookup"><span data-stu-id="b8f4f-110">Prepare your environment</span></span>

<span data-ttu-id="b8f4f-111">Cree un nuevo proyecto en un directorio vacío e instale los siguientes módulos npm:</span><span class="sxs-lookup"><span data-stu-id="b8f4f-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="b8f4f-112">Configuración de la autenticación</span><span class="sxs-lookup"><span data-stu-id="b8f4f-112">Set up authentication</span></span>

<span data-ttu-id="b8f4f-113">Las aplicaciones Node.js tienen que leer y crear permisos en su suscripción de Azure para ejecutar el código de ejemplo de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="b8f4f-114">Cree una entidad de servicio y configure la aplicación para que se ejecute con sus credenciales.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="b8f4f-115">Las entidades de servicio son una cuenta no interactiva asociada con su identidad a la que conceder únicamente los privilegios que la aplicación necesita para la ejecución.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="b8f4f-116">[Cree una entidad de servicio mediante la CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) y capture la salida.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="b8f4f-117">Debe proporcionar una [contraseña segura](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) en el argumento de contraseña en lugar de `MY_SECURE_PASSWORD`.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="b8f4f-118">Exporte los valores de *appId*, *password* y *tenant* como variables de entorno:</span><span class="sxs-lookup"><span data-stu-id="b8f4f-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="b8f4f-119">Obtenga el identificador de su suscripción con [az account show](https://docs.microsoft.com/cli/azure/account#show).</span><span class="sxs-lookup"><span data-stu-id="b8f4f-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="b8f4f-120">Exporte el identificador de suscripción como una variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="b8f4f-121">Creación de una máquina virtual con Linux</span><span class="sxs-lookup"><span data-stu-id="b8f4f-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="b8f4f-122">Cree un nuevo archivo *createVM.js* en el directorio actual con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="b8f4f-123">Actualice el valor de `adminPass` con una contraseña válida.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-123">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="b8f4f-124">Ejecute el código desde la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="b8f4f-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="b8f4f-125">Una vez completado el código, obtenga la dirección IP de la nueva máquina virtual e inicie sesión con SSH utilizando el valor de `adminPass` desde el código.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="b8f4f-126">Escritura de un blob en Azure Storage</span><span class="sxs-lookup"><span data-stu-id="b8f4f-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="b8f4f-127">Cree un nuevo archivo *uploadFile.js* en el directorio actual con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="b8f4f-128">Ejecute el comando y después copie y pegue la dirección URL desde la salida en el explorador web para ver el archivo en Azure Storage:</span><span class="sxs-lookup"><span data-stu-id="b8f4f-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="b8f4f-129">Limpieza de recursos</span><span class="sxs-lookup"><span data-stu-id="b8f4f-129">Clean up resources</span></span>

<span data-ttu-id="b8f4f-130">Elimine el grupo de recursos para quitar los recursos creados en esta guía.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="b8f4f-131">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="b8f4f-131">Next steps</span></span>

<span data-ttu-id="b8f4f-132">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="b8f4f-133">Referencia</span><span class="sxs-lookup"><span data-stu-id="b8f4f-133">Reference</span></span> 

<span data-ttu-id="b8f4f-134">Hay una [referencia](/javascript/api/overview/azure/) disponible para todos los paquetes.</span><span class="sxs-lookup"><span data-stu-id="b8f4f-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="b8f4f-135">Obtener ayuda y proporcionar comentarios</span><span class="sxs-lookup"><span data-stu-id="b8f4f-135">Get help and give feedback</span></span>

<span data-ttu-id="b8f4f-136">Puede publicar preguntas a la comunidad en [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span><span class="sxs-lookup"><span data-stu-id="b8f4f-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="b8f4f-137">Puede informar sobre errores y abrir incidencias en los módulos de Azure para Node.js en el [GitHub del proyecto](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="b8f4f-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

