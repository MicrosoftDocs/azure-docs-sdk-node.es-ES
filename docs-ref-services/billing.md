---
title: "Módulos de Azure Billing para Node.js"
description: "Referencia de los módulos de Azure Billing para Node.js"
keywords: Azure,SDK,API,Billing, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="93570-104">Módulos de Azure Billing para Node.js</span><span class="sxs-lookup"><span data-stu-id="93570-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="93570-105">Información general</span><span class="sxs-lookup"><span data-stu-id="93570-105">Overview</span></span>
<span data-ttu-id="93570-106">Las API de Azure Billing proporcionan acceso mediante programación a la información de facturación y a las facturas de Azure.</span><span class="sxs-lookup"><span data-stu-id="93570-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="93570-107">Para utilizar esta API, debe elegir el administrador de cuenta a través de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="93570-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="93570-108">Consulte el tema sobre [administración del acceso a la facturación de Azure mediante roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="93570-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="93570-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="93570-109">Install the npm module</span></span> 

<span data-ttu-id="93570-110">Instale el módulo npm de Azure Billing.</span><span class="sxs-lookup"><span data-stu-id="93570-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="93570-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="93570-111">Example</span></span> 
 
<span data-ttu-id="93570-112">En este ejemplo se imprime una lista de todas las facturas anteriores.</span><span class="sxs-lookup"><span data-stu-id="93570-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="93570-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="93570-113">Samples</span></span>

<span data-ttu-id="93570-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="93570-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
