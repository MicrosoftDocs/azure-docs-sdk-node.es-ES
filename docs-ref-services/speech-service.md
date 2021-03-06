---
title: Speech SDK de Cognitive Services para JavaScript
description: Referencia de Speech SDK de Cognitive Services para JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052571"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Speech SDK de Cognitive Services para JavaScript

## <a name="overview"></a>Información general

Para simplificar el desarrollo de aplicaciones habilitadas para voz, Microsoft proporciona Speech SDK para su uso con [Speech Service](https://aka.ms/csspeech).
Speech SDK proporciona API coherentes nativas de conversión de voz en texto y de traducción de voz.

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instalación del módulo npm del SDK de Voz de Cognitive Services

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>Ejemplo 

Los fragmentos de código siguientes muestran cómo realizar un reconocimiento de voz simple desde un archivo:

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

Consulte la [guía de inicio rápido paso a paso](/azure/cognitive-services/speech-service/quickstart-js-node).

## <a name="samples"></a>Ejemplos

* [Inicio rápido paso a paso para Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).
* [Inicio rápido paso a paso para el explorador](/azure/cognitive-services/speech-service/quickstart-js-browser).
* Vea más ejemplos en el [repositorio de ejemplos del SDK de Voz](https://aka.ms/csspeech/samples).
