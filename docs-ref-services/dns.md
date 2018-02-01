---
title: "Módulos de Azure DNS para Node.js"
description: "Referencia de los módulos de Azure DNS para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: c1ffacb3dd6b836303c5fcb2c18d7d68d2390ec7
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="567db-103">Módulos de Azure DNS para Node.js</span><span class="sxs-lookup"><span data-stu-id="567db-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="567db-104">Utilice Azure DNS para hospedar sus dominios del Sistema de nombres de dominio (DNS) en Azure.</span><span class="sxs-lookup"><span data-stu-id="567db-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="567db-105">Puede administrar sus registros de DNS usando las mismas credenciales, el mismo plan de facturación y el mismo contrato de soporte técnico que utiliza para los demás servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="567db-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="567db-106">Integre sin problemas los servicios basados en Azure con las correspondientes actualizaciones de DNS y optimice el proceso de implementación de un extremo a otro.</span><span class="sxs-lookup"><span data-stu-id="567db-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="567db-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="567db-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="567db-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="567db-108">Install the npm module</span></span>

<span data-ttu-id="567db-109">Instale el módulo npm de Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="567db-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="567db-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="567db-110">Example</span></span>

<span data-ttu-id="567db-111">En este ejemplo se enumeran las zonas de administración de DNS.</span><span class="sxs-lookup"><span data-stu-id="567db-111">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="567db-112">Muestras</span><span class="sxs-lookup"><span data-stu-id="567db-112">Samples</span></span>

<span data-ttu-id="567db-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="567db-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
