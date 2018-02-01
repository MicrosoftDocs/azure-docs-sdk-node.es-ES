---
title: "Módulos de Azure Logic Apps para Node.js"
description: "Referencia de los módulos de Azure Logic Apps para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 37e485bea316ebd7fb4a064e1919da5501d96eac
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="01ee6-103">Módulos de Azure Logic Apps para Node.js</span><span class="sxs-lookup"><span data-stu-id="01ee6-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="01ee6-104">Logic Apps es una manera de simplificar e implementar integraciones escalables y flujos de trabajo en la nube.</span><span class="sxs-lookup"><span data-stu-id="01ee6-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="01ee6-105">Proporciona un diseñador visual para modelar y automatizar el proceso en una serie de pasos denominada flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="01ee6-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="01ee6-106">Hay muchos conectores locales y en la nube para la integración rápida en servicios y protocolos.</span><span class="sxs-lookup"><span data-stu-id="01ee6-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="01ee6-107">Una aplicación lógica comienza con un desencadenador (como "Cuando se agrega una cuenta a Dynamics CRM") y después la activación puede comenzar muchas combinaciones de acciones, conversiones y lógicas de condiciones.</span><span class="sxs-lookup"><span data-stu-id="01ee6-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="01ee6-108">Algunas ventajas de Logic Apps:</span><span class="sxs-lookup"><span data-stu-id="01ee6-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="01ee6-109">Ahorro de tiempo al diseñar procesos complejos gracias a las herramientas de diseño que se entienden fácilmente</span><span class="sxs-lookup"><span data-stu-id="01ee6-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="01ee6-110">Implementación inigualable de patrones y flujos de trabajo, que de lo contrario, serían difíciles de implementar en el código</span><span class="sxs-lookup"><span data-stu-id="01ee6-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="01ee6-111">Introducción rápida desde plantillas</span><span class="sxs-lookup"><span data-stu-id="01ee6-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="01ee6-112">Personalización de aplicaciones lógicas con API, código y acciones propios</span><span class="sxs-lookup"><span data-stu-id="01ee6-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="01ee6-113">Conexión y sincronización de sistemas dispares locales y en la nube</span><span class="sxs-lookup"><span data-stu-id="01ee6-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="01ee6-114">Generación del servidor de BizTalk, API Management, Azure Functions y Azure Service Bus compatible con integración de primera clase</span><span class="sxs-lookup"><span data-stu-id="01ee6-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="01ee6-115">Logic Apps es una iPaaS (plataforma de integración como servicio) totalmente administrada que permite a los desarrolladores despreocuparse del hospedaje, la escalabilidad, la disponibilidad y la administración.</span><span class="sxs-lookup"><span data-stu-id="01ee6-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="01ee6-116">Logic Apps se escala automáticamente según las necesidades.</span><span class="sxs-lookup"><span data-stu-id="01ee6-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="01ee6-117">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="01ee6-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="01ee6-118">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="01ee6-118">Install the npm module</span></span>

<span data-ttu-id="01ee6-119">Instale el módulo de Azure Logic Apps para Node.js.</span><span class="sxs-lookup"><span data-stu-id="01ee6-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="01ee6-120">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="01ee6-120">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="01ee6-121">Muestras</span><span class="sxs-lookup"><span data-stu-id="01ee6-121">Samples</span></span>

<span data-ttu-id="01ee6-122">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="01ee6-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
