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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071872"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="f2978-103">Módulos de Azure Cognitive Services para JavaScript</span><span class="sxs-lookup"><span data-stu-id="f2978-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="f2978-104">Módulos de visión</span><span class="sxs-lookup"><span data-stu-id="f2978-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="f2978-105">Computer Vision</span><span class="sxs-lookup"><span data-stu-id="f2978-105">Computer Vision</span></span> 

<span data-ttu-id="f2978-106">Devuelve información sobre el contenido visual encontrado en una imagen:</span><span class="sxs-lookup"><span data-stu-id="f2978-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="f2978-107">Use etiquetado, descripciones y modelos específicos del dominio para identificar el contenido y etiquetarlo con confianza.</span><span class="sxs-lookup"><span data-stu-id="f2978-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="f2978-108">Aplique la configuración para adultos para habilitar la restricción automatizada de contenido adulto.</span><span class="sxs-lookup"><span data-stu-id="f2978-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="f2978-109">Identifique los tipos y los esquemas de color de las imágenes.</span><span class="sxs-lookup"><span data-stu-id="f2978-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="f2978-110">[Pruebe Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) de forma gratuita en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="f2978-111">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="f2978-112">[Obtenga más información](/azure/cognitive-services/computer-vision/home) acerca de Computer Vision API y empiece a trabajar con la [guía de inicio rápido para JavaScript de Computer Vision API](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="f2978-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="f2978-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="f2978-113">Content Moderator</span></span>

<span data-ttu-id="f2978-114">Moderación de texto, vídeo e imágenes asistida por máquina, mejorada con herramientas de revisión humanas.</span><span class="sxs-lookup"><span data-stu-id="f2978-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="f2978-115">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="f2978-116">[Obtenga más información](/azure/cognitive-services/content-moderator/overview) acerca del servicio Content Moderator.</span><span class="sxs-lookup"><span data-stu-id="f2978-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="f2978-117">Face API</span><span class="sxs-lookup"><span data-stu-id="f2978-117">Face API</span></span>

<span data-ttu-id="f2978-118">Detecte, identifique, analice, organice y etiquete las caras en las fotos.</span><span class="sxs-lookup"><span data-stu-id="f2978-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="f2978-119">[Pruebe Face API](https://azure.microsoft.com/services/cognitive-services/face/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="f2978-120">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="f2978-121">[Obtenga más información](/azure/cognitive-services/face/overview) acerca de Face API y empiece a trabajar con la [guía de inicio rápido para JavaScript de Face API](/azure/cognitive-services/Face/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="f2978-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="f2978-122">Módulos de búsqueda</span><span class="sxs-lookup"><span data-stu-id="f2978-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="f2978-123">Búsqueda web</span><span class="sxs-lookup"><span data-stu-id="f2978-123">Web search</span></span>

<span data-ttu-id="f2978-124">Recupere documentos web indexados por Bing Web Search API y limite los resultados según el tipo, la actualidad y muchos otros criterios.</span><span class="sxs-lookup"><span data-stu-id="f2978-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="f2978-125">[Pruebe Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="f2978-126">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="f2978-127">[Obtenga más información](/azure/cognitive-services/bing-web-search/overview) acerca de Bing Web Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Web Search API](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="f2978-128">Búsqueda de imágenes</span><span class="sxs-lookup"><span data-stu-id="f2978-128">Image search</span></span>

<span data-ttu-id="f2978-129">Busque imágenes y obtenga vistas en miniatura, direcciones URL completas de imágenes, metadatos de imagen y mucho más en los resultados.</span><span class="sxs-lookup"><span data-stu-id="f2978-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="f2978-130">[Pruebe Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="f2978-131">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="f2978-132">[Obtenga más información](/azure/cognitive-services/bing-image-search/overview) acerca de Bing Image Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Image Search API](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="f2978-133">Búsqueda de entidades</span><span class="sxs-lookup"><span data-stu-id="f2978-133">Entity search</span></span>

<span data-ttu-id="f2978-134">Busque la entidad más pertinente (lugar, persona o cosa) para un término de búsqueda o una ubicación determinados.</span><span class="sxs-lookup"><span data-stu-id="f2978-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="f2978-135">[Pruebe Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="f2978-136">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="f2978-137">[Obtenga más información](/azure/cognitive-services/bing-entities-search/search-the-web) acerca de Bing Entity Search API y empiece a trabajar con la [guía de inicio rápido para Node.js de Entity Search API](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="f2978-138">Búsqueda personalizada</span><span class="sxs-lookup"><span data-stu-id="f2978-138">Custom search</span></span>

<span data-ttu-id="f2978-139">Cree una búsqueda web personalizada que cumpla los requisitos específicos de su dominio de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="f2978-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="f2978-140">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="f2978-141">[Obtenga más información](/azure/cognitive-services/bing-custom-search/) acerca del servicio Bing Custom Search y empiece a trabajar con consultas sobre su búsqueda personalizada desde sus aplicaciones con la [guía de inicio rápido para Node.js de Custom Search API](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="f2978-142">Búsqueda de vídeos</span><span class="sxs-lookup"><span data-stu-id="f2978-142">Video search</span></span>

<span data-ttu-id="f2978-143">Busque vídeos en Internet y obtenga resultados con metadatos del creador, codificación, duración y número de visualizaciones.</span><span class="sxs-lookup"><span data-stu-id="f2978-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="f2978-144">[Pruebe Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="f2978-145">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="f2978-146">[Obtenga más información](/azure/cognitive-services/bing-video-search/search-the-web) acerca del servicio Bing Video Search y empiece a trabajar con la [guía de inicio rápido para Node.js de Video Search API](/azure/cognitive-services/bing-video-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="f2978-147">Búsqueda de noticias</span><span class="sxs-lookup"><span data-stu-id="f2978-147">News search</span></span>

<span data-ttu-id="f2978-148">Busque en Internet artículos de noticias y trabaje con los metadatos del artículo, noticias relacionadas, imágenes e información del proveedor.</span><span class="sxs-lookup"><span data-stu-id="f2978-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="f2978-149">[Pruebe News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="f2978-150">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="f2978-151">[Obtenga más información](/azure/cognitive-services/bing-news-search/search-the-web) acerca del servicio Bing News Search y empiece a trabajar con la [guía de inicio rápido para JavaScript de News Search API](/azure/cognitive-services/bing-news-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="f2978-152">Modelo de lenguaje</span><span class="sxs-lookup"><span data-stu-id="f2978-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="f2978-153">Text Analytics</span><span class="sxs-lookup"><span data-stu-id="f2978-153">Text Analytics</span></span> 

<span data-ttu-id="f2978-154">Text Analytics API es un servicio en la nube que realiza el procesamiento del lenguaje natural en textos sin formato.</span><span class="sxs-lookup"><span data-stu-id="f2978-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="f2978-155">La API incluye tres funciones principales:</span><span class="sxs-lookup"><span data-stu-id="f2978-155">The API includes three main functions:</span></span>

- <span data-ttu-id="f2978-156">análisis de opiniones</span><span class="sxs-lookup"><span data-stu-id="f2978-156">Sentiment analysis</span></span>
- <span data-ttu-id="f2978-157">Extracción de la frase clave</span><span class="sxs-lookup"><span data-stu-id="f2978-157">Key phrase extraction</span></span>
- <span data-ttu-id="f2978-158">Detección de idiomas</span><span class="sxs-lookup"><span data-stu-id="f2978-158">Language detection</span></span>

<span data-ttu-id="f2978-159">[Pruebe Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="f2978-160">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="f2978-161">[Obtenga más información](/azure/cognitive-services/text-analytics/overview) acerca de Text Analytics API y empiece a trabajar con la [guía de inicio rápido para Node.js de Text Analytics API](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="f2978-162">Corrector ortográfico</span><span class="sxs-lookup"><span data-stu-id="f2978-162">Spell Check</span></span>

<span data-ttu-id="f2978-163">Compruebe la gramática y la ortografía en contexto con Bing Spell Check API.</span><span class="sxs-lookup"><span data-stu-id="f2978-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="f2978-164">[Pruebe Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) en su explorador.</span><span class="sxs-lookup"><span data-stu-id="f2978-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="f2978-165">Obtención del módulo de JavaScript con [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="f2978-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="f2978-166">[Obtenga más información](/azure/cognitive-services/bing-spell-check/proof-text) acerca de Spell Check API y empiece a trabajar con la [guía de inicio rápido para Node.js de Spell Check API](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2978-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="f2978-167">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="f2978-167">Samples</span></span>

<span data-ttu-id="f2978-168">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f2978-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
