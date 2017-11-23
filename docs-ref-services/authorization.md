---
title: "Módulos de Azure Authorization para Node.js"
description: "Referencia de los módulos de Azure Authorization para Node.js"
keywords: Azure,SDK,API,Authorization, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="fb210-104">Módulos de Azure Authorization para Node.js</span><span class="sxs-lookup"><span data-stu-id="fb210-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fb210-105">Información general</span><span class="sxs-lookup"><span data-stu-id="fb210-105">Overview</span></span>

<span data-ttu-id="fb210-106">La autenticación/autorización de Azure App Service es una característica que proporciona una forma para que la aplicación lleve a cabo el inicio de sesión de usuarios sin necesidad de cambiar el código en el back-end de aplicación.</span><span class="sxs-lookup"><span data-stu-id="fb210-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="fb210-107">La autorización ofrece una forma fácil de proteger su aplicación y trabajar con datos por usuario.</span><span class="sxs-lookup"><span data-stu-id="fb210-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="fb210-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="fb210-108">Management package</span></span>

<span data-ttu-id="fb210-109">Utilice npm para instalar los módulos de Azure Authorization para Node.js.</span><span class="sxs-lookup"><span data-stu-id="fb210-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fb210-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="fb210-110">Install the npm module</span></span>

<span data-ttu-id="fb210-111">Instale el módulo npm de Azure Authorization.</span><span class="sxs-lookup"><span data-stu-id="fb210-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="fb210-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fb210-112">Example</span></span>

<span data-ttu-id="fb210-113">En este ejemplo se enumeran todas las asignaciones de roles para el grupo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="fb210-113">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="fb210-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="fb210-114">Samples</span></span>

<span data-ttu-id="fb210-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="fb210-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
