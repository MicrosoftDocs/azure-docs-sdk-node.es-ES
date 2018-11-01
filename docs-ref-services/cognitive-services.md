---
title: Módulos de Azure Cognitive Services para Node.js
description: Referencia de los módulos de Azure Cognitive Services para Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50272688"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Módulos de Azure Cognitive Services para JavaScript

## <a name="vision-modules"></a>Módulos de visión

### <a name="computer-vision"></a>Computer Vision 

Devuelve información sobre el contenido visual encontrado en una imagen:

- Use etiquetado, descripciones y modelos específicos del dominio para identificar el contenido y etiquetarlo con confianza.
- Aplique la configuración para adultos para habilitar la restricción automatizada de contenido adulto.
- Identifique los tipos y los esquemas de color de las imágenes.

[Pruebe Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) de forma gratuita en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-computervision
```

[Obtenga más información](/azure/cognitive-services/computer-vision/home) acerca de Computer Vision API y empiece a trabajar con la [guía de inicio rápido para JavaScript de Computer Vision API](/azure/cognitive-services/computer-vision/quickstarts/javascript).

### <a name="content-moderator"></a>Content Moderator

Moderación de texto, vídeo e imágenes asistida por máquina, mejorada con herramientas de revisión humanas.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-contentmoderator
```

[Obtenga más información](/azure/cognitive-services/content-moderator/overview) acerca del servicio Content Moderator.

### <a name="face-api"></a>Face API

Detecte, identifique, analice, organice y etiquete las caras en las fotos. 

[Pruebe Face API](https://azure.microsoft.com/services/cognitive-services/face/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-face
```

[Obtenga más información](/azure/cognitive-services/face/overview) acerca de Face API y empiece a trabajar con la [guía de inicio rápido para JavaScript de Face API](/azure/cognitive-services/Face/quickstarts/javascript).

## <a name="search-modules"></a>Módulos de búsqueda

### <a name="web-search"></a>Búsqueda web

Recupere documentos web indexados por Bing Web Search API y limite los resultados según el tipo, la actualidad y muchos otros criterios. 

[Pruebe Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-websearch
```

[Obtenga más información](/azure/cognitive-services/bing-web-search/overview) acerca de Bing Web Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Web Search API](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).

### <a name="image-search"></a>Búsqueda de imágenes

Busque imágenes y obtenga vistas en miniatura, direcciones URL completas de imágenes, metadatos de imagen y mucho más en los resultados.

[Pruebe Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-imagesearch
```

[Obtenga más información](/azure/cognitive-services/bing-image-search/overview) acerca de Bing Image Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Image Search API](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).


### <a name="entity-search"></a>Búsqueda de entidades

Busque la entidad más pertinente (lugar, persona o cosa) para un término de búsqueda o una ubicación determinados.

[Pruebe Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-entitysearch
```

[Obtenga más información](/azure/cognitive-services/bing-entities-search/search-the-web) acerca de Bing Entity Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Entity Search API](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).

### <a name="custom-search"></a>Búsqueda personalizada

Cree una búsqueda web personalizada que cumpla los requisitos específicos de su dominio de búsqueda.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-customsearch
```

[Obtenga más información](/azure/cognitive-services/bing-custom-search/) acerca del servicio Bing Custom Search y empiece a trabajar con consultas sobre su búsqueda personalizada desde sus aplicaciones con la [guía de inicio rápido para Node.js de Custom Search API](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).

### <a name="video-search"></a>Búsqueda de vídeos

Busque vídeos en Internet y obtenga resultados con metadatos del creador, codificación, duración y número de visualizaciones.

[Pruebe Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-videosearch
```

[Obtenga más información](/azure/cognitive-services/bing-video-search/search-the-web) acerca del servicio Bing Video Search y empiece a trabajar con la [guía de inicio rápido para Node.js de Video Search API](/azure/cognitive-services/bing-video-search/nodejs).


### <a name="news-search"></a>Búsqueda de noticias

Busque en Internet artículos de noticias y trabaje con los metadatos del artículo, noticias relacionadas, imágenes e información del proveedor.

[Pruebe News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-newssearch
```

[Obtenga más información](/azure/cognitive-services/bing-news-search/search-the-web) acerca del servicio Bing News Search y empiece a trabajar con la [guía de inicio rápido para JavaScript de News Search API](/azure/cognitive-services/bing-news-search/nodejs).


## <a name="language-modules"></a>Modelo de lenguaje

### <a name="text-analytics"></a>Text Analytics 

Text Analytics API es un servicio en la nube que realiza el procesamiento del lenguaje natural en textos sin formato. La API incluye tres funciones principales:

- análisis de opiniones
- Extracción de la frase clave
- Detección de idiomas

[Pruebe Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-textanalytics
```

[Obtenga más información](/azure/cognitive-services/text-analytics/overview) acerca de Text Analytics API y empiece a trabajar con la [guía de inicio rápido para Node.js de Text Analytics API](/azure/cognitive-services/text-analytics/quickstarts/nodejs).


### <a name="spell-check"></a>Corrector ortográfico

Compruebe la gramática y la ortografía en contexto con Bing Spell Check API.

[Pruebe Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) en su explorador.

Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-spellcheck
```

[Obtenga más información](/azure/cognitive-services/bing-spell-check/proof-text) acerca de Spell Check API y empiece a trabajar con la [guía de inicio rápido para Node.js de Spell Check API](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
