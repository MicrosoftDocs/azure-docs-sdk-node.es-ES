---
title: "Módulos de Azure App Service para Node.js"
description: "Referencia de los módulos de Azure App Service para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="dfc15-103">Módulos de Azure App Service para Node.js</span><span class="sxs-lookup"><span data-stu-id="dfc15-103">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dfc15-104">Información general</span><span class="sxs-lookup"><span data-stu-id="dfc15-104">Overview</span></span>

<span data-ttu-id="dfc15-105">Azure App Service es una oferta de plataforma como servicio (PaaS) de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="dfc15-105">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="dfc15-106">Cree aplicaciones web y móviles para cualquier plataforma o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dfc15-106">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="dfc15-107">Integre sus aplicaciones con soluciones SaaS, conecte con aplicaciones locales y automatice los procesos empresariales.</span><span class="sxs-lookup"><span data-stu-id="dfc15-107">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="dfc15-108">Azure ejecuta las aplicaciones en máquinas virtuales totalmente administradas, con la elección de los recursos compartidos de máquinas virtuales o máquinas virtuales dedicadas.</span><span class="sxs-lookup"><span data-stu-id="dfc15-108">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="dfc15-109">App Service incluye las funcionalidades web y móviles que anteriormente se ofrecían por separado como Azure Websites y Azure Mobile Services.</span><span class="sxs-lookup"><span data-stu-id="dfc15-109">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="dfc15-110">También incluye nuevas funcionalidades para automatizar procesos empresariales y hospedar las API en la nube.</span><span class="sxs-lookup"><span data-stu-id="dfc15-110">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="dfc15-111">Como un servicio integrado único, App Service le permite crear distintos componentes, como sitios web, back-end de aplicación móvil, API de RESTful y procesos empresariales, en una única solución.</span><span class="sxs-lookup"><span data-stu-id="dfc15-111">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="dfc15-112">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="dfc15-112">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="dfc15-113">Instalación del paquete npm</span><span class="sxs-lookup"><span data-stu-id="dfc15-113">Install the npm package</span></span>

<span data-ttu-id="dfc15-114">Instale el módulo de Azure App Service para Node.js.</span><span class="sxs-lookup"><span data-stu-id="dfc15-114">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="dfc15-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="dfc15-115">Example</span></span>

<span data-ttu-id="dfc15-116">En este ejemplo se crea un sitio web en Azure con Node.js.</span><span class="sxs-lookup"><span data-stu-id="dfc15-116">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="dfc15-117">Muestras</span><span class="sxs-lookup"><span data-stu-id="dfc15-117">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="dfc15-118">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="dfc15-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
