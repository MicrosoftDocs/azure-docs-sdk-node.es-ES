---
title: Módulos de Azure Machine Learning para Node.js
description: Referencia de los módulos de Azure Machine Learning para Node.js
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7dfa6d8fa633863fe834ce73462584e79c312c5d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="15b6d-103">Módulos de Azure Machine Learning para Node.js</span><span class="sxs-lookup"><span data-stu-id="15b6d-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="15b6d-104">El aprendizaje automático es una técnica de ciencia de datos que ayuda a los equipos a aprender de los datos existentes para prever tendencias, resultados y comportamientos futuros.</span><span class="sxs-lookup"><span data-stu-id="15b6d-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="15b6d-105">Estas previsiones o predicciones del aprendizaje automático pueden hacer que las aplicaciones y los dispositivos sean más inteligentes.</span><span class="sxs-lookup"><span data-stu-id="15b6d-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="15b6d-106">Cuando compra en línea, el aprendizaje automático ayuda a recomendar otros productos según lo que haya adquirido.</span><span class="sxs-lookup"><span data-stu-id="15b6d-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="15b6d-107">Al pasar su tarjeta de crédito, el aprendizaje automático compara la transacción con una base de datos de transacciones y ayuda a detectar fraudes.</span><span class="sxs-lookup"><span data-stu-id="15b6d-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="15b6d-108">Cuando la aspiradora robot aspira una sala, el aprendizaje automático le ayuda a decidir si se ha terminado el trabajo.</span><span class="sxs-lookup"><span data-stu-id="15b6d-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="15b6d-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="15b6d-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="15b6d-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="15b6d-110">Install the npm module</span></span>

<span data-ttu-id="15b6d-111">Instale el módulo npm de Azure Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="15b6d-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="15b6d-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="15b6d-112">Example</span></span>

<span data-ttu-id="15b6d-113">En este ejemplo se enumeran todos los planes de confirmación de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="15b6d-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="15b6d-114">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="15b6d-114">Samples</span></span>

<span data-ttu-id="15b6d-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="15b6d-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
