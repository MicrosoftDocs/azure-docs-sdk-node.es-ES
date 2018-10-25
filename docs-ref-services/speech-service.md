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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49724420"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Speech SDK de Cognitive Services para JavaScript

## <a name="overview"></a>Información general

Para simplificar el desarrollo de aplicaciones habilitadas para voz, Microsoft proporciona Speech SDK para su uso con [Speech Service](https://aka.ms/csspeech).
Speech SDK proporciona API coherentes nativas de conversión de voz en texto y de traducción de voz.

> [!NOTE]
> Speech SDK de Cognitive Services está actualmente disponible solo para exploradores.
> Pronto proporcionaremos un paquete de NPM.

### <a name="install-the-speech-sdk"></a>Instalación de Speech SDK

Descargue Speech SDK como un [paquete .zip](https://aka.ms/csspeech/jsbrowserpackage) y descomprímalo.
Esto debería producir el desempaquetado de varios archivos incluido un archivo Llamado `microsoft.cognitiveservices.speech.sdk.bundle.js`.
Cargue este archivo como un recurso de script en la página web para empezar a usar Speech SDK:

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Ejemplo 

Los fragmentos de código siguientes muestran cómo realizar un reconocimiento de voz simple desde el explorador:

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

Consulte la [guía de inicio rápido paso a paso](/azure/cognitive-services/speech-service/quickstart-js-browser).

## <a name="samples"></a>Ejemplos

Explore más ejemplos en el [repositorio de ejemplos de Speech SDK](https://aka.ms/csspeech/samples).
