---
title: Módulos de Azure Billing para Node.js
description: Referencia de los módulos de Azure Billing para Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 7be64d01c1bf8d247694735b8581f72678f55983
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50294178"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="1b89d-103">Módulos de Azure Billing para Node.js</span><span class="sxs-lookup"><span data-stu-id="1b89d-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1b89d-104">Información general</span><span class="sxs-lookup"><span data-stu-id="1b89d-104">Overview</span></span>
<span data-ttu-id="1b89d-105">Las API de Azure Billing proporcionan acceso mediante programación a la información de facturación y a las facturas de Azure.</span><span class="sxs-lookup"><span data-stu-id="1b89d-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="1b89d-106">Para utilizar esta API, debe elegir el administrador de cuenta a través de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="1b89d-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="1b89d-107">Consulte el tema sobre [administración del acceso a la facturación de Azure mediante roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="1b89d-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1b89d-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="1b89d-108">Install the npm module</span></span> 

<span data-ttu-id="1b89d-109">Instale el módulo npm de Azure Billing.</span><span class="sxs-lookup"><span data-stu-id="1b89d-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="1b89d-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1b89d-110">Example</span></span> 
 
<span data-ttu-id="1b89d-111">En este ejemplo se imprime una lista de todas las facturas anteriores.</span><span class="sxs-lookup"><span data-stu-id="1b89d-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="1b89d-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="1b89d-112">Samples</span></span>

<span data-ttu-id="1b89d-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1b89d-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
