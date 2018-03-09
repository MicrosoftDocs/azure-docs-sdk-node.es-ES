---
title: "Módulos de Azure CDN para Node.js"
description: "Referencia de los módulos de Azure CDN para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 05e77072f551d425ba3ca5225111d0470d14fe68
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="95c45-103">Módulos de Azure CDN para Node.js</span><span class="sxs-lookup"><span data-stu-id="95c45-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="95c45-104">Información general</span><span class="sxs-lookup"><span data-stu-id="95c45-104">Overview</span></span>

<span data-ttu-id="95c45-105">Microsoft Azure Content Delivery Network (CDN) ofrece a los desarrolladores una solución global para entregar contenido con alto ancho de banda que se hospeda en Azure o en cualquier otra ubicación.</span><span class="sxs-lookup"><span data-stu-id="95c45-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="95c45-106">Con la red CDN, puede almacenar en caché objetos disponibles públicamente cargados desde Almacenamiento de blobs de Azure, una aplicación web, una máquina virtual, una carpeta de la aplicación u otra ubicación HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="95c45-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="95c45-107">La caché de CDN puede mantenerse en ubicaciones estratégicas, con el fin de proporcionar el ancho de banda máximo para entregar contenido a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="95c45-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="95c45-108">La red CDN se suele usar para entregar el contenido estático, como imágenes, hojas de estilo, documentos, archivos, scripts de cliente y páginas HTML.</span><span class="sxs-lookup"><span data-stu-id="95c45-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="95c45-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="95c45-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="95c45-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="95c45-110">Install the npm module</span></span>

<span data-ttu-id="95c45-111">Instale el módulo npm de Azure CDN.</span><span class="sxs-lookup"><span data-stu-id="95c45-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="95c45-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="95c45-112">Example</span></span>

<span data-ttu-id="95c45-113">En este ejemplo se muestran todos los perfiles de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="95c45-113">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="95c45-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="95c45-114">Samples</span></span>

<span data-ttu-id="95c45-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="95c45-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>