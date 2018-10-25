---
title: Módulos de Azure Data Lake Store para Node.js
description: Referencia de los módulos de Azure Data Lake Store para Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49670841"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="c6210-103">Módulos de Azure Data Lake Store para Node.js</span><span class="sxs-lookup"><span data-stu-id="c6210-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="c6210-104">El Almacén de Azure Data Lake es un repositorio de gran escala en toda la empresa para cargas de trabajo de análisis de macrodatos.</span><span class="sxs-lookup"><span data-stu-id="c6210-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="c6210-105">Azure Data Lake permite capturar datos de cualquier tamaño, tipo y velocidad de ingesta en un único lugar para realizar análisis exploratorios y operativos.</span><span class="sxs-lookup"><span data-stu-id="c6210-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="c6210-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="c6210-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c6210-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="c6210-107">Install the npm module</span></span>

<span data-ttu-id="c6210-108">Utilice npm para instalar los módulos de Azure Data Lake Store para Node.js.</span><span class="sxs-lookup"><span data-stu-id="c6210-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="c6210-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6210-109">Example</span></span>

<span data-ttu-id="c6210-110">En este ejemplo se enumeran todas las cuentas de Data Lake Store en una suscripción de Azure dada.</span><span class="sxs-lookup"><span data-stu-id="c6210-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="c6210-111">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="c6210-111">Samples</span></span>

<span data-ttu-id="c6210-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c6210-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
