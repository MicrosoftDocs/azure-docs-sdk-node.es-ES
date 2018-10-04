---
title: Módulos de Azure Active Directory para Node.js
description: Referencia de los módulos de Azure Active Directory para Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48534493"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="2d217-103">Módulos de Azure Active Directory para Node.js</span><span class="sxs-lookup"><span data-stu-id="2d217-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2d217-104">Información general</span><span class="sxs-lookup"><span data-stu-id="2d217-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d217-105">Se recomienda encarecidamente que utilice [Microsoft Graph](https://graph.microsoft.io/) en lugar de Graph API de Azure AD para tener acceso a recursos de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2d217-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="2d217-106">Nuestros esfuerzos de desarrollo ahora se centran en Microsoft Graph y no están previstas realizar mejoras adicionales para Graph API de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2d217-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="2d217-107">Hay un número muy limitado de escenarios para los que Azure AD Graph API todavía podría ser adecuado. Para obtener más información, consulte la entrada de blog [Microsoft Graph o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) del centro de desarrollo de Office.</span><span class="sxs-lookup"><span data-stu-id="2d217-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="2d217-108">[Azure Active Directory Authentication Library (ADAL) para Node.js](https://www.npmjs.com/package/adal-node) permite que las aplicaciones Node.js se autentiquen en AAD para acceder a los recursos web protegidos por AAD.</span><span class="sxs-lookup"><span data-stu-id="2d217-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="2d217-109">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="2d217-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="2d217-110">Instalación de los módulos npm</span><span class="sxs-lookup"><span data-stu-id="2d217-110">Install the npm modules</span></span>

<span data-ttu-id="2d217-111">Utilice npm para instalar los módulos de administración o cliente de Azure Storage para Node.js.</span><span class="sxs-lookup"><span data-stu-id="2d217-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="2d217-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2d217-112">Example</span></span>

<span data-ttu-id="2d217-113">En este ejemplo procedente del [ejemplo de credenciales de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) se muestra la autenticación entre servidores a través de las credenciales del cliente.</span><span class="sxs-lookup"><span data-stu-id="2d217-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2d217-114">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="2d217-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="2d217-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="2d217-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
