---
title: Creación de una entidad de servicio de Azure con Node.js
description: Aprenda a usar la autenticación de entidad de servicio a través de Node.js.
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406541"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="96be7-103">Creación de una entidad de servicio de Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="96be7-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="96be7-104">Cuando una aplicación necesite acceder a recursos, puede configurar una identidad para la aplicación y autenticarla con sus propias credenciales.</span><span class="sxs-lookup"><span data-stu-id="96be7-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="96be7-105">Esta identidad se conoce como *entidad de servicio*.</span><span class="sxs-lookup"><span data-stu-id="96be7-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="96be7-106">En resumen, puede crear claves para su cuenta de Azure Active Directory que proporciona a los SDK para autenticarse, en lugar de requerir la intervención del usuario o el nombre de usuario/contraseña.</span><span class="sxs-lookup"><span data-stu-id="96be7-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="96be7-107">El enfoque de la entidad de servicio le permite:</span><span class="sxs-lookup"><span data-stu-id="96be7-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="96be7-108">Asignar permisos a la identidad de la aplicación que sean diferentes a los suyos propios.</span><span class="sxs-lookup"><span data-stu-id="96be7-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="96be7-109">Normalmente, estos permisos están restringidos a exactamente aquello que la aplicación debe hacer.</span><span class="sxs-lookup"><span data-stu-id="96be7-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="96be7-110">Usar un certificado para la autenticación al ejecutar un script desatendido.</span><span class="sxs-lookup"><span data-stu-id="96be7-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="96be7-111">En este tema se muestran tres técnicas para crear una entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="96be7-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="96be7-112">Azure Portal</span><span class="sxs-lookup"><span data-stu-id="96be7-112">Azure portal</span></span>
- <span data-ttu-id="96be7-113">CLI de Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="96be7-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="96be7-114">SDK de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="96be7-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="96be7-115">Creación de una entidad de servicio con Azure Portal</span><span class="sxs-lookup"><span data-stu-id="96be7-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="96be7-116">Siga los pasos descritos en el tema [Uso del portal para crear una aplicación de Azure Active Directory y una entidad de servicio con acceso a los recursos](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) para generar la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="96be7-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="96be7-117">Creación de una entidad de servicio con la CLI de Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="96be7-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="96be7-118">La creación de una entidad de servicio mediante la [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) puede realizarse mediante los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="96be7-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="96be7-119">Descargue la [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="96be7-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="96be7-120">Abra una ventana del terminal.</span><span class="sxs-lookup"><span data-stu-id="96be7-120">Open a terminal window.</span></span>

3. <span data-ttu-id="96be7-121">Escriba el comando siguiente para iniciar el proceso de inicio de sesión:</span><span class="sxs-lookup"><span data-stu-id="96be7-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="96be7-122">Al llamar a `az login` da como resultado una dirección URL y un código.</span><span class="sxs-lookup"><span data-stu-id="96be7-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="96be7-123">Vaya a la dirección URL especificada, escriba el código e inicie sesión con su identidad de Azure (esto puede ocurrir automáticamente si ya inició sesión).</span><span class="sxs-lookup"><span data-stu-id="96be7-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="96be7-124">Después, podrá tener acceso a su cuenta a través de la CLI.</span><span class="sxs-lookup"><span data-stu-id="96be7-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="96be7-125">Obtenga los identificadores de suscripción y de inquilino:</span><span class="sxs-lookup"><span data-stu-id="96be7-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="96be7-126">El siguiente texto muestra un ejemplo de la salida:</span><span class="sxs-lookup"><span data-stu-id="96be7-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="96be7-127">**Anote el identificador de suscripción, pues lo utilizará en el paso 7.**</span><span class="sxs-lookup"><span data-stu-id="96be7-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="96be7-128">Cree una entidad de servicio para obtener un objeto JSON que contenga las otras partes de información que necesita para autenticarse con Azure.</span><span class="sxs-lookup"><span data-stu-id="96be7-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="96be7-129">El siguiente texto muestra un ejemplo de la salida:</span><span class="sxs-lookup"><span data-stu-id="96be7-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="96be7-130">**Anote los valores de inquilino, nombre y contraseña, ya que se van a utilizar en el paso 7.**</span><span class="sxs-lookup"><span data-stu-id="96be7-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="96be7-131">Configure las variables de entorno: reemplace los marcadores de posición &lt;Id. suscripción>, &lt;inquilino>, &lt;nombre> y &lt;contraseña> con los valores obtenidos en los pasos 4 y 5.</span><span class="sxs-lookup"><span data-stu-id="96be7-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="96be7-132">**Con Bash**</span><span class="sxs-lookup"><span data-stu-id="96be7-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="96be7-133">**Uso de PowerShell**</span><span class="sxs-lookup"><span data-stu-id="96be7-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="96be7-134">Creación de una entidad de servicio con el SDK de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="96be7-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="96be7-135">Para crear mediante programación una entidad de servicio con JavaScript, use el [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="96be7-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="96be7-136">Uso de la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="96be7-136">Using the service principal</span></span>

<span data-ttu-id="96be7-137">Cuando tenga una entidad de servicio, el siguiente fragmento de código JavaScript muestra cómo utilizar las claves de entidad de servicio para autenticarse con el SDK de Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="96be7-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="96be7-138">Modifique los siguientes marcadores de posición: &lt;clientId o appId>, &lt;secret o password> y &lt;domain o tenant>,</span><span class="sxs-lookup"><span data-stu-id="96be7-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
