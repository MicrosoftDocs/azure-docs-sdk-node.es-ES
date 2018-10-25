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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49772230"
---
# <a name="azure-billing-modules-for-nodejs"></a>Módulos de Azure Billing para Node.js

## <a name="overview"></a>Información general
Las API de Azure Billing proporcionan acceso mediante programación a la información de facturación y a las facturas de Azure.

Para utilizar esta API, debe elegir el administrador de cuenta a través de Azure Portal. Consulte el tema sobre [administración del acceso a la facturación de Azure mediante roles](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Instalación del módulo npm 

Instale el módulo npm de Azure Billing. 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Ejemplo 
 
En este ejemplo se imprime una lista de todas las facturas anteriores.
 
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


## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
