---
title: Módulos de Azure Automation para Node.js
description: Referencia de los módulos de Azure Automation para Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 5efe0c0633313bcf489b05b8a54f71bba9a00da5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-automation-modules-for-nodejs"></a>Módulos de Azure Automation para Node.js

## <a name="overview"></a>Información general

Azure Automation ofrece a los usuarios una manera de automatizar las tareas manuales, propensas a errores, con una ejecución prolongada y repetidas con frecuencia que se realizan normalmente en un entorno empresarial y en la nube. Automation ahorra tiempo y aumenta la confiabilidad de las tareas administrativas periódicas e incluso las programa para que se realicen automáticamente a intervalos regulares. Puede automatizar procesos mediante runbooks o automatizar la administración de configuración mediante la configuración de estado deseado.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-modules-with-npm"></a>Instalación de los módulos con npm

Utilice npm para instalar los módulos de Azure Automation para Node.js.

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran las cuentas de Automation.

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
