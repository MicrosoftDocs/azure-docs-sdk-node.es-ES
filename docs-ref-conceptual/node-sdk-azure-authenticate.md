---
title: "Autenticación con los módulos de administración de Azure para Node.js"
description: "Autenticación con una entidad de servicio en los módulos de administración de Azure para Node.js"
keywords: "Azure, Node, SDK, API, autenticación, active directory, entidad de servicio"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="88b86-104">Autenticación con los módulos de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="88b86-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="88b86-105">Todas las API de servicio requieren autenticación a través de un objeto `credentials` cuando se crea una instancia de él.</span><span class="sxs-lookup"><span data-stu-id="88b86-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="88b86-106">Hay tres maneras de autenticar y crear las credenciales necesarias mediante el SDK de Azure para Node.js:</span><span class="sxs-lookup"><span data-stu-id="88b86-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="88b86-107">Autenticación básica</span><span class="sxs-lookup"><span data-stu-id="88b86-107">Basic authentication</span></span>
- <span data-ttu-id="88b86-108">Inicio de sesión interactivo</span><span class="sxs-lookup"><span data-stu-id="88b86-108">Interactive login</span></span>
- <span data-ttu-id="88b86-109">Autenticación de entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="88b86-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="88b86-110">Autenticación básica</span><span class="sxs-lookup"><span data-stu-id="88b86-110">Basic authentication</span></span>

<span data-ttu-id="88b86-111">Para autenticar mediante programación mediante sus credenciales de la cuenta de Azure, use la función `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="88b86-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="88b86-112">El siguiente fragmento de código de JavaScript muestra cómo utilizar la autenticación básica con credenciales almacenadas como variables de entorno.</span><span class="sxs-lookup"><span data-stu-id="88b86-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="88b86-113">Inicio de sesión interactivo</span><span class="sxs-lookup"><span data-stu-id="88b86-113">Interactive login</span></span>

<span data-ttu-id="88b86-114">El inicio de sesión interactivo proporciona un vínculo y un código que permita a los usuarios autenticarse desde un explorador.</span><span class="sxs-lookup"><span data-stu-id="88b86-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="88b86-115">Utilice este método cuando el mismo script utiliza varias cuentas o cuando se prefiere la intervención del usuario.</span><span class="sxs-lookup"><span data-stu-id="88b86-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="88b86-116">Autenticación de entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="88b86-116">Service principal authentication</span></span>

<span data-ttu-id="88b86-117">El [inicio de sesión interactivo](#interactive-login) es la manera más sencilla de autenticarse.</span><span class="sxs-lookup"><span data-stu-id="88b86-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="88b86-118">Sin embargo, al usar el SDK de Node.js, puede que desee utilizar la autenticación de entidad de servicio en lugar de proporcionar sus credenciales de cuenta.</span><span class="sxs-lookup"><span data-stu-id="88b86-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="88b86-119">En el tema [Creación de una entidad de servicio de Azure con Node.js](./node-sdk-azure-authenticate-principal.md) se explican varias técnicas para crear (y utilizar) una entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="88b86-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 