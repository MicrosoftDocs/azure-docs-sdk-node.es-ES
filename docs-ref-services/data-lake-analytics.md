---
title: "Módulos de Azure Data Lake Analytics para Node.js"
description: "Referencia de los módulos de Azure Data Lake Analytics para Node.js"
keywords: Azure,SDK,API,Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Módulos de Azure Data Lake Analytics para Node.js

## <a name="overview"></a>Información general
Azure Data Lake Analytics es un servicio de trabajos de análisis a petición que simplifica el análisis de macrodatos. Le permite centrarse en la escritura, ejecución y administración de trabajos, en lugar de en el manejo de una infraestructura distribuida. En lugar de implementar, configurar y ajustar el hardware, escribirá consultas para transformar los datos y extraer ideas valiosas. El servicio de análisis puede administrar trabajos de cualquier escala al instante, simplemente estableciendo el ajuste adecuado. Solo tiene que pagar por su trabajo cuando se está ejecutando, lo que hace que sea una solución económica. El servicio de análisis admite Azure Active Directory, lo que permite administrar de forma sencilla el acceso y los roles, que se integran con su sistema local de identidades. También incluye U-SQL, un lenguaje que unifica las ventajas de SQL con el poder expresivo del código del usuario. El tiempo de ejecución distribuido escalable de U-SQL permite analizar de forma eficiente los datos del almacén y entre los servidores SQL Server en Azure, Azure SQL Database y Azure SQL Data Warehouse.

### <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar los módulos de Azure Data Lake Analytics para Node.js.

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todas las cuentas de análisis para una suscripción determinada.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Muestras

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.