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
ms.locfileid: "34259894"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Módulos de Azure Machine Learning para Node.js

El aprendizaje automático es una técnica de ciencia de datos que ayuda a los equipos a aprender de los datos existentes para prever tendencias, resultados y comportamientos futuros. Estas previsiones o predicciones del aprendizaje automático pueden hacer que las aplicaciones y los dispositivos sean más inteligentes. Cuando compra en línea, el aprendizaje automático ayuda a recomendar otros productos según lo que haya adquirido. Al pasar su tarjeta de crédito, el aprendizaje automático compara la transacción con una base de datos de transacciones y ayuda a detectar fraudes. Cuando la aspiradora robot aspira una sala, el aprendizaje automático le ayuda a decidir si se ha terminado el trabajo.

## <a name="management-package"></a>Paquete de administración


### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Machine Learning.

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todos los planes de confirmación de aprendizaje automático.

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

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
