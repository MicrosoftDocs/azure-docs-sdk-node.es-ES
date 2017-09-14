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


## <a name="samples"></a>Muestras

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
