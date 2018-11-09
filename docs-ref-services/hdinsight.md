---
title: Módulos de Azure HDInsight para Node.js
description: Referencia de los módulos de Azure HDInsight para Node.js
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: e35e0d487efce2a591130403f8b72a43c638fdec
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51148926"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="fd862-103">Módulos de Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="fd862-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="fd862-104">Azure HDInsight es una distribución en la nube de los componentes de Hadoop de Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="fd862-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="fd862-105">Apache Hadoop era el entorno de trabajo de código abierto original para el procesamiento distribuido y análisis de macrodatos en clústeres de equipos.</span><span class="sxs-lookup"><span data-stu-id="fd862-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="fd862-106">HDInsight hace más fácil de usar las tecnologías de Hadoop, con:</span><span class="sxs-lookup"><span data-stu-id="fd862-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="fd862-107">Menos configuración.</span><span class="sxs-lookup"><span data-stu-id="fd862-107">Less setup and configuration.</span></span> <span data-ttu-id="fd862-108">Consulte Aprovisionamiento de clústeres de Hadoop en HDInsight.</span><span class="sxs-lookup"><span data-stu-id="fd862-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="fd862-109">Alta disponibilidad y confiabilidad.</span><span class="sxs-lookup"><span data-stu-id="fd862-109">High availability and reliability.</span></span> <span data-ttu-id="fd862-110">Consulte Disponibilidad y confiabilidad de HDInsight.</span><span class="sxs-lookup"><span data-stu-id="fd862-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="fd862-111">Seguridad y gobierno mediante la integración con Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fd862-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="fd862-112">Consulte Clústeres unidos al dominio.</span><span class="sxs-lookup"><span data-stu-id="fd862-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="fd862-113">Escalado dinámico sin interrupción de trabajos</span><span class="sxs-lookup"><span data-stu-id="fd862-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="fd862-114">Actualizaciones de componentes y versiones actuales.</span><span class="sxs-lookup"><span data-stu-id="fd862-114">Component updates and current versions.</span></span> <span data-ttu-id="fd862-115">Consulte Componentes y versiones de Hadoop en HDInsight.</span><span class="sxs-lookup"><span data-stu-id="fd862-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="fd862-116">Integración con otros servicios de Azure, como Web Apps y SQL Database</span><span class="sxs-lookup"><span data-stu-id="fd862-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="fd862-117">La pila de tecnología de Hadoop incluye software relacionado y utilidades, incluidas Apache Hive, HBase, Spark, Kafka y muchas otras.</span><span class="sxs-lookup"><span data-stu-id="fd862-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="fd862-118">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="fd862-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="fd862-119">Instalación de los módulos npm</span><span class="sxs-lookup"><span data-stu-id="fd862-119">Install the npm modules</span></span>

<span data-ttu-id="fd862-120">Utilice npm para instalar los módulos de Azure HDInsight para Node.js.</span><span class="sxs-lookup"><span data-stu-id="fd862-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="fd862-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fd862-121">Example</span></span> 

<span data-ttu-id="fd862-122">En este ejemplo se crea un cliente de HD Insight y, después, se enumeran todos los clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="fd862-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="fd862-123">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="fd862-123">Samples</span></span>

<span data-ttu-id="fd862-124">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="fd862-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
