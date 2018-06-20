---
title: Módulos de Azure Key Vault para Node.js
description: Referencia de los módulos de Azure Key Vault para Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 72bf4bc5443618f5f1bb9b4d1bb4d905669ff8c8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266602"
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Módulos de Azure Key Vault para Node.js

Azure Key Vault ayuda a proteger claves criptográficas y secretos usados por servicios y aplicaciones en la nube. Mediante el uso de Key Vault, puede cifrar claves y secretos (por ejemplo claves de autenticación, claves de cuenta de almacenamiento, claves de cifrado de datos, archivos .PFX y contraseñas) a través del uso de claves que están protegidas por módulos de seguridad de hardware (HSM). Para tener mayor seguridad, puede importar o generar las claves en HSM. Si decide hacerlo, Microsoft procesa las claves en los HSM validados de FIPS 140-2 nivel 2 (hardware y firmware).

Key Vault agiliza el proceso de administración de claves y le permite mantener el control de claves que obtienen acceso a sus datos y los cifran. Los desarrolladores pueden crear claves para desarrollo y prueba en minutos y, a continuación, migrarlas sin problemas a claves de producción. Los administradores de seguridad pueden conceder (y revocar) permisos a las claves según sea necesario.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm 

Instale el módulo npm de Azure Key Vault.

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Ejemplo

En este ejemplo se crea un nuevo servicio Key Vault en Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>Ejemplos

- [Introducción a Key Vault en Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Administración de recursos y grupos de recursos de Azure con Node.js](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) (Integración de Azure AD en una aplicación web de NodeJS) 

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
