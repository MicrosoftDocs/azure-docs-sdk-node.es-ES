---
title: Módulos de Azure Data Lake Analytics para Node.js
description: Referencia de los módulos de Azure Data Lake Analytics para Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134334"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="6c472-103">Módulos de Azure Data Lake Analytics para Node.js</span><span class="sxs-lookup"><span data-stu-id="6c472-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="6c472-104">Azure Data Lake Analytics es un servicio de trabajos de análisis a petición que simplifica el análisis de macrodatos.</span><span class="sxs-lookup"><span data-stu-id="6c472-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="6c472-105">Le permite centrarse en la escritura, ejecución y administración de trabajos, en lugar de en el manejo de una infraestructura distribuida.</span><span class="sxs-lookup"><span data-stu-id="6c472-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="6c472-106">En lugar de implementar, configurar y ajustar el hardware, escribirá consultas para transformar los datos y extraer ideas valiosas.</span><span class="sxs-lookup"><span data-stu-id="6c472-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="6c472-107">El servicio de análisis puede administrar trabajos de cualquier escala al instante, simplemente estableciendo el ajuste adecuado.</span><span class="sxs-lookup"><span data-stu-id="6c472-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="6c472-108">Solo tiene que pagar por su trabajo cuando se está ejecutando, lo que hace que sea una solución económica.</span><span class="sxs-lookup"><span data-stu-id="6c472-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="6c472-109">El servicio de análisis admite Azure Active Directory, lo que permite administrar de forma sencilla el acceso y los roles, que se integran con su sistema local de identidades.</span><span class="sxs-lookup"><span data-stu-id="6c472-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="6c472-110">También incluye U-SQL, un lenguaje que unifica las ventajas de SQL con el poder expresivo del código del usuario.</span><span class="sxs-lookup"><span data-stu-id="6c472-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="6c472-111">El tiempo de ejecución distribuido escalable de U-SQL permite analizar de forma eficiente los datos del almacén y entre los servidores SQL Server en Azure, Azure SQL Database y Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6c472-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="6c472-112">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="6c472-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6c472-113">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="6c472-113">Install the npm module</span></span>

<span data-ttu-id="6c472-114">Utilice npm para instalar los módulos de Azure Data Lake Analytics para Node.js.</span><span class="sxs-lookup"><span data-stu-id="6c472-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="6c472-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6c472-115">Example</span></span>

<span data-ttu-id="6c472-116">En este ejemplo se enumeran todas las cuentas de análisis para una suscripción determinada.</span><span class="sxs-lookup"><span data-stu-id="6c472-116">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="6c472-117">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="6c472-117">Samples</span></span>

<span data-ttu-id="6c472-118">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="6c472-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
