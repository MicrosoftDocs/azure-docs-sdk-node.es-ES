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
ms.openlocfilehash: c91b8396dbfeb766887b650541044f7ce2e7bde6
ms.sourcegitcommit: 79213a25192d8913bf8ec16c19fbec6a8eb691f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Módulos de Azure Active Directory para Node.js

## <a name="overview"></a>Información general

> [!IMPORTANT]
> Se recomienda encarecidamente que utilice [Microsoft Graph](https://graph.microsoft.io/) en lugar de Graph API de Azure AD para tener acceso a recursos de Azure Active Directory. Nuestros esfuerzos de desarrollo ahora se centran en Microsoft Graph y no están previstas realizar mejoras adicionales para Graph API de Azure AD. Hay un número muy limitado de escenarios para los que Azure AD Graph API todavía podría ser adecuado. Para obtener más información, consulte la entrada de blog [Microsoft Graph o Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) del centro de desarrollo de Office.

[Azure Active Directory Authentication Library (ADAL) para Node.js](https://www.npmjs.com/package/adal-node) permite que las aplicaciones Node.js se autentiquen en AAD para acceder a los recursos web protegidos por AAD.

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-modules"></a>Instalación de los módulos npm

Utilice npm para instalar los módulos de administración o cliente de Azure Storage para Node.js.

```bash
npm install adal-node
```   

### <a name="example"></a>Ejemplo

En este ejemplo procedente del [ejemplo de credenciales de cliente](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) se muestra la autenticación entre servidores a través de las credenciales del cliente.

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

## <a name="samples"></a>Ejemplos

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
