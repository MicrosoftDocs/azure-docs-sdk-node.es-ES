---
title: "Módulos de Azure Data Lake Store para Node.js"
description: "Referencia de los módulos de Azure Data Lake Store para Node.js"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="e4192-104">Módulos de Azure Data Lake Store para Node.js</span><span class="sxs-lookup"><span data-stu-id="e4192-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e4192-105">Información general</span><span class="sxs-lookup"><span data-stu-id="e4192-105">Overview</span></span>
<span data-ttu-id="e4192-106">El Almacén de Azure Data Lake es un repositorio de gran escala en toda la empresa para cargas de trabajo de análisis de macrodatos.</span><span class="sxs-lookup"><span data-stu-id="e4192-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="e4192-107">Azure Data Lake permite capturar datos de cualquier tamaño, tipo y velocidad de ingesta en un único lugar para realizar análisis exploratorios y operativos.</span><span class="sxs-lookup"><span data-stu-id="e4192-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="e4192-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="e4192-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e4192-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="e4192-109">Install the npm module</span></span>

<span data-ttu-id="e4192-110">Utilice npm para instalar los módulos de Azure Data Lake Store para Node.js.</span><span class="sxs-lookup"><span data-stu-id="e4192-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="e4192-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e4192-111">Example</span></span>

<span data-ttu-id="e4192-112">En este ejemplo se enumeran todas las cuentas de Data Lake Store en una suscripción de Azure dada.</span><span class="sxs-lookup"><span data-stu-id="e4192-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="e4192-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="e4192-113">Samples</span></span>

<span data-ttu-id="e4192-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e4192-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
