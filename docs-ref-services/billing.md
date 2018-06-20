---
title: Módulos de Azure Billing para Node.js
description: Referencia de los módulos de Azure Billing para Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 111ca8d4ed40200a307b608915d71d2fa6944ed2
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260348"
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
