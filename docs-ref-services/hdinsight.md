---
title: "Módulos de Azure HDInsight para Node.js"
description: "Referencia de los módulos de Azure HDInsight para Node.js"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="542fd-104">Módulos de Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="542fd-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="542fd-105">Información general</span><span class="sxs-lookup"><span data-stu-id="542fd-105">Overview</span></span>

<span data-ttu-id="542fd-106">Azure HDInsight es una distribución en la nube de los componentes de Hadoop de Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="542fd-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="542fd-107">Apache Hadoop era el entorno de trabajo de código abierto original para el procesamiento distribuido y análisis de macrodatos en clústeres de equipos.</span><span class="sxs-lookup"><span data-stu-id="542fd-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="542fd-108">HDInsight hace más fácil de usar las tecnologías de Hadoop, con:</span><span class="sxs-lookup"><span data-stu-id="542fd-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="542fd-109">Menos configuración.</span><span class="sxs-lookup"><span data-stu-id="542fd-109">Less setup and configuration.</span></span> <span data-ttu-id="542fd-110">Consulte Aprovisionamiento de clústeres de Hadoop en HDInsight.</span><span class="sxs-lookup"><span data-stu-id="542fd-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="542fd-111">Alta disponibilidad y confiabilidad.</span><span class="sxs-lookup"><span data-stu-id="542fd-111">High availability and reliability.</span></span> <span data-ttu-id="542fd-112">Consulte Disponibilidad y confiabilidad de HDInsight.</span><span class="sxs-lookup"><span data-stu-id="542fd-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="542fd-113">Seguridad y gobierno mediante la integración con Active Directory.</span><span class="sxs-lookup"><span data-stu-id="542fd-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="542fd-114">Consulte Clústeres unidos al dominio.</span><span class="sxs-lookup"><span data-stu-id="542fd-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="542fd-115">Escalado dinámico sin interrupción de trabajos</span><span class="sxs-lookup"><span data-stu-id="542fd-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="542fd-116">Actualizaciones de componentes y versiones actuales.</span><span class="sxs-lookup"><span data-stu-id="542fd-116">Component updates and current versions.</span></span> <span data-ttu-id="542fd-117">Consulte Componentes y versiones de Hadoop en HDInsight.</span><span class="sxs-lookup"><span data-stu-id="542fd-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="542fd-118">Integración con otros servicios de Azure, como Web Apps y SQL Database</span><span class="sxs-lookup"><span data-stu-id="542fd-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="542fd-119">La pila de tecnología de Hadoop incluye software relacionado y utilidades, incluidas Apache Hive, HBase, Spark, Kafka y muchas otras.</span><span class="sxs-lookup"><span data-stu-id="542fd-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="542fd-120">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="542fd-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="542fd-121">Instalación de los módulos npm</span><span class="sxs-lookup"><span data-stu-id="542fd-121">Install the npm modules</span></span>

<span data-ttu-id="542fd-122">Utilice npm para instalar los módulos de Azure HDInsight para Node.js.</span><span class="sxs-lookup"><span data-stu-id="542fd-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="542fd-123">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="542fd-123">Example</span></span> 

<span data-ttu-id="542fd-124">En este ejemplo se crea un cliente de HD Insight y, después, se enumeran todos los clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="542fd-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="542fd-125">Muestras</span><span class="sxs-lookup"><span data-stu-id="542fd-125">Samples</span></span>

<span data-ttu-id="542fd-126">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="542fd-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
