---
title: "Ejemplos de código sobre el uso de la mensajería de Azure e IoT con Node.js"
description: "Código de ejemplo que muestra el uso de la mensajería de Azure e IoT con Node.js"
author: craigshoemaker
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: cshoe
ms.openlocfilehash: 45aad90670a8ac8c0f32f9deab2eb32043c52d96
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="399fd-103">Código de ejemplo para usar la mensajería de Azure e IoT con Node.js</span><span class="sxs-lookup"><span data-stu-id="399fd-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="399fd-104">El código de ejemplo siguiente muestra cómo usar la mensajería de Azure con IoT con Node.js.</span><span class="sxs-lookup"><span data-stu-id="399fd-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="399fd-105">Si se necesita código para otras tareas, puede examinar la lista completa de [ejemplos de Node.js de Azure](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="399fd-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="399fd-106">**Azure IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="399fd-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="399fd-107">Ping de Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="399fd-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="399fd-108">Solución sencilla de ping como ayuda para validar una conectividad de dispositivo en Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="399fd-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| <span data-ttu-id="399fd-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalías de vibración de tweets detectadas por los servicios Azure IoT en los datos de un Intel Edison que ejecuta Node.js)</span><span class="sxs-lookup"><span data-stu-id="399fd-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span> | <span data-ttu-id="399fd-110">Proyecto de IoT con Azure IoT Hub y que muestra un dispositivo que ejecuta un nodo para enviar datos de telemetría que se analizan mediante servicios IoT de Azure.</span><span class="sxs-lookup"><span data-stu-id="399fd-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="399fd-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="399fd-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="399fd-112">Introducción a Starter Kit de IoT de Azure en Intel Edison</span><span class="sxs-lookup"><span data-stu-id="399fd-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="399fd-113">Muestra Azure IoT con el Starter Kit de IoT de Azure - Intel Edison.</span><span class="sxs-lookup"><span data-stu-id="399fd-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="399fd-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="399fd-114">**MQTT**</span></span> ||
| [<span data-ttu-id="399fd-115">Ejemplos de módulos de puerta de enlace MQTT y HTTP</span><span class="sxs-lookup"><span data-stu-id="399fd-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="399fd-116">Proporciona dos módulos de puerta de enlace que exponen puntos de conexión HTTPS y MQTT basados IoT Hub para la carga de telemetría y, en el caso del módulo MQTT, también mensajería C2D.</span><span class="sxs-lookup"><span data-stu-id="399fd-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="399fd-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="399fd-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="399fd-118">Introducción a Starter Kit de Raspberry Pi de IoT de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="399fd-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="399fd-119">Muestra cómo utilizar el Starter Kit de Raspberry Pi de IoT de Azure.</span><span class="sxs-lookup"><span data-stu-id="399fd-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="399fd-120">Conexión de su Starter Kit de Raspberry Pi 3 de IoT de Microsoft Azure a la solución de supervisión remota</span><span class="sxs-lookup"><span data-stu-id="399fd-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="399fd-121">Aprenda a conectar un dispositivo Raspberry Pi 3 a la solución de supervisión remota de Azure IoT Suite.</span><span class="sxs-lookup"><span data-stu-id="399fd-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
