---
title: "Módulos de Azure Active Directory para Node.js"
description: "Referencia de los módulos de Azure Active Directory para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="6a4f9-103">Módulos de Azure Active Directory para Node.js</span><span class="sxs-lookup"><span data-stu-id="6a4f9-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6a4f9-104">Información general</span><span class="sxs-lookup"><span data-stu-id="6a4f9-104">Overview</span></span>

<span data-ttu-id="6a4f9-105">[Azure Active Directory Authentication Library (ADAL) para Node.js](https://www.npmjs.com/package/adal-node) permite que las aplicaciones Node.js se autentiquen en AAD para acceder a los recursos web protegidos por AAD.</span><span class="sxs-lookup"><span data-stu-id="6a4f9-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="6a4f9-106">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="6a4f9-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="6a4f9-107">Instalación de los módulos npm</span><span class="sxs-lookup"><span data-stu-id="6a4f9-107">Install the npm modules</span></span>

<span data-ttu-id="6a4f9-108">Utilice npm para instalar los módulos de administración o cliente de Azure Storage para Node.js.</span><span class="sxs-lookup"><span data-stu-id="6a4f9-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="6a4f9-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6a4f9-109">Example</span></span>

<span data-ttu-id="6a4f9-110">En este ejemplo procedente del [ejemplo de credenciales de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) se muestra la autenticación entre servidores a través de las credenciales del cliente.</span><span class="sxs-lookup"><span data-stu-id="6a4f9-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="6a4f9-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="6a4f9-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="6a4f9-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="6a4f9-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>