---
title: Módulos de Azure Authorization para Node.js
description: Referencia de los módulos de Azure Authorization para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 5be0e069d0acf72de65e891e6304ef1ca78e967a
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>Módulos de Azure Authorization para Node.js

## <a name="overview"></a>Información general

La autenticación/autorización de Azure App Service es una característica que proporciona una forma para que la aplicación lleve a cabo el inicio de sesión de usuarios sin necesidad de cambiar el código en el back-end de aplicación. La autorización ofrece una forma fácil de proteger su aplicación y trabajar con datos por usuario.

## <a name="management-package"></a>Paquete de administración

Utilice npm para instalar los módulos de Azure Authorization para Node.js.

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Authorization.

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todas las asignaciones de roles para el grupo de recursos solicitado.

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
