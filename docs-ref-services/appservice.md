---
title: Módulos de Azure App Service para Node.js
description: Referencia de los módulos de Azure App Service para Node.js
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a>Módulos de Azure App Service para Node.js

## <a name="overview"></a>Información general

Azure App Service es una oferta de plataforma como servicio (PaaS) de Microsoft Azure. Cree aplicaciones web y móviles para cualquier plataforma o dispositivo. Integre sus aplicaciones con soluciones SaaS, conecte con aplicaciones locales y automatice los procesos empresariales. Azure ejecuta las aplicaciones en máquinas virtuales totalmente administradas, con la elección de los recursos compartidos de máquinas virtuales o máquinas virtuales dedicadas.

App Service incluye las funcionalidades web y móviles que anteriormente se ofrecían por separado como Azure Websites y Azure Mobile Services. También incluye nuevas funcionalidades para automatizar procesos empresariales y hospedar las API en la nube. Como un servicio integrado único, App Service le permite crear distintos componentes, como sitios web, back-end de aplicación móvil, API de RESTful y procesos empresariales, en una única solución.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-package"></a>Instalación del paquete npm

Instale el módulo de Azure App Service para Node.js.

```bash
npm install azure-arm-website
```

### <a name="example"></a>Ejemplo

En este ejemplo se crea un sitio web en Azure con Node.js.

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>Ejemplos

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
