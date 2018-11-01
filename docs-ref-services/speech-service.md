---
title: Speech SDK de Cognitive Services para JavaScript
description: Referencia de Speech SDK de Cognitive Services para JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50402391"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="38510-103">Speech SDK de Cognitive Services para JavaScript</span><span class="sxs-lookup"><span data-stu-id="38510-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="38510-104">Información general</span><span class="sxs-lookup"><span data-stu-id="38510-104">Overview</span></span>

<span data-ttu-id="38510-105">Para simplificar el desarrollo de aplicaciones habilitadas para voz, Microsoft proporciona Speech SDK para su uso con [Speech Service](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="38510-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="38510-106">Speech SDK proporciona API coherentes nativas de conversión de voz en texto y de traducción de voz.</span><span class="sxs-lookup"><span data-stu-id="38510-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="38510-107">Speech SDK de Cognitive Services está actualmente disponible solo para exploradores.</span><span class="sxs-lookup"><span data-stu-id="38510-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="38510-108">Pronto proporcionaremos un paquete de NPM.</span><span class="sxs-lookup"><span data-stu-id="38510-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="38510-109">Instalación de Speech SDK</span><span class="sxs-lookup"><span data-stu-id="38510-109">Install the Speech SDK</span></span>

<span data-ttu-id="38510-110">Descargue Speech SDK como un [paquete .zip](https://aka.ms/csspeech/jsbrowserpackage) y descomprímalo.</span><span class="sxs-lookup"><span data-stu-id="38510-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="38510-111">Esto debería producir el desempaquetado de varios archivos incluido un archivo Llamado `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span><span class="sxs-lookup"><span data-stu-id="38510-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="38510-112">Cargue este archivo como un recurso de script en la página web para empezar a usar Speech SDK:</span><span class="sxs-lookup"><span data-stu-id="38510-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="38510-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="38510-113">Example</span></span> 

<span data-ttu-id="38510-114">Los fragmentos de código siguientes muestran cómo realizar un reconocimiento de voz simple desde el explorador:</span><span class="sxs-lookup"><span data-stu-id="38510-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="38510-115">Consulte la [guía de inicio rápido paso a paso](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="38510-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="38510-116">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="38510-116">Samples</span></span>

<span data-ttu-id="38510-117">Explore más ejemplos en el [repositorio de ejemplos de Speech SDK](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="38510-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
