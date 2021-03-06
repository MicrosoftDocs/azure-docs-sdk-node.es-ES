---
title: Módulos de Azure Advisor para Node.js
description: Referencia de los módulos de Azure Advisor para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 952ac4bb67f4c177a06ce0ae3eb0fac7fa8ded54
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052589"
---
# <a name="azure-advisor-modules-for-nodejs"></a>Módulos de Azure Advisor para Node.js

## <a name="overview"></a>Información general

Asistente de Azure es un consultor en la nube personalizado que le ayudará a realizar procedimientos recomendadas para optimizar las implementaciones de Azure. Advisor analiza la configuración de recursos y la telemetría de uso, y recomienda soluciones que pueden ayudar a mejoran la rentabilidad, el rendimiento, la alta disponibilidad y la seguridad de los recursos de Azure.

Con Advisor, puede:
- Obtener sugerencias de procedimientos recomendados proactivas, prácticas y personalizadas,
- Mejorar el rendimiento, la seguridad y la alta disponibilidad de los recursos, al mismo tiempo que identifica oportunidades para reducir el gasto general de Azure, y
- Obtener recomendaciones con acciones propuestas en línea.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Advisor.

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Ejemplo

En este ejemplo se muestra la lista de recomendaciones de Azure Advisor.

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
