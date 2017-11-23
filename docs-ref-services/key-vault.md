---
title: "Módulos de Azure Key Vault para Node.js"
description: "Referencia de los módulos de Azure Key Vault para Node.js"
keywords: Azure,SDK,API,Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="bbb2f-104">Módulos de Azure Key Vault para Node.js</span><span class="sxs-lookup"><span data-stu-id="bbb2f-104">Azure Key Vault modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bbb2f-105">Información general</span><span class="sxs-lookup"><span data-stu-id="bbb2f-105">Overview</span></span>

<span data-ttu-id="bbb2f-106">El Almacén de claves de Azure ayuda a proteger claves criptográficas y secretos usados por servicios y aplicaciones en la nube.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-106">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="bbb2f-107">Mediante el uso de Key Vault, puede cifrar claves y secretos (por ejemplo claves de autenticación, claves de cuenta de almacenamiento, claves de cifrado de datos, archivos .PFX y contraseñas) a través del uso de claves que están protegidas por módulos de seguridad de hardware (HSM).</span><span class="sxs-lookup"><span data-stu-id="bbb2f-107">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="bbb2f-108">Para tener mayor seguridad, puede importar o generar las claves en HSM.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-108">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="bbb2f-109">Si decide hacerlo, Microsoft procesa las claves en los HSM validados de FIPS 140-2 nivel 2 (hardware y firmware).</span><span class="sxs-lookup"><span data-stu-id="bbb2f-109">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="bbb2f-110">Almacén de claves agiliza el proceso de administración de claves y le permite mantener el control de claves que obtienen acceso a sus datos y los cifran.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-110">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="bbb2f-111">Los desarrolladores pueden crear claves para desarrollo y prueba en minutos y, a continuación, migrarlas sin problemas a claves de producción.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-111">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="bbb2f-112">Los administradores de seguridad pueden conceder (y revocar) permisos a las claves según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-112">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="bbb2f-113">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="bbb2f-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bbb2f-114">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="bbb2f-114">Install the npm module</span></span> 

<span data-ttu-id="bbb2f-115">Instale el módulo npm de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-115">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="bbb2f-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bbb2f-116">Example</span></span>

<span data-ttu-id="bbb2f-117">En este ejemplo se crea un nuevo servicio Key Vault en Azure.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-117">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="bbb2f-118">Muestras</span><span class="sxs-lookup"><span data-stu-id="bbb2f-118">Samples</span></span>

- [<span data-ttu-id="bbb2f-119">Introducción a Key Vault en Node.js</span><span class="sxs-lookup"><span data-stu-id="bbb2f-119">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="bbb2f-120">Administración de recursos y grupos de recursos de Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="bbb2f-120">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- <span data-ttu-id="bbb2f-121">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) (Integración de Azure AD en una aplicación web de NodeJS)</span><span class="sxs-lookup"><span data-stu-id="bbb2f-121">[Integrating Azure AD into a NodeJS web application](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/)</span></span> 

<span data-ttu-id="bbb2f-122">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="bbb2f-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
