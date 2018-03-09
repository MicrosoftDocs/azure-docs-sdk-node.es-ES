---
title: "Módulos de Azure Authorization para Node.js"
description: "Referencia de los módulos de Azure Authorization para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="a8bb9-103">Módulos de Azure Authorization para Node.js</span><span class="sxs-lookup"><span data-stu-id="a8bb9-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a8bb9-104">Información general</span><span class="sxs-lookup"><span data-stu-id="a8bb9-104">Overview</span></span>

<span data-ttu-id="a8bb9-105">La autenticación/autorización de Azure App Service es una característica que proporciona una forma para que la aplicación lleve a cabo el inicio de sesión de usuarios sin necesidad de cambiar el código en el back-end de aplicación.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="a8bb9-106">La autorización ofrece una forma fácil de proteger su aplicación y trabajar con datos por usuario.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="a8bb9-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="a8bb9-107">Management package</span></span>

<span data-ttu-id="a8bb9-108">Utilice npm para instalar los módulos de Azure Authorization para Node.js.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a8bb9-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="a8bb9-109">Install the npm module</span></span>

<span data-ttu-id="a8bb9-110">Instale el módulo npm de Azure Authorization.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="a8bb9-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a8bb9-111">Example</span></span>

<span data-ttu-id="a8bb9-112">En este ejemplo se enumeran todas las asignaciones de roles para el grupo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a8bb9-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="a8bb9-113">Samples</span></span>

<span data-ttu-id="a8bb9-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a8bb9-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>