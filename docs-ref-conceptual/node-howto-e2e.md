---
title: Desarrollo de Node.js con Visual Studio Code y Azure
description: "Completo tutorial que ilustra cómo crear, incluir en un contenedor Docker e implementar en Azure una aplicación Node.js."
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="f2984-103">Desarrollo de Node.js con Visual Studio Code y Azure</span><span class="sxs-lookup"><span data-stu-id="f2984-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="f2984-104">En este tutorial se muestra cómo tomar una aplicación Node.js existente, incluirla en un contenedor Docker e implementarla en Azure mediante Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="f2984-105">El tutorial utiliza una aplicación simple de lista de tareas creada y publicada por [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span><span class="sxs-lookup"><span data-stu-id="f2984-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="f2984-106">Es una aplicación MEAN de una página y, por lo tanto, usa MongoDB como base de datos, Node/Express para la API de RESTy servidor web y Angular.js 1.x para la interfaz de usuario de front-end.</span><span class="sxs-lookup"><span data-stu-id="f2984-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f2984-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f2984-107">Prerequisites</span></span>

<span data-ttu-id="f2984-108">Para proseguir con la demostración, debe tener instalado el software siguiente:</span><span class="sxs-lookup"><span data-stu-id="f2984-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="f2984-109">código de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2984-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="f2984-110">Docker</span><span class="sxs-lookup"><span data-stu-id="f2984-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="f2984-111">Cuenta de DockerHub</span><span class="sxs-lookup"><span data-stu-id="f2984-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="f2984-112">CLI de Azure 2.0</span><span class="sxs-lookup"><span data-stu-id="f2984-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="f2984-113">Cuenta de Azure</span><span class="sxs-lookup"><span data-stu-id="f2984-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="f2984-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="f2984-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="f2984-115">[Chrome](https://www.google.com/chrome/browser/desktop/): se usa para depurar el front-end de la aplicación de demostración.</span><span class="sxs-lookup"><span data-stu-id="f2984-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="f2984-116">MongoDB: debido a que la aplicación de demostración utiliza MongoDB, debe tener una instancia de MongoDB que se ejecute localmente y que está escuchando en el puerto estándar `27017`.</span><span class="sxs-lookup"><span data-stu-id="f2984-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="f2984-117">La manera más sencilla de lograrlo es mediante la ejecución de los dos comandos siguientes después de instalar Docker: `docker pull mongo` seguido de `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="f2984-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="f2984-118">Configuración del proyecto</span><span class="sxs-lookup"><span data-stu-id="f2984-118">Project setup</span></span>

<span data-ttu-id="f2984-119">Para empezar, descargue el proyecto de ejemplo mediante los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f2984-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="f2984-120">Abra Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="f2984-121">Presione **&lt;F1>** para mostrar la paleta de comandos.</span><span class="sxs-lookup"><span data-stu-id="f2984-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="f2984-122">En el símbolo de la paleta de comandos, escriba `gitcl`, seleccione el comando **Git: Clone** y presione **&lt;Entrar>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Comando gitcl en el símbolo de la paleta de comandos de Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="f2984-124">Cuando se le solicite la **dirección URL de repositorio**, escriba `https://github.com/scotch-io/node-todo` y presione  **&lt;Entrar>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="f2984-125">Seleccione el directorio local en el que va a clonar el proyecto, o créelo.</span><span class="sxs-lookup"><span data-stu-id="f2984-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Explorador de Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="f2984-127">Terminal integrado</span><span class="sxs-lookup"><span data-stu-id="f2984-127">Integrated terminal</span></span>

<span data-ttu-id="f2984-128">Como es un proyecto Node.js, lo primero que debe hacer es asegurarse de que todas las dependencias del proyecto se instalan desde npm.</span><span class="sxs-lookup"><span data-stu-id="f2984-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="f2984-129">Presione **&lt;Ctrl>'** para mostrar el terminal integrado de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="f2984-130">Escriba `yarn` y presione **&lt;Entrar>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Ejecute el comando yarn dentro de Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="f2984-132">Control de versiones Git integrado</span><span class="sxs-lookup"><span data-stu-id="f2984-132">Integrated Git version control</span></span>

<span data-ttu-id="f2984-133">Después de instalar las dependencias de la aplicación a través de Yarn, se crea un archivo `yarn.lock` que proporciona una manera predecible de volver a adquirir las mismas dependencias exactas en el futuro, sin sorpresas en las compilaciones de integración continua, implementaciones de producción o en otros equipos de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="f2984-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="f2984-134">Los siguientes pasos muestran cómo comprobar el archivo `yarn.lock` en el control de código fuente:</span><span class="sxs-lookup"><span data-stu-id="f2984-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="f2984-135">En Visual Studio Code, cambie a la pestaña de Git integrada (la pestaña con el logotipo Git).</span><span class="sxs-lookup"><span data-stu-id="f2984-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="f2984-136">En el cuadro **Mensaje**, escriba un mensaje de confirmación y presione **&lt;Ctrl>&lt;Entrar>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Adición del archivo yarn.lock a Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="f2984-138">Navegación del proyecto y código</span><span class="sxs-lookup"><span data-stu-id="f2984-138">Project and code navigation</span></span>

<span data-ttu-id="f2984-139">Para orientarnos en el código base, vamos a ver algunos ejemplos de algunas de las funcionalidades de navegación que proporciona Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="f2984-140">Presione **&lt;Ctrl>P**.</span><span class="sxs-lookup"><span data-stu-id="f2984-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="f2984-141">Escriba `.js` para mostrar todos los archivos JavaScript/JSON en el proyecto junto con el directorio principal de cada archivo.</span><span class="sxs-lookup"><span data-stu-id="f2984-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Mostrar todos los archivos .js*](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="f2984-143">Seleccione `server.js`, que es el script de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="f2984-144">Mantenga el puntero sobre la variable **base de datos** (importada en la línea 6) para ver su tipo.</span><span class="sxs-lookup"><span data-stu-id="f2984-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="f2984-145">Esta capacidad de inspeccionar rápidamente variables/módulos/tipos en un archivo es muy útil durante el desarrollo de los proyectos.</span><span class="sxs-lookup"><span data-stu-id="f2984-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Detectar tipo](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="f2984-147">Si hace clic en el mouse dentro del intervalo de una variable, como **database**, le permite ver todas las referencias a esa variable dentro del mismo archivo.</span><span class="sxs-lookup"><span data-stu-id="f2984-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="f2984-148">Para ver todas las referencias a una variable dentro del proyecto, haga clic con el botón derecho en la variable y, en el menú contextual, seleccione **Buscar todas las referencias**.</span><span class="sxs-lookup"><span data-stu-id="f2984-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Buscar referencias a una variable](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="f2984-150">Además de mantener el puntero sobre una variable para descubrir su tipo, puede inspeccionar la definición de una variable, incluso si se encuentra en otro archivo.</span><span class="sxs-lookup"><span data-stu-id="f2984-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="f2984-151">Para ver esto en acción, haga clic con el botón derecho en **database.localUrl** (línea 12) y, en el menú contextual, seleccione **Ver la definición**.</span><span class="sxs-lookup"><span data-stu-id="f2984-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Ver la definición de una variable](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="f2984-153">Modificación del código y uso de la característica de autocompletar</span><span class="sxs-lookup"><span data-stu-id="f2984-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="f2984-154">La cadena de conexión de MongoDB está codificada de forma rígida en la declaración de la variable **database.localUrl**.</span><span class="sxs-lookup"><span data-stu-id="f2984-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="f2984-155">En esta sección, va a modificar el código para recuperar la cadena de conexión de una variable de entorno y aprenderá sobre la característica de autocompletar de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="f2984-156">Abra el archivo `server.js`.</span><span class="sxs-lookup"><span data-stu-id="f2984-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="f2984-157">Reemplace el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="f2984-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="f2984-158">por este otro:</span><span class="sxs-lookup"><span data-stu-id="f2984-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="f2984-159">Tenga en cuenta que si escribe el código de forma manual (en lugar de copiar y pegar), cuando se escribe un punto después `process`, Visual Studio Code muestra los miembros disponibles de la API global de **proceso** de Node.js.</span><span class="sxs-lookup"><span data-stu-id="f2984-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![La característica de autocompletar muestra automáticamente los miembros de una API](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="f2984-161">La característica de autocompletar funciona porque Visual Studio Code usa TypeScript en segundo plano (incluso para JavaScript) con el fin de proporcionar información de tipo que puede utilizarse para informar a la lista de finalización a medida que escribe.</span><span class="sxs-lookup"><span data-stu-id="f2984-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="f2984-162">Visual Studio Code es capaz de detectar que se trata de un proyecto Node.js y, como resultado, se descarga automáticamente el archivo typings de TypeScript para [Node.js desde NPM](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="f2984-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="f2984-163">El archivo typings le permite obtener la función de autocompletar para otras funciones globales de Node.js (como **Buffer** y **setTimeout**), así como para todos los módulos integrados como **fs** y **http**.</span><span class="sxs-lookup"><span data-stu-id="f2984-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="f2984-164">Además de las API de Node.js integradas, esta adquisición automática del archivo typings también funciona con más de 2000 módulos de terceros, como React, Underscore y Express.</span><span class="sxs-lookup"><span data-stu-id="f2984-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="f2984-165">Por ejemplo, para impedir que Mongoose bloquee la aplicación de ejemplo si no puede conectarse a la instancia de base de datos de MongoDB configurada, inserte la siguiente línea de código en la línea 13:</span><span class="sxs-lookup"><span data-stu-id="f2984-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="f2984-166">Al igual que con el código anterior, observará se autocompletará sin ningún trabajo por su parte.</span><span class="sxs-lookup"><span data-stu-id="f2984-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![La característica de autocompletar muestra automáticamente los miembros de una API](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="f2984-168">Puede ver qué módulos son compatibles con esta funcionalidad de autocompletar al examinar el proyecto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), que es el código fuente orientado a la comunidad de todas las definiciones de tipos de TypeScript.</span><span class="sxs-lookup"><span data-stu-id="f2984-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="f2984-169">Ejecución de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f2984-169">Running the app</span></span>

<span data-ttu-id="f2984-170">Cuando haya explorado un poco el código, es el momento de ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="f2984-171">Para ejecutar la aplicación desde Visual Studio Code, presione **&lt;F5>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="f2984-172">Cuando se ejecuta el código a través de **&lt;F5>** (modo de depuración), Visual Studio Code inicia la aplicación y muestra la ventana **Consola de depuración** que muestra el stdout de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Supervisión del stdout de una aplicación a través de la consola de depuración](./media/node-howto-e2e/console.png)

<span data-ttu-id="f2984-174">Además, la **Consola de depuración** se adjunta a la aplicación en ejecución recientemente para que pueda escribir expresiones de JavaScript, que se evaluará en la aplicación y también incluye características de autocompletar.</span><span class="sxs-lookup"><span data-stu-id="f2984-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="f2984-175">Para ver esto en acción, escriba `process.env` en la consola:</span><span class="sxs-lookup"><span data-stu-id="f2984-175">To see this in action, type `process.env` in the console:</span></span>

![Escritura de código en la Consola de depuración](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="f2984-177">Puede presionar **&lt;F5>** para ejecutar la aplicación porque el archivo abierto actualmente es un archivo JavaScript (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="f2984-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="f2984-178">Como resultado, Visual Studio Code asume que el proyecto es una aplicación Node.js.</span><span class="sxs-lookup"><span data-stu-id="f2984-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="f2984-179">Si cierra todos los archivos JavaScript de Visual Studio Code y después presiona **&lt;F5>**, Visual Studio Code le consultará el entorno:</span><span class="sxs-lookup"><span data-stu-id="f2984-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Especificación del entorno en tiempo de ejecución](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="f2984-181">Abra un explorador y vaya a `http://localhost:8080` para ver la aplicación en ejecución.</span><span class="sxs-lookup"><span data-stu-id="f2984-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="f2984-182">Escriba un mensaje en el cuadro de texto y agregue o quite alguna lista de tareas para hacerse una idea de cómo funciona la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![Ejecución de la aplicación de lista de tareas](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="f2984-184">Depuración</span><span class="sxs-lookup"><span data-stu-id="f2984-184">Debugging</span></span>

<span data-ttu-id="f2984-185">Además de poder ejecutar la aplicación e interactuar con ella a través de la consola integrada, Visual Studio Code proporciona la capacidad de establecer puntos de interrupción directamente dentro del código.</span><span class="sxs-lookup"><span data-stu-id="f2984-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="f2984-186">Por ejemplo, presione **&lt;Ctrl> P** para mostrar el selector de archivos.</span><span class="sxs-lookup"><span data-stu-id="f2984-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="f2984-187">Cuando se muestre el selector de archivos, escriba `route` y seleccione el archivo `route.js`.</span><span class="sxs-lookup"><span data-stu-id="f2984-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="f2984-188">Establezca un punto de interrupción en la línea 28, que representa la ruta de Express que se llama cuando la aplicación intenta agregar una entrada a la lista de tareas.</span><span class="sxs-lookup"><span data-stu-id="f2984-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="f2984-189">Para establecer un punto de interrupción, simplemente haga clic en el área situada a la izquierda del número de línea en el editor, tal como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2984-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Establecimiento de un punto de interrupción en Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="f2984-191">Además de los puntos de interrupción estándares, Visual Studio Code admite puntos de interrupción condicionales que le permiten personalizar cuando la aplicación debe suspender la ejecución.</span><span class="sxs-lookup"><span data-stu-id="f2984-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="f2984-192">Para establecer un punto de interrupción condicional, haga clic con el botón derecho en el área situada a la izquierda de la línea en la que desea detener la ejecución, seleccione **Agregar punto de interrupción condicional...** y especifique una expresión de JavaScript (p. ej. `foo = "bar"`) o el número de ejecución que define la condición bajo la que desea pausar la ejecución.</span><span class="sxs-lookup"><span data-stu-id="f2984-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="f2984-193">Una vez establecido el punto de interrupción, vuelva a la aplicación en ejecución y agregue una entrada a la lista de tareas.</span><span class="sxs-lookup"><span data-stu-id="f2984-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="f2984-194">Si agrega una entrada a la lista de tareas inmediatamente, hará que la aplicación suspenda la ejecución en la línea 28 en la que estableció el punto de interrupción:</span><span class="sxs-lookup"><span data-stu-id="f2984-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Ejecución de Visual Studio Code en pausa en un punto de interrupción](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="f2984-196">Cuando se ha detenido la aplicación, mantenga el puntero sobre expresiones del código para ver su valor actual, inspeccione las variables locales e inspecciones y la pila de llamadas, y use la barra de herramientas de depuración para recorrer la ejecución del código.</span><span class="sxs-lookup"><span data-stu-id="f2984-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="f2984-197">Presione **&lt;F5>** para reanudar la ejecución de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="f2984-198">Depuración de pila completa</span><span class="sxs-lookup"><span data-stu-id="f2984-198">Full-stack debugging</span></span>

<span data-ttu-id="f2984-199">Como se mencionó anteriormente en este tema, la aplicación de la lista de tareas es una aplicación MEAN, lo que significa que su front-end y back-end están ambos escritos con JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f2984-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="f2984-200">Por lo tanto, mientras está depurando el código de back-end (Node/Express), en algún momento debe depurar el código de front-end (Angular).</span><span class="sxs-lookup"><span data-stu-id="f2984-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="f2984-201">Para ello, Visual Studio Code tiene un enorme ecosistema de extensiones, incluida la depuración de Chrome integrada.</span><span class="sxs-lookup"><span data-stu-id="f2984-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="f2984-202">Cambie a la pestaña **Extensiones** y escriba `chrome` en el cuadro de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="f2984-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Extensión de depuración de Chrome para Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="f2984-204">Seleccione la extensión denominada **Debugger for Chrome** (Depurador para Chrome) y seleccione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="f2984-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="f2984-205">Después de instalar la extensión de depuración de Chrome, seleccione **Recargar** para cerrar y volver a abrir Visual Studio Code para activar la extensión.</span><span class="sxs-lookup"><span data-stu-id="f2984-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Recarga de Visual Studio Code después de instalar la extensión de depuración de Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="f2984-207">Mientras se podía ejecutar y depurar el código de Node.js sin ninguna configuración específica de Visual Studio Code, para depurar una aplicación web de front-end, debe generar un archivo `launch.json` que indica a Visual Studio Code cómo ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="f2984-208">Para generar el archivo `launch.json`, cambie a la pestaña **Depurar**, haga clic en el icono de engranaje (que debe tener un pequeño punto rojo en la parte superior) y seleccione el entorno **node.js**.</span><span class="sxs-lookup"><span data-stu-id="f2984-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Opción de Visual Studio Code para configurar el archivo de launch.json](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="f2984-210">Una vez creado, el archivo `launch.json` tiene un aspecto similar al siguiente e indica a Visual Studio Code cómo iniciar o asociar a la aplicación para depurarla.</span><span class="sxs-lookup"><span data-stu-id="f2984-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

<span data-ttu-id="f2984-211">Tenga en cuenta que Visual Studio Code era capaz de detectar que el script de inicio de la aplicación es `server.js`.</span><span class="sxs-lookup"><span data-stu-id="f2984-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="f2984-212">Con archivo `launch.json` abierto, seleccione **Agregar configuración** (parte inferior derecha) y seleccione **Chrome: Launch with userDataDir** (Chrome: iniciar con userDataDir).</span><span class="sxs-lookup"><span data-stu-id="f2984-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Adición de una configuración de Chrome a Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="f2984-214">Si se agrega una nueva configuración de ejecución para Chrome, podrá depurar el código de JavaScript de front-end.</span><span class="sxs-lookup"><span data-stu-id="f2984-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="f2984-215">Puede mantener el puntero sobre cualquiera de las opciones que se especifican para ver la documentación sobre lo que hace la configuración.</span><span class="sxs-lookup"><span data-stu-id="f2984-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="f2984-216">Además, tenga en cuenta que Visual Studio Code detecta automáticamente la dirección URL de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="f2984-217">Actualice la propiedad **webRoot** a `${workspaceRoot}/public` para que el depurador de Chrome sepa dónde encontrar los recursos de front-end de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="f2984-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

<span data-ttu-id="f2984-218">Para iniciar o debug tanto el front-end como el back-end al mismo tiempo, tiene que crear una configuración de ejecución *compuesta* que indica a Visual Studio Code el conjunto de configuraciones que se van a ejecutar en paralelo.</span><span class="sxs-lookup"><span data-stu-id="f2984-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="f2984-219">Agregue el siguiente fragmento de código como una propiedad de nivel superior dentro del archivo `launch.json` (como un elemento del mismo nivel de la propiedad **configurations** existente).</span><span class="sxs-lookup"><span data-stu-id="f2984-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="f2984-220">Los valores de cadena especificados en la matriz **compounds.configurations** hacen referencia al **nombre** de las entradas individuales de la lista de **configurations**.</span><span class="sxs-lookup"><span data-stu-id="f2984-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="f2984-221">Si ha modificarse esos nombres, debe realizar los cambios apropiados en la matriz.</span><span class="sxs-lookup"><span data-stu-id="f2984-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="f2984-222">Para ver esto en acción, cambie a la pestaña Depurar y cambie la configuración seleccionada para **Full-Stack** (el nombre de la configuración compuesta) y presione **&lt;F5>** para ejecutarla.</span><span class="sxs-lookup"><span data-stu-id="f2984-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Ejecución de una configuración en Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="f2984-224">Si se ejecuta la configuración, se inicia la aplicación Node.js (como puede verse en la salida de la consola de depuración) y Chrome (configurado para navegar a la aplicación Node.js en `http://localhost:8080`).</span><span class="sxs-lookup"><span data-stu-id="f2984-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="f2984-225">Presione **&lt;Ctrl> P** y escriba (o seleccione) `todos.js`, que es el controlador principal de Angular para el front-end de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="f2984-226">Establezca un punto de interrupción en la línea 11, que es el punto de entrada para una nueva entrada de lista de tareas que se está creando.</span><span class="sxs-lookup"><span data-stu-id="f2984-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="f2984-227">Vuelva a la aplicación en ejecución, agregue una nueva entrada de lista de tareas y tenga en cuenta que Visual Studio Code ahora ha suspendido la ejecución dentro del código Angular.</span><span class="sxs-lookup"><span data-stu-id="f2984-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Depuración de código de front-end en Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="f2984-229">Similar a la depuración de Node.js, puede mantener el puntero sobre las expresiones, ver las variables locales e inspecciones, evaluar las expresiones en la consola y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="f2984-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="f2984-230">Hay dos aspectos importantes que deben tenerse en cuenta:</span><span class="sxs-lookup"><span data-stu-id="f2984-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="f2984-231">El panel **Pila de llamadas** muestra dos pilas diferentes: **Node** y **Chrome** e indica cuál es la que está actualmente en pausa.</span><span class="sxs-lookup"><span data-stu-id="f2984-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="f2984-232">Puede pasar entre el código de front-end y back-end.</span><span class="sxs-lookup"><span data-stu-id="f2984-232">You can step between front and back-end code.</span></span> <span data-ttu-id="f2984-233">Para probarlo, presione **&lt;F5>**, que ejecutará el punto de interrupción previamente establecido en la ruta de Express.</span><span class="sxs-lookup"><span data-stu-id="f2984-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="f2984-234">Con esta configuración, ahora puede depurar eficazmente el código de JavaScript de pila completa, de front-end y back-end directamente en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="f2984-235">Además, el concepto de depurador compuesto no está limitado únicamente a dos procesos de destino y además no está limitado a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f2984-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="f2984-236">Por tanto, si funciona en una aplicación de microservicio (que sea potencialmente políglota), puede usar el mismo flujo de trabajo (una vez que haya instalado las extensiones correspondientes para el lenguaje o plataforma).</span><span class="sxs-lookup"><span data-stu-id="f2984-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="f2984-237">Inclusión de la aplicación en un contenedor Docker</span><span class="sxs-lookup"><span data-stu-id="f2984-237">Dockerizing the app</span></span>

<span data-ttu-id="f2984-238">Esta sección se centra en la experiencia que proporciona Visual Studio Code para el desarrollo con [Docker](https://www.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="f2984-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="f2984-239">Los desarrolladores de Node.js usan Docker para proporcionar implementaciones de aplicaciones portátiles para los entornos de desarrollo, integración continua y de producción.</span><span class="sxs-lookup"><span data-stu-id="f2984-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="f2984-240">Como Docker presenta que fuerte curva de aprendizaje para algunos, Visual Studio Code ofrece una extensión que ayuda a simplificar el uso de Docker en las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f2984-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="f2984-241">Vuelva a la pestaña **Extensiones**, busque `docker` y seleccione la extensión **Docker**.</span><span class="sxs-lookup"><span data-stu-id="f2984-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="f2984-242">Instale la extensión Docker y vuelva a cargar Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Instalación de la extensión de Docker para Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="f2984-244">La extensión Docker para Visual Studio Code incluye un comando para generar un *Dockerfile* y el archivo `docker-compose.yml` para un proyecto existente.</span><span class="sxs-lookup"><span data-stu-id="f2984-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="f2984-245">Para ver los comandos de Docker disponibles, muestre la paleta de comandos (a través de **&lt;F1>**) y escriba `docker`.</span><span class="sxs-lookup"><span data-stu-id="f2984-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="f2984-246">Comandos admitidos por la extensión Docker para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2984-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="f2984-247">Seleccione **Docker: Add docker files to workspace** (Docker: Agregar archivos de docker al área de trabajo), seleccione **Node.js** como la plataforma de aplicación y especifique que la aplicación expone el puerto `8080`.</span><span class="sxs-lookup"><span data-stu-id="f2984-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="f2984-248">El comando de Docker genera un `Dockerfile` completo y archivos docker-compose que puede empezar a usar inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="f2984-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Dockerfile generado](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="f2984-250">La extensión Docker también proporciona características de autocompletar para sus archivo `Dockerfiles` y `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="f2984-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="f2984-251">Para ver esto en acción, abra el `Dockerfile` y cambie la línea 2 de:</span><span class="sxs-lookup"><span data-stu-id="f2984-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="f2984-252">Por:</span><span class="sxs-lookup"><span data-stu-id="f2984-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="f2984-253">Con el cursor situado después de la `t` en `mhart`, presione **&lt;Ctrl>&lt;espacio>** para ver todos los repositorios de imágenes que `mhart` ha publicado en DockerHub.</span><span class="sxs-lookup"><span data-stu-id="f2984-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Completado automático de la extensión Docker](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="f2984-255">Seleccione `mhart/alpine-node`, que proporciona todo lo que necesita esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="f2984-256">Las imágenes más pequeñas suelen ser mejores, ya que quiere que las compilaciones e implementaciones de la aplicación sean lo más rápidas posibles, lo que permite una distribución y un ajuste de escala más rápido.</span><span class="sxs-lookup"><span data-stu-id="f2984-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="f2984-257">Ahora que ha generado el `Dockerfile`, necesita crear la imagen de Docker real.</span><span class="sxs-lookup"><span data-stu-id="f2984-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="f2984-258">Una vez más, puede usar un comando que ha instalado la extensión Docker en Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2984-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="f2984-259">Presione **&lt;F1>**, escriba `dockerb` en la paleta de comandos y seleccione el comando **Docker: Build Image** (Docker: Crear imagen).</span><span class="sxs-lookup"><span data-stu-id="f2984-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="f2984-260">Elija la `/Dockerfile` que acaba de generar y modificar.</span><span class="sxs-lookup"><span data-stu-id="f2984-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="f2984-261">Especifique una etiqueta que incluya el nombre de usuario de DockerHub (p. ej. `lostintangent/node`).</span><span class="sxs-lookup"><span data-stu-id="f2984-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="f2984-262">Presione **&lt;ENTRAR>** para iniciar la ventana del terminal integrado, que muestra la salida de la imagen de Docker que se está creando.</span><span class="sxs-lookup"><span data-stu-id="f2984-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Estado de creación de la imagen de Docker](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="f2984-264">Observe que el comando ha automatizado el proceso de ejecución `docker build`, lo que representa otro ejemplo de un optimizador de productividad que puede usar o bien puede utilizar directamente la CLI de Docker.</span><span class="sxs-lookup"><span data-stu-id="f2984-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="f2984-265">En este momento, para que esta imagen sea fácilmente asequible para las implementaciones, solo necesita insertar la imagen en DockerHub.</span><span class="sxs-lookup"><span data-stu-id="f2984-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="f2984-266">Para ello, asegúrese de que ya está autenticado con DockerHub mediante la ejecución de `docker login` desde la CLI y escriba sus credenciales de cuenta.</span><span class="sxs-lookup"><span data-stu-id="f2984-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="f2984-267">Después, en Visual Studio Code, puede abrir la paleta de comandos, escribir `dockerpush` y seleccionar el comando `Docker: Push`.</span><span class="sxs-lookup"><span data-stu-id="f2984-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="f2984-268">Seleccione la etiqueta de imagen que acaba de crear (p. ej. `lostintangent/node`) y presione **&lt;Entrar>**.</span><span class="sxs-lookup"><span data-stu-id="f2984-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="f2984-269">El comando automatiza la llamada de `docker push` y muestra la salida en el terminal integrado.</span><span class="sxs-lookup"><span data-stu-id="f2984-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="f2984-270">Implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f2984-270">Deploying the app</span></span>

<span data-ttu-id="f2984-271">Ahora que se ha incluido la aplicación en un contenedor Docker y se ha insertado en Dockerhub, deberá implementarla en la nube para que todo el mundo pueda verla.</span><span class="sxs-lookup"><span data-stu-id="f2984-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="f2984-272">Para ello, puede usar Azure App Service, que es una oferta de PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="f2984-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="f2984-273">App Service tiene dos funcionalidades pertinentes para los desarrolladores de Node.js:</span><span class="sxs-lookup"><span data-stu-id="f2984-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="f2984-274">Compatibilidad con máquinas virtuales basadas en Linux, lo que reduce las incompatibilidades para aplicaciones creadas con módulos nativos de Node u otras herramientas que es posible que no admitan Windows o que puedan comportarse de manera diferente.</span><span class="sxs-lookup"><span data-stu-id="f2984-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="f2984-275">Compatibilidad con las implementaciones basadas en Docker, que le permite especificar el nombre de la imagen de Docker y permite que App Service extraiga, implemente y escale la imagen automáticamente.</span><span class="sxs-lookup"><span data-stu-id="f2984-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="f2984-276">Para empezar, abra el terminal de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2984-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="f2984-277">Deberá usar la nueva versión 2.0 de la CLI de Azure para administrar su cuenta de Azure y aprovisionar la infraestructura necesaria para ejecutar la aplicación de la lista de tareas.</span><span class="sxs-lookup"><span data-stu-id="f2984-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="f2984-278">Cuando haya iniciado sesión en su cuenta de la CLI usando el comando `az login` (como se mencionó en los requisitos previos), lleve a cabo los pasos siguientes para aprovisionar la instancia de App Service e implementar el contenedor de la aplicación de lista de tareas:</span><span class="sxs-lookup"><span data-stu-id="f2984-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="f2984-279">Cree un grupo de recursos, que se puede considerar como un *espacio de nombres* o *directorio* para ayudar a organizar los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="f2984-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="f2984-280">La opción `-n` se utiliza para especificar el nombre del grupo y puede ser cualquier cosa que desee.</span><span class="sxs-lookup"><span data-stu-id="f2984-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="f2984-281">La opción `-l` indica la ubicación del grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="f2984-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="f2984-282">Mientras esté en versión preliminar, la compatibilidad de App Service en Linux solo estará disponible en regiones seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="f2984-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="f2984-283">Por lo tanto, si no se encuentra en la zona del oeste de EE. UU. y quiere comprobar qué otras regiones están disponibles, ejecute `az appservice list-locations --linux-workers-enabled` desde la CLI para ver las opciones del centro de datos.</span><span class="sxs-lookup"><span data-stu-id="f2984-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="f2984-284">Establezca el grupo de recursos recién creado como el grupo de recursos predeterminado para que pueda continuar usando la CLI sin necesidad de especificar explícitamente el grupo de recursos con cada llamada a la CLI:</span><span class="sxs-lookup"><span data-stu-id="f2984-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="f2984-285">Cree el *plan* de App Service, que administra la creación y el escalado de las máquinas virtuales subyacentes en las que se implementa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2984-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="f2984-286">Una vez más, especifique el valor que desee para la opción `n`.</span><span class="sxs-lookup"><span data-stu-id="f2984-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="f2984-287">La opción --is-linux indica que quiere máquinas virtuales basadas en Linux.</span><span class="sxs-lookup"><span data-stu-id="f2984-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="f2984-288">Sin ella, la CLI se establece de forma predeterminada para aprovisionar las máquinas virtuales basadas en Windows.</span><span class="sxs-lookup"><span data-stu-id="f2984-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="f2984-289">Cree la aplicación web de App Service, que representa la aplicación real de lista de tareas que se ejecutarán en el plan y en el grupo de recursos que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="f2984-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="f2984-290">Se puede considerar que una aplicación web es sinónimo de un proceso o contenedor y el plan es como el host de la máquina virtual o contenedor en el que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="f2984-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="f2984-291">Además, como parte de la creación de la aplicación web, deberá configurarlo para usar la imagen de Docker que se publicó en DockerHub:</span><span class="sxs-lookup"><span data-stu-id="f2984-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="f2984-292">Si en lugar de utilizar un contenedor personalizado prefiere una implementación de Git, consulte el artículo [Creación de una aplicación web de Node.js en Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span><span class="sxs-lookup"><span data-stu-id="f2984-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="f2984-293">Establezca la aplicación web como la instancia de web predeterminada:</span><span class="sxs-lookup"><span data-stu-id="f2984-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="f2984-294">Inicie la aplicación para ver el contenedor implementado, que estará disponible en una dirección URL `*.azurewebsites.net`:</span><span class="sxs-lookup"><span data-stu-id="f2984-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![Aplicación de lista de tareas que se ejecuta en el explorador](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="f2984-296">Puede tardar varios minutos en cargarse la aplicación por primera vez, ya que App Service tiene que extraer la imagen de Docker del DockerHub y volver a iniciarla.</span><span class="sxs-lookup"><span data-stu-id="f2984-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="f2984-297">En este momento, ha implementado y ejecutado la aplicación de lista de tareas.</span><span class="sxs-lookup"><span data-stu-id="f2984-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="f2984-298">Ahora ha implementado la aplicación de lista de tareas.</span><span class="sxs-lookup"><span data-stu-id="f2984-298">You have now deployed the todo app.</span></span> <span data-ttu-id="f2984-299">Sin embargo, el icono de giro indica que la aplicación no se puede conectar a la base de datos.</span><span class="sxs-lookup"><span data-stu-id="f2984-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="f2984-300">Esto es debido al hecho de que se usa una instancia local de MongoDB durante el desarrollo, lo que obviamente no es accesible desde los centros de datos de Azure.</span><span class="sxs-lookup"><span data-stu-id="f2984-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="f2984-301">Como se ha modificado la aplicación para que acepte la cadena de conexión a través de una variable de entorno, solo debe iniciar un servidor de MongoDB y volver a configurar la instancia de App Service para que haga referencia a la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="f2984-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="f2984-302">Esto se muestra en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2984-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="f2984-303">Aprovisionamiento de un servidor de MongoDB</span><span class="sxs-lookup"><span data-stu-id="f2984-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="f2984-304">Aunque puede configurar un servidor de MongoDB, o un conjunto de réplicas, y administrar usted mismo esa infraestructura, Azure proporciona una solución denominada [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span><span class="sxs-lookup"><span data-stu-id="f2984-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="f2984-305">Cosmos DB es una base de datos de NoSQL completamente administrada, con replicación geográfica y de alto rendimiento, que proporciona una capa de compatibilidad con MongoDB.</span><span class="sxs-lookup"><span data-stu-id="f2984-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="f2984-306">Esto significa que puede apuntar una aplicación MEAN existente a él (o cualquier otra herramienta o cliente de MongoDB, como [Studio 3T](https://studio3t.com/)) sin tener que cambiar nada más que la cadena de conexión.</span><span class="sxs-lookup"><span data-stu-id="f2984-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="f2984-307">Los pasos siguientes muestran cómo realizar esto:</span><span class="sxs-lookup"><span data-stu-id="f2984-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="f2984-308">Desde el terminal de Visual Studio Code, ejecute el siguiente comando para crear una instancia compatible con MongoDB del servicio Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="f2984-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="f2984-309">Reemplace el marcador de posición **<NAME>** por un valor único global (Cosmos DB utiliza este nombre para generar la dirección URL del servidor de la base de datos):</span><span class="sxs-lookup"><span data-stu-id="f2984-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="f2984-310">Recupere la cadena de conexión de MongoDB para esta instancia:</span><span class="sxs-lookup"><span data-stu-id="f2984-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="f2984-311">Actualice la variable de entorno **MONGODB_URL** de la aplicación web, para se conecte a la instancia de Cosmos DB recién aprovisionada en lugar de intentar conectarse a un servidor de MongoDB que se ejecuta localmente (y que no existe):</span><span class="sxs-lookup"><span data-stu-id="f2984-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="f2984-312">Regrese al explorador y actualícelo.</span><span class="sxs-lookup"><span data-stu-id="f2984-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="f2984-313">Pruebe a agregar y quitar un elemento de la lista de tareas para demostrar que la aplicación funciona sin necesidad de cambiar nada.</span><span class="sxs-lookup"><span data-stu-id="f2984-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="f2984-314">Establezca la variable de entorno en la instancia de Cosmos DB creada, que está emulando completamente una base de datos de MongoDB.</span><span class="sxs-lookup"><span data-stu-id="f2984-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![Aplicación de demostración después de su conexión a una base de datos](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="f2984-316">Cuando sea necesario, puede cambiar la instancia de Cosmos DB y escalar (o reducir) verticalmente el rendimiento reservado que necesita la instancia de MongoDB y aprovechar así el tráfico agregado sin necesidad de administrar ninguna infraestructura manualmente.</span><span class="sxs-lookup"><span data-stu-id="f2984-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="f2984-317">Además, Cosmos DB indexará automáticamente cada documento y propiedad.</span><span class="sxs-lookup"><span data-stu-id="f2984-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="f2984-318">De este modo, no tiene que generar perfiles de consultas lentas ni ajustar manualmente los índices.</span><span class="sxs-lookup"><span data-stu-id="f2984-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="f2984-319">Solo se necesita el aprovisionamiento y el escalado, y Cosmos DB se encarga del resto.</span><span class="sxs-lookup"><span data-stu-id="f2984-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="f2984-320">Hospedaje de un registro de Docker privado</span><span class="sxs-lookup"><span data-stu-id="f2984-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="f2984-321">DockerHub proporciona una experiencia increíble al distribuir las imágenes de contenedor, pero puede haber escenarios donde preferiría hospedar su propio registro de Docker privado, como de las ventajas de rendimiento o de seguridad y gobierno.</span><span class="sxs-lookup"><span data-stu-id="f2984-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="f2984-322">Para ello, Azure proporciona [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), que permite poner en marcha su propio registro de Docker cuyo almacenamiento de copias de seguridad se encuentra en el mismo centro de datos que la aplicación web (con lo que hace la extracción es más rápida).</span><span class="sxs-lookup"><span data-stu-id="f2984-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="f2984-323">ACR también proporciona un control total sobre el contenido y los controles de acceso, como, por ejemplo, quién puede insertar o extraer imágenes.</span><span class="sxs-lookup"><span data-stu-id="f2984-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="f2984-324">El aprovisionamiento de un registro personalizado puede realizarse con la ejecución del siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="f2984-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="f2984-325">(Reemplace el marcador de posición **<NAME>** por un valor único global que use ACR como valor especificado para generar la dirección URL del servidor de inicio de sesión del registro.</span><span class="sxs-lookup"><span data-stu-id="f2984-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="f2984-326">Aunque este tema de ejemplo utiliza la **cuenta de administrador** para no complicar las cosas, no se recomienda para los registros de producción.</span><span class="sxs-lookup"><span data-stu-id="f2984-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="f2984-327">El comando `az acr create` muestra la dirección URL del servidor de inicio de sesión (a través de la columna `LOGIN SERVER`) que se utiliza para iniciar sesión mediante la CLI de Docker (p. ej. `ninademo.azurecr.io`).</span><span class="sxs-lookup"><span data-stu-id="f2984-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="f2984-328">Además, el comando genera las credenciales de administrador que puede usar para autenticarse con ellas.</span><span class="sxs-lookup"><span data-stu-id="f2984-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="f2984-329">Para recuperar esas credenciales, ejecute el siguiente comando y anote el nombre de usuario y la contraseña mostrados:</span><span class="sxs-lookup"><span data-stu-id="f2984-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="f2984-330">Con las credenciales del paso anterior y el servidor de inicio de sesión individual, puede iniciar sesión en el registro mediante el flujo de trabajo estándar de la CLI de Docker.</span><span class="sxs-lookup"><span data-stu-id="f2984-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="f2984-331">Ahora puede etiquetar el contenedor de Docker para indicar que está asociado a su registro privado mediante el siguiente comando (reemplazando `lostintangent/node` por el nombre que asignó a la imagen del contenedor).</span><span class="sxs-lookup"><span data-stu-id="f2984-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="f2984-332">Por último, inserte la imagen etiquetada en el registro de Docker privado.</span><span class="sxs-lookup"><span data-stu-id="f2984-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="f2984-333">El contenedor ya está almacenado en su propio registro privado y la CLI de Docker le permite seguir trabajando en la misma manera que cuando usaba DockerHub.</span><span class="sxs-lookup"><span data-stu-id="f2984-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="f2984-334">Para indicar a la aplicación web de App Service que incorporar los cambios del registro privado, solo necesita ejecutar el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="f2984-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="f2984-335">Asegúrese de agregar el prefijo `https://` al principio de la opción `-r`.</span><span class="sxs-lookup"><span data-stu-id="f2984-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="f2984-336">Sin embargo, no agregue el prefijo al nombre de la imagen de contenedor.</span><span class="sxs-lookup"><span data-stu-id="f2984-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="f2984-337">Si actualiza la aplicación en el explorador, todo debería parecer y funcionar de la misma forma.</span><span class="sxs-lookup"><span data-stu-id="f2984-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="f2984-338">Sin embargo, ahora se está ejecutando la aplicación a través del registro de Docker privado.</span><span class="sxs-lookup"><span data-stu-id="f2984-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="f2984-339">Una vez actualizada la aplicación, etiquete e inserte los cambios como realizó anteriormente y actualice la etiqueta en la configuración del contenedor de App Service.</span><span class="sxs-lookup"><span data-stu-id="f2984-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="f2984-340">Configuración de un nombre de dominio personalizado</span><span class="sxs-lookup"><span data-stu-id="f2984-340">Configuring a custom domain name</span></span>

<span data-ttu-id="f2984-341">Mientras la dirección URL `*.azurewebsites.net` es muy útil para pruebas, en algún momento puede querer agregar un nombre de dominio personalizado a la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="f2984-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="f2984-342">Cuando tenga un nombre de dominio en un registrador de dominios, solo necesitará agregarle un registro `A` que señala a la IP externa de la aplicación web (que es realmente un equilibrador de carga).</span><span class="sxs-lookup"><span data-stu-id="f2984-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="f2984-343">Puede recuperar esta IP mediante la ejecución del siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="f2984-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="f2984-344">Además de agregar un registro `A`, también debe agregar un registro `TXT` a su dominio que apunta al dominio `*.azurewebsites.net` que ha estado utilizando hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="f2984-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="f2984-345">La combinación de los registros `A` y `TXT` permite a Azure comprobar que posee el dominio.</span><span class="sxs-lookup"><span data-stu-id="f2984-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="f2984-346">Cuando se crean los registros y se han propagado los cambios de DNS, registre el dominio personalizado con Azure para que pueda esperar el tráfico entrante correctamente.</span><span class="sxs-lookup"><span data-stu-id="f2984-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="f2984-347">El comando no funcionará hasta que se hayan propagado los cambios de DNS.</span><span class="sxs-lookup"><span data-stu-id="f2984-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="f2984-348">Abra un explorador y vaya a su dominio personalizado para ver que se resuelve ahora en la aplicación implementada en Azure.</span><span class="sxs-lookup"><span data-stu-id="f2984-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="f2984-349">Escalado vertical y horizontal</span><span class="sxs-lookup"><span data-stu-id="f2984-349">Scaling up and out</span></span>

<span data-ttu-id="f2984-350">En algún momento, la aplicación web puede convertirse en lo suficientemente popular sus recursos asignados (CPU y RAM) no sean ya suficientes para controlar el aumento de demandas de tráfico y operacionales.</span><span class="sxs-lookup"><span data-stu-id="f2984-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="f2984-351">El plan de App Service que creó anteriormente (**B1**) viene con una CPU de 1 núcleo y 1,75 GB de RAM, que puede sobrepasarse con bastante rapidez.</span><span class="sxs-lookup"><span data-stu-id="f2984-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="f2984-352">El plan **B2** incluye el doble de RAM y CPU, por lo que si observa que la aplicación comienza a agotarlos, puede escalar verticalmente la máquina virtual subyacente mediante la ejecución el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="f2984-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="f2984-353">Para obtener información sobre especificaciones y detalles del plan App de Azure, consulte el artículo, [Precios de App Service](https://azure.microsoft.com/pricing/details/app-service/)</span><span class="sxs-lookup"><span data-stu-id="f2984-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="f2984-354">Poco después, la aplicación web se migrará al hardware solicitado y podrá empezar a sacar partido de los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="f2984-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="f2984-355">Además de escalarla verticalmente, también puede reducirla verticalmente mediante la ejecución del mismo comando que antes, especifique una opción `--sku` que proporciona menos recursos a un precio menor.</span><span class="sxs-lookup"><span data-stu-id="f2984-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="f2984-356">Además de escalar verticalmente las especificaciones de máquina virtual, mientras la aplicación web no tenga estado, también tiene la opción de *escalarla horizontalmente* mediante la adición de más instancias de máquinas virtuales subyacentes.</span><span class="sxs-lookup"><span data-stu-id="f2984-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="f2984-357">El plan de App Service que creó anteriormente incluía una sola máquina virtual (un *trabajo*) y, por tanto, todo el tráfico entrante en última instancia estaba limitado por los límites de los recursos disponibles de esa instancia.</span><span class="sxs-lookup"><span data-stu-id="f2984-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="f2984-358">Si quiere agregar una segunda instancia de máquina virtual, puede ejecutar el mismo comando que ejecutó anteriormente, pero en lugar de escalar verticalmente el SKU, reduzca verticalmente el número de máquinas virtuales de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f2984-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="f2984-359">Al escalar horizontalmente una aplicación web similar a la siguiente, el tráfico entrante equilibrará la carga de manera transparente entre todas las instancias, lo que permite aumentar de inmediato su capacidad sin realizar ningún cambio en el código ni preocuparse de la infraestructura necesaria.</span><span class="sxs-lookup"><span data-stu-id="f2984-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="f2984-360">Las aplicaciones web sin estado se consideran un procedimiento recomendado, ya que permiten la capacidad de escalarlos (verticalmente, horizontalmente y reducirlos verticalmente) de forma completamente determinista ya que ninguna máquina virtual o instancia de la aplicación incluye el estado que es necesario para poder funcionar.</span><span class="sxs-lookup"><span data-stu-id="f2984-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="f2984-361">Aunque el tutorial de este tema muestra la ejecución de una aplicación web individual como parte de un plan de App Service, puede crear e implementar varias aplicaciones web en el mismo plan, lo que le permite aprovisionar y pagar por un único plan.</span><span class="sxs-lookup"><span data-stu-id="f2984-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="f2984-362">Limpieza</span><span class="sxs-lookup"><span data-stu-id="f2984-362">Clean-up</span></span>

<span data-ttu-id="f2984-363">Para asegurarse de que no se le cobre por ningún recurso de Azure que no esté usando, ejecute el siguiente comando desde el terminal de Visual Studio Code para eliminar todos los recursos aprovisionados durante este tutorial.</span><span class="sxs-lookup"><span data-stu-id="f2984-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="f2984-364">El proceso de limpieza puede tardar varios minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="f2984-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="f2984-365">Una vez finalizado, el comando `az group delete` deja la cuenta de Azure en el mismo estado que tenía antes de iniciar el tutorial.</span><span class="sxs-lookup"><span data-stu-id="f2984-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="f2984-366">La capacidad de organizar, implementar y eliminar recursos de Azure como una sola unidad es una de las principales ventajas de los grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="f2984-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="f2984-367">Por lo tanto, como procedimiento recomendado, se deben agrupar aquellos recursos que puedan tener la misma duración.</span><span class="sxs-lookup"><span data-stu-id="f2984-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>