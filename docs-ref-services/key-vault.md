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
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2018
ms.locfileid: "52098870"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="b15e0-103">Módulos de Azure Key Vault para Node.js</span><span class="sxs-lookup"><span data-stu-id="b15e0-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="b15e0-104">Azure Key Vault ayuda a proteger claves criptográficas y secretos usados por servicios y aplicaciones en la nube.</span><span class="sxs-lookup"><span data-stu-id="b15e0-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="b15e0-105">Mediante el uso de Key Vault, puede cifrar claves y secretos (por ejemplo claves de autenticación, claves de cuenta de almacenamiento, claves de cifrado de datos, archivos .PFX y contraseñas) a través del uso de claves que están protegidas por módulos de seguridad de hardware (HSM).</span><span class="sxs-lookup"><span data-stu-id="b15e0-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="b15e0-106">Para tener mayor seguridad, puede importar o generar las claves en HSM.</span><span class="sxs-lookup"><span data-stu-id="b15e0-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="b15e0-107">Si decide hacerlo, Microsoft procesa las claves en los HSM validados de FIPS 140-2 nivel 2 (hardware y firmware).</span><span class="sxs-lookup"><span data-stu-id="b15e0-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="b15e0-108">Key Vault agiliza el proceso de administración de claves y le permite mantener el control de claves que obtienen acceso a sus datos y los cifran.</span><span class="sxs-lookup"><span data-stu-id="b15e0-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="b15e0-109">Los desarrolladores pueden crear claves para desarrollo y prueba en minutos y, a continuación, migrarlas sin problemas a claves de producción.</span><span class="sxs-lookup"><span data-stu-id="b15e0-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="b15e0-110">Los administradores de seguridad pueden conceder (y revocar) permisos a las claves según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="b15e0-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="b15e0-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="b15e0-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b15e0-112">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="b15e0-112">Install the npm module</span></span> 

<span data-ttu-id="b15e0-113">Instale el módulo npm de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b15e0-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="b15e0-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b15e0-114">Example</span></span>

<span data-ttu-id="b15e0-115">En este ejemplo se crea un nuevo servicio Key Vault en Azure.</span><span class="sxs-lookup"><span data-stu-id="b15e0-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b15e0-116">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="b15e0-116">Samples</span></span>

- [<span data-ttu-id="b15e0-117">Introducción a Key Vault en Node.js</span><span class="sxs-lookup"><span data-stu-id="b15e0-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="b15e0-118">Administración de recursos y grupos de recursos de Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="b15e0-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- <span data-ttu-id="b15e0-119">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) (Integración de Azure AD en una aplicación web de NodeJS)</span><span class="sxs-lookup"><span data-stu-id="b15e0-119">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/)</span></span> 

<span data-ttu-id="b15e0-120">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b15e0-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
