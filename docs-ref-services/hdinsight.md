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
ms.openlocfilehash: 9a40830e7c5330d4e258840b1b1b2210acf891c5
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48479393"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Módulos de Azure HDInsight para Node.js

Azure HDInsight es una distribución en la nube de los componentes de Hadoop de Hortonworks Data Platform (HDP). Apache Hadoop era el entorno de trabajo de código abierto original para el procesamiento distribuido y análisis de macrodatos en clústeres de equipos.

HDInsight hace más fácil de usar las tecnologías de Hadoop, con:
- Menos configuración. Consulte Aprovisionamiento de clústeres de Hadoop en HDInsight.
- Alta disponibilidad y confiabilidad. Consulte Disponibilidad y confiabilidad de HDInsight.
- Seguridad y gobierno mediante la integración con Active Directory. Consulte Clústeres unidos al dominio.
- Escalado dinámico sin interrupción de trabajos
- Actualizaciones de componentes y versiones actuales. Consulte Componentes y versiones de Hadoop en HDInsight.
- Integración con otros servicios de Azure, como Web Apps y SQL Database

La pila de tecnología de Hadoop incluye software relacionado y utilidades, incluidas Apache Hive, HBase, Spark, Kafka y muchas otras. 

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-modules"></a>Instalación de los módulos npm

Utilice npm para instalar los módulos de Azure HDInsight para Node.js.

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Ejemplo 

En este ejemplo se crea un cliente de HD Insight y, después, se enumeran todos los clústeres disponibles. 

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

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
