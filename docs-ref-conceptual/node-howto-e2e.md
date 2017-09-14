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
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>Desarrollo de Node.js con Visual Studio Code y Azure

En este tutorial se muestra cómo tomar una aplicación Node.js existente, incluirla en un contenedor Docker e implementarla en Azure mediante Visual Studio Code.

El tutorial utiliza una aplicación simple de lista de tareas creada y publicada por [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular). Es una aplicación MEAN de una página y, por lo tanto, usa MongoDB como base de datos, Node/Express para la API de RESTy servidor web y Angular.js 1.x para la interfaz de usuario de front-end. 

## <a name="prerequisites"></a>Requisitos previos

Para proseguir con la demostración, debe tener instalado el software siguiente:

- [código de Visual Studio](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [Cuenta de DockerHub](https://hub.docker.com/)
- [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Cuenta de Azure](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/): se usa para depurar el front-end de la aplicación de demostración.
- MongoDB: debido a que la aplicación de demostración utiliza MongoDB, debe tener una instancia de MongoDB que se ejecute localmente y que está escuchando en el puerto estándar `27017`. La manera más sencilla de lograrlo es mediante la ejecución de los dos comandos siguientes después de instalar Docker: `docker pull mongo` seguido de `docker run -it -p 27017:27017 mongo`.

## <a name="project-setup"></a>Configuración del proyecto

Para empezar, descargue el proyecto de ejemplo mediante los pasos siguientes:

1. Abra Visual Studio Code.

1. Presione **&lt;F1>** para mostrar la paleta de comandos.

1. En el símbolo de la paleta de comandos, escriba `gitcl`, seleccione el comando **Git: Clone** y presione **&lt;Entrar>**.

    ![Comando gitcl en el símbolo de la paleta de comandos de Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. Cuando se le solicite la **dirección URL de repositorio**, escriba `https://github.com/scotch-io/node-todo` y presione  **&lt;Entrar>**.

1. Seleccione el directorio local en el que va a clonar el proyecto, o créelo.

    ![Explorador de Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>Terminal integrado

Como es un proyecto Node.js, lo primero que debe hacer es asegurarse de que todas las dependencias del proyecto se instalan desde npm.  

1. Presione **&lt;Ctrl>'** para mostrar el terminal integrado de Visual Studio Code. 

1. Escriba `yarn` y presione **&lt;Entrar>**.  

    ![Ejecute el comando yarn dentro de Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>Control de versiones Git integrado

Después de instalar las dependencias de la aplicación a través de Yarn, se crea un archivo `yarn.lock` que proporciona una manera predecible de volver a adquirir las mismas dependencias exactas en el futuro, sin sorpresas en las compilaciones de integración continua, implementaciones de producción o en otros equipos de desarrollador.

Los siguientes pasos muestran cómo comprobar el archivo `yarn.lock` en el control de código fuente:

1. En Visual Studio Code, cambie a la pestaña de Git integrada (la pestaña con el logotipo Git).

1. En el cuadro **Mensaje**, escriba un mensaje de confirmación y presione **&lt;Ctrl>&lt;Entrar>**. 

    ![Adición del archivo yarn.lock a Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>Navegación del proyecto y código

Para orientarnos en el código base, vamos a ver algunos ejemplos de algunas de las funcionalidades de navegación que proporciona Visual Studio Code.

1. Presione **&lt;Ctrl>P**.

1. Escriba `.js` para mostrar todos los archivos JavaScript/JSON en el proyecto junto con el directorio principal de cada archivo. 

    ![Mostrar todos los archivos .js*](./media/node-howto-e2e/git-output.png)

1. Seleccione `server.js`, que es el script de inicio de la aplicación. 

1. Mantenga el puntero sobre la variable **base de datos** (importada en la línea 6) para ver su tipo. Esta capacidad de inspeccionar rápidamente variables/módulos/tipos en un archivo es muy útil durante el desarrollo de los proyectos. 

    ![Detectar tipo](./media/node-howto-e2e/hover-help.png)

1. Si hace clic en el mouse dentro del intervalo de una variable, como **database**, le permite ver todas las referencias a esa variable dentro del mismo archivo. Para ver todas las referencias a una variable dentro del proyecto, haga clic con el botón derecho en la variable y, en el menú contextual, seleccione **Buscar todas las referencias**.

    ![Buscar referencias a una variable](./media/node-howto-e2e/word-hilight.png)

1. Además de mantener el puntero sobre una variable para descubrir su tipo, puede inspeccionar la definición de una variable, incluso si se encuentra en otro archivo. Para ver esto en acción, haga clic con el botón derecho en **database.localUrl** (línea 12) y, en el menú contextual, seleccione **Ver la definición**. 

    ![Ver la definición de una variable](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>Modificación del código y uso de la característica de autocompletar

La cadena de conexión de MongoDB está codificada de forma rígida en la declaración de la variable **database.localUrl**. En esta sección, va a modificar el código para recuperar la cadena de conexión de una variable de entorno y aprenderá sobre la característica de autocompletar de Visual Studio Code.  

1. Abra el archivo `server.js`.

1. Reemplace el código siguiente: 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    por este otro:

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

Tenga en cuenta que si escribe el código de forma manual (en lugar de copiar y pegar), cuando se escribe un punto después `process`, Visual Studio Code muestra los miembros disponibles de la API global de **proceso** de Node.js.

![La característica de autocompletar muestra automáticamente los miembros de una API](./media/node-howto-e2e/process-env.png)

La característica de autocompletar funciona porque Visual Studio Code usa TypeScript en segundo plano (incluso para JavaScript) con el fin de proporcionar información de tipo que puede utilizarse para informar a la lista de finalización a medida que escribe. Visual Studio Code es capaz de detectar que se trata de un proyecto Node.js y, como resultado, se descarga automáticamente el archivo typings de TypeScript para [Node.js desde NPM](https://www.npmjs.com/package/@types/node). El archivo typings le permite obtener la función de autocompletar para otras funciones globales de Node.js (como **Buffer** y **setTimeout**), así como para todos los módulos integrados como **fs** y **http**.

Además de las API de Node.js integradas, esta adquisición automática del archivo typings también funciona con más de 2000 módulos de terceros, como React, Underscore y Express. Por ejemplo, para impedir que Mongoose bloquee la aplicación de ejemplo si no puede conectarse a la instancia de base de datos de MongoDB configurada, inserte la siguiente línea de código en la línea 13:

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

Al igual que con el código anterior, observará se autocompletará sin ningún trabajo por su parte.

![La característica de autocompletar muestra automáticamente los miembros de una API](./media/node-howto-e2e/mongoose.png)

Puede ver qué módulos son compatibles con esta funcionalidad de autocompletar al examinar el proyecto [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), que es el código fuente orientado a la comunidad de todas las definiciones de tipos de TypeScript.

## <a name="running-the-app"></a>Ejecución de la aplicación

Cuando haya explorado un poco el código, es el momento de ejecutar la aplicación. Para ejecutar la aplicación desde Visual Studio Code, presione **&lt;F5>**. Cuando se ejecuta el código a través de **&lt;F5>** (modo de depuración), Visual Studio Code inicia la aplicación y muestra la ventana **Consola de depuración** que muestra el stdout de la aplicación.

![Supervisión del stdout de una aplicación a través de la consola de depuración](./media/node-howto-e2e/console.png)

Además, la **Consola de depuración** se adjunta a la aplicación en ejecución recientemente para que pueda escribir expresiones de JavaScript, que se evaluará en la aplicación y también incluye características de autocompletar. Para ver esto en acción, escriba `process.env` en la consola:

![Escritura de código en la Consola de depuración](./media/node-howto-e2e/console-code.png)

Puede presionar **&lt;F5>** para ejecutar la aplicación porque el archivo abierto actualmente es un archivo JavaScript (`server.js`). Como resultado, Visual Studio Code asume que el proyecto es una aplicación Node.js. Si cierra todos los archivos JavaScript de Visual Studio Code y después presiona **&lt;F5>**, Visual Studio Code le consultará el entorno:

![Especificación del entorno en tiempo de ejecución](./media/node-howto-e2e/select-env.png)

Abra un explorador y vaya a `http://localhost:8080` para ver la aplicación en ejecución. Escriba un mensaje en el cuadro de texto y agregue o quite alguna lista de tareas para hacerse una idea de cómo funciona la aplicación.

![Ejecución de la aplicación de lista de tareas](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Depuración

Además de poder ejecutar la aplicación e interactuar con ella a través de la consola integrada, Visual Studio Code proporciona la capacidad de establecer puntos de interrupción directamente dentro del código. Por ejemplo, presione **&lt;Ctrl> P** para mostrar el selector de archivos. Cuando se muestre el selector de archivos, escriba `route` y seleccione el archivo `route.js`.

Establezca un punto de interrupción en la línea 28, que representa la ruta de Express que se llama cuando la aplicación intenta agregar una entrada a la lista de tareas. Para establecer un punto de interrupción, simplemente haga clic en el área situada a la izquierda del número de línea en el editor, tal como se muestra en la ilustración siguiente.

![Establecimiento de un punto de interrupción en Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> Además de los puntos de interrupción estándares, Visual Studio Code admite puntos de interrupción condicionales que le permiten personalizar cuando la aplicación debe suspender la ejecución. Para establecer un punto de interrupción condicional, haga clic con el botón derecho en el área situada a la izquierda de la línea en la que desea detener la ejecución, seleccione **Agregar punto de interrupción condicional...** y especifique una expresión de JavaScript (p. ej. `foo = "bar"`) o el número de ejecución que define la condición bajo la que desea pausar la ejecución.
> 
> 

Una vez establecido el punto de interrupción, vuelva a la aplicación en ejecución y agregue una entrada a la lista de tareas. Si agrega una entrada a la lista de tareas inmediatamente, hará que la aplicación suspenda la ejecución en la línea 28 en la que estableció el punto de interrupción:

![Ejecución de Visual Studio Code en pausa en un punto de interrupción](./media/node-howto-e2e/debugger.png)

Cuando se ha detenido la aplicación, mantenga el puntero sobre expresiones del código para ver su valor actual, inspeccione las variables locales e inspecciones y la pila de llamadas, y use la barra de herramientas de depuración para recorrer la ejecución del código. Presione **&lt;F5>** para reanudar la ejecución de la aplicación.

## <a name="full-stack-debugging"></a>Depuración de pila completa

Como se mencionó anteriormente en este tema, la aplicación de la lista de tareas es una aplicación MEAN, lo que significa que su front-end y back-end están ambos escritos con JavaScript. Por lo tanto, mientras está depurando el código de back-end (Node/Express), en algún momento debe depurar el código de front-end (Angular). Para ello, Visual Studio Code tiene un enorme ecosistema de extensiones, incluida la depuración de Chrome integrada.

Cambie a la pestaña **Extensiones** y escriba `chrome` en el cuadro de búsqueda:

![Extensión de depuración de Chrome para Visual Studio Code](./media/node-howto-e2e/chrome.png)

Seleccione la extensión denominada **Debugger for Chrome** (Depurador para Chrome) y seleccione **Instalar**. Después de instalar la extensión de depuración de Chrome, seleccione **Recargar** para cerrar y volver a abrir Visual Studio Code para activar la extensión. 

![Recarga de Visual Studio Code después de instalar la extensión de depuración de Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

Mientras se podía ejecutar y depurar el código de Node.js sin ninguna configuración específica de Visual Studio Code, para depurar una aplicación web de front-end, debe generar un archivo `launch.json` que indica a Visual Studio Code cómo ejecutar la aplicación. 

Para generar el archivo `launch.json`, cambie a la pestaña **Depurar**, haga clic en el icono de engranaje (que debe tener un pequeño punto rojo en la parte superior) y seleccione el entorno **node.js**.

![Opción de Visual Studio Code para configurar el archivo de launch.json](./media/node-howto-e2e/debug-gear.png)

Una vez creado, el archivo `launch.json` tiene un aspecto similar al siguiente e indica a Visual Studio Code cómo iniciar o asociar a la aplicación para depurarla. 

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

Tenga en cuenta que Visual Studio Code era capaz de detectar que el script de inicio de la aplicación es `server.js`. 

Con archivo `launch.json` abierto, seleccione **Agregar configuración** (parte inferior derecha) y seleccione **Chrome: Launch with userDataDir** (Chrome: iniciar con userDataDir).

![Adición de una configuración de Chrome a Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

Si se agrega una nueva configuración de ejecución para Chrome, podrá depurar el código de JavaScript de front-end. 

Puede mantener el puntero sobre cualquiera de las opciones que se especifican para ver la documentación sobre lo que hace la configuración. Además, tenga en cuenta que Visual Studio Code detecta automáticamente la dirección URL de la aplicación. Actualice la propiedad **webRoot** a `${workspaceRoot}/public` para que el depurador de Chrome sepa dónde encontrar los recursos de front-end de la aplicación:

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

Para iniciar o debug tanto el front-end como el back-end al mismo tiempo, tiene que crear una configuración de ejecución *compuesta* que indica a Visual Studio Code el conjunto de configuraciones que se van a ejecutar en paralelo. 

Agregue el siguiente fragmento de código como una propiedad de nivel superior dentro del archivo `launch.json` (como un elemento del mismo nivel de la propiedad **configurations** existente).

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

Los valores de cadena especificados en la matriz **compounds.configurations** hacen referencia al **nombre** de las entradas individuales de la lista de **configurations**. Si ha modificarse esos nombres, debe realizar los cambios apropiados en la matriz. Para ver esto en acción, cambie a la pestaña Depurar y cambie la configuración seleccionada para **Full-Stack** (el nombre de la configuración compuesta) y presione **&lt;F5>** para ejecutarla.

![Ejecución de una configuración en Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

Si se ejecuta la configuración, se inicia la aplicación Node.js (como puede verse en la salida de la consola de depuración) y Chrome (configurado para navegar a la aplicación Node.js en `http://localhost:8080`).

Presione **&lt;Ctrl> P** y escriba (o seleccione) `todos.js`, que es el controlador principal de Angular para el front-end de la aplicación. 

Establezca un punto de interrupción en la línea 11, que es el punto de entrada para una nueva entrada de lista de tareas que se está creando.

Vuelva a la aplicación en ejecución, agregue una nueva entrada de lista de tareas y tenga en cuenta que Visual Studio Code ahora ha suspendido la ejecución dentro del código Angular.

![Depuración de código de front-end en Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

Similar a la depuración de Node.js, puede mantener el puntero sobre las expresiones, ver las variables locales e inspecciones, evaluar las expresiones en la consola y así sucesivamente. 

Hay dos aspectos importantes que deben tenerse en cuenta:

1. El panel **Pila de llamadas** muestra dos pilas diferentes: **Node** y **Chrome** e indica cuál es la que está actualmente en pausa.

1. Puede pasar entre el código de front-end y back-end. Para probarlo, presione **&lt;F5>**, que ejecutará el punto de interrupción previamente establecido en la ruta de Express.

Con esta configuración, ahora puede depurar eficazmente el código de JavaScript de pila completa, de front-end y back-end directamente en Visual Studio Code. 

Además, el concepto de depurador compuesto no está limitado únicamente a dos procesos de destino y además no está limitado a JavaScript. Por tanto, si funciona en una aplicación de microservicio (que sea potencialmente políglota), puede usar el mismo flujo de trabajo (una vez que haya instalado las extensiones correspondientes para el lenguaje o plataforma).

## <a name="dockerizing-the-app"></a>Inclusión de la aplicación en un contenedor Docker

Esta sección se centra en la experiencia que proporciona Visual Studio Code para el desarrollo con [Docker](https://www.docker.com/). Los desarrolladores de Node.js usan Docker para proporcionar implementaciones de aplicaciones portátiles para los entornos de desarrollo, integración continua y de producción. Como Docker presenta que fuerte curva de aprendizaje para algunos, Visual Studio Code ofrece una extensión que ayuda a simplificar el uso de Docker en las aplicaciones.

Vuelva a la pestaña **Extensiones**, busque `docker` y seleccione la extensión **Docker**. 

Instale la extensión Docker y vuelva a cargar Visual Studio Code.

![Instalación de la extensión de Docker para Visual Studio Code](./media/node-howto-e2e/docker-search.png)

La extensión Docker para Visual Studio Code incluye un comando para generar un *Dockerfile* y el archivo `docker-compose.yml` para un proyecto existente. 

Para ver los comandos de Docker disponibles, muestre la paleta de comandos (a través de **&lt;F1>**) y escriba `docker`.

![Comandos admitidos por la extensión Docker para Visual Studio ](./media/node-howto-e2e/docker-commands.png)

Seleccione **Docker: Add docker files to workspace** (Docker: Agregar archivos de docker al área de trabajo), seleccione **Node.js** como la plataforma de aplicación y especifique que la aplicación expone el puerto `8080`. 

El comando de Docker genera un `Dockerfile` completo y archivos docker-compose que puede empezar a usar inmediatamente.

![Dockerfile generado](./media/node-howto-e2e/docker-file.png)

La extensión Docker también proporciona características de autocompletar para sus archivo `Dockerfiles` y `docker-compose.yml`. 

Para ver esto en acción, abra el `Dockerfile` y cambie la línea 2 de:

```docker
FROM node:latest
```

Por:

```docker
FROM mhart
```

Con el cursor situado después de la `t` en `mhart`, presione **&lt;Ctrl>&lt;espacio>** para ver todos los repositorios de imágenes que `mhart` ha publicado en DockerHub.

![Completado automático de la extensión Docker](./media/node-howto-e2e/docker-completion.png)

Seleccione `mhart/alpine-node`, que proporciona todo lo que necesita esta aplicación. 

Las imágenes más pequeñas suelen ser mejores, ya que quiere que las compilaciones e implementaciones de la aplicación sean lo más rápidas posibles, lo que permite una distribución y un ajuste de escala más rápido.

Ahora que ha generado el `Dockerfile`, necesita crear la imagen de Docker real. Una vez más, puede usar un comando que ha instalado la extensión Docker en Visual Studio Code. Presione **&lt;F1>**, escriba `dockerb` en la paleta de comandos y seleccione el comando **Docker: Build Image** (Docker: Crear imagen). Elija la `/Dockerfile` que acaba de generar y modificar. Especifique una etiqueta que incluya el nombre de usuario de DockerHub (p. ej. `lostintangent/node`). Presione **&lt;ENTRAR>** para iniciar la ventana del terminal integrado, que muestra la salida de la imagen de Docker que se está creando.

![Estado de creación de la imagen de Docker](./media/node-howto-e2e/docker-build.png)

Observe que el comando ha automatizado el proceso de ejecución `docker build`, lo que representa otro ejemplo de un optimizador de productividad que puede usar o bien puede utilizar directamente la CLI de Docker. 

En este momento, para que esta imagen sea fácilmente asequible para las implementaciones, solo necesita insertar la imagen en DockerHub. Para ello, asegúrese de que ya está autenticado con DockerHub mediante la ejecución de `docker login` desde la CLI y escriba sus credenciales de cuenta. Después, en Visual Studio Code, puede abrir la paleta de comandos, escribir `dockerpush` y seleccionar el comando `Docker: Push`. Seleccione la etiqueta de imagen que acaba de crear (p. ej. `lostintangent/node`) y presione **&lt;Entrar>**. El comando automatiza la llamada de `docker push` y muestra la salida en el terminal integrado.

## <a name="deploying-the-app"></a>Implementación de la aplicación

Ahora que se ha incluido la aplicación en un contenedor Docker y se ha insertado en Dockerhub, deberá implementarla en la nube para que todo el mundo pueda verla. Para ello, puede usar Azure App Service, que es una oferta de PaaS de Azure. App Service tiene dos funcionalidades pertinentes para los desarrolladores de Node.js:

- Compatibilidad con máquinas virtuales basadas en Linux, lo que reduce las incompatibilidades para aplicaciones creadas con módulos nativos de Node u otras herramientas que es posible que no admitan Windows o que puedan comportarse de manera diferente.
- Compatibilidad con las implementaciones basadas en Docker, que le permite especificar el nombre de la imagen de Docker y permite que App Service extraiga, implemente y escale la imagen automáticamente.

Para empezar, abra el terminal de Visual Studio. Deberá usar la nueva versión 2.0 de la CLI de Azure para administrar su cuenta de Azure y aprovisionar la infraestructura necesaria para ejecutar la aplicación de la lista de tareas. Cuando haya iniciado sesión en su cuenta de la CLI usando el comando `az login` (como se mencionó en los requisitos previos), lleve a cabo los pasos siguientes para aprovisionar la instancia de App Service e implementar el contenedor de la aplicación de lista de tareas:

1. Cree un grupo de recursos, que se puede considerar como un *espacio de nombres* o *directorio* para ayudar a organizar los recursos de Azure. La opción `-n` se utiliza para especificar el nombre del grupo y puede ser cualquier cosa que desee.

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > La opción `-l` indica la ubicación del grupo de recursos. Mientras esté en versión preliminar, la compatibilidad de App Service en Linux solo estará disponible en regiones seleccionadas. Por lo tanto, si no se encuentra en la zona del oeste de EE. UU. y quiere comprobar qué otras regiones están disponibles, ejecute `az appservice list-locations --linux-workers-enabled` desde la CLI para ver las opciones del centro de datos.

2. Establezca el grupo de recursos recién creado como el grupo de recursos predeterminado para que pueda continuar usando la CLI sin necesidad de especificar explícitamente el grupo de recursos con cada llamada a la CLI:

   ```shell
   az configure -d group=nina-demo
   ```
   
3. Cree el *plan* de App Service, que administra la creación y el escalado de las máquinas virtuales subyacentes en las que se implementa la aplicación. Una vez más, especifique el valor que desee para la opción `n`.

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > La opción --is-linux indica que quiere máquinas virtuales basadas en Linux. Sin ella, la CLI se establece de forma predeterminada para aprovisionar las máquinas virtuales basadas en Windows.

4. Cree la aplicación web de App Service, que representa la aplicación real de lista de tareas que se ejecutarán en el plan y en el grupo de recursos que acaba de crear. Se puede considerar que una aplicación web es sinónimo de un proceso o contenedor y el plan es como el host de la máquina virtual o contenedor en el que se ejecuta. Además, como parte de la creación de la aplicación web, deberá configurarlo para usar la imagen de Docker que se publicó en DockerHub:

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > Si en lugar de utilizar un contenedor personalizado prefiere una implementación de Git, consulte el artículo [Creación de una aplicación web de Node.js en Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).

5. Establezca la aplicación web como la instancia de web predeterminada:

    ```shell
    az configure -d web=nina-demo-app
    ```

6. Inicie la aplicación para ver el contenedor implementado, que estará disponible en una dirección URL `*.azurewebsites.net`:

    ```shell
    az webapp browse
    ```

    ![Aplicación de lista de tareas que se ejecuta en el explorador](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > Puede tardar varios minutos en cargarse la aplicación por primera vez, ya que App Service tiene que extraer la imagen de Docker del DockerHub y volver a iniciarla.

En este momento, ha implementado y ejecutado la aplicación de lista de tareas. 

Ahora ha implementado la aplicación de lista de tareas. Sin embargo, el icono de giro indica que la aplicación no se puede conectar a la base de datos. Esto es debido al hecho de que se usa una instancia local de MongoDB durante el desarrollo, lo que obviamente no es accesible desde los centros de datos de Azure. Como se ha modificado la aplicación para que acepte la cadena de conexión a través de una variable de entorno, solo debe iniciar un servidor de MongoDB y volver a configurar la instancia de App Service para que haga referencia a la variable de entorno. Esto se muestra en la sección siguiente.

## <a name="provisioning-a-mongodb-server"></a>Aprovisionamiento de un servidor de MongoDB

Aunque puede configurar un servidor de MongoDB, o un conjunto de réplicas, y administrar usted mismo esa infraestructura, Azure proporciona una solución denominada [Cosmos DB](https://azure.microsoft.com/services/documentdb/). Cosmos DB es una base de datos de NoSQL completamente administrada, con replicación geográfica y de alto rendimiento, que proporciona una capa de compatibilidad con MongoDB. Esto significa que puede apuntar una aplicación MEAN existente a él (o cualquier otra herramienta o cliente de MongoDB, como [Studio 3T](https://studio3t.com/)) sin tener que cambiar nada más que la cadena de conexión. Los pasos siguientes muestran cómo realizar esto:

1. Desde el terminal de Visual Studio Code, ejecute el siguiente comando para crear una instancia compatible con MongoDB del servicio Cosmos DB. Reemplace el marcador de posición **<NAME>** por un valor único global (Cosmos DB utiliza este nombre para generar la dirección URL del servidor de la base de datos):

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. Recupere la cadena de conexión de MongoDB para esta instancia:

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. Actualice la variable de entorno **MONGODB_URL** de la aplicación web, para se conecte a la instancia de Cosmos DB recién aprovisionada en lugar de intentar conectarse a un servidor de MongoDB que se ejecuta localmente (y que no existe):

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. Regrese al explorador y actualícelo. Pruebe a agregar y quitar un elemento de la lista de tareas para demostrar que la aplicación funciona sin necesidad de cambiar nada. Establezca la variable de entorno en la instancia de Cosmos DB creada, que está emulando completamente una base de datos de MongoDB.

    ![Aplicación de demostración después de su conexión a una base de datos](./media/node-howto-e2e/finished-demo.png)

Cuando sea necesario, puede cambiar la instancia de Cosmos DB y escalar (o reducir) verticalmente el rendimiento reservado que necesita la instancia de MongoDB y aprovechar así el tráfico agregado sin necesidad de administrar ninguna infraestructura manualmente.

Además, Cosmos DB indexará automáticamente cada documento y propiedad. De este modo, no tiene que generar perfiles de consultas lentas ni ajustar manualmente los índices. Solo se necesita el aprovisionamiento y el escalado, y Cosmos DB se encarga del resto.

## <a name="hosting-a-private-docker-registry"></a>Hospedaje de un registro de Docker privado

DockerHub proporciona una experiencia increíble al distribuir las imágenes de contenedor, pero puede haber escenarios donde preferiría hospedar su propio registro de Docker privado, como de las ventajas de rendimiento o de seguridad y gobierno. Para ello, Azure proporciona [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), que permite poner en marcha su propio registro de Docker cuyo almacenamiento de copias de seguridad se encuentra en el mismo centro de datos que la aplicación web (con lo que hace la extracción es más rápida). ACR también proporciona un control total sobre el contenido y los controles de acceso, como, por ejemplo, quién puede insertar o extraer imágenes. 

El aprovisionamiento de un registro personalizado puede realizarse con la ejecución del siguiente comando. (Reemplace el marcador de posición **<NAME>** por un valor único global que use ACR como valor especificado para generar la dirección URL del servidor de inicio de sesión del registro.

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> Aunque este tema de ejemplo utiliza la **cuenta de administrador** para no complicar las cosas, no se recomienda para los registros de producción. 

El comando `az acr create` muestra la dirección URL del servidor de inicio de sesión (a través de la columna `LOGIN SERVER`) que se utiliza para iniciar sesión mediante la CLI de Docker (p. ej. `ninademo.azurecr.io`). Además, el comando genera las credenciales de administrador que puede usar para autenticarse con ellas. Para recuperar esas credenciales, ejecute el siguiente comando y anote el nombre de usuario y la contraseña mostrados:

```shell
az acr credential show -n $ACR_NAME
```

Con las credenciales del paso anterior y el servidor de inicio de sesión individual, puede iniciar sesión en el registro mediante el flujo de trabajo estándar de la CLI de Docker.

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

Ahora puede etiquetar el contenedor de Docker para indicar que está asociado a su registro privado mediante el siguiente comando (reemplazando `lostintangent/node` por el nombre que asignó a la imagen del contenedor).

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

Por último, inserte la imagen etiquetada en el registro de Docker privado.

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

El contenedor ya está almacenado en su propio registro privado y la CLI de Docker le permite seguir trabajando en la misma manera que cuando usaba DockerHub. Para indicar a la aplicación web de App Service que incorporar los cambios del registro privado, solo necesita ejecutar el siguiente comando:

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> Asegúrese de agregar el prefijo `https://` al principio de la opción `-r`. Sin embargo, no agregue el prefijo al nombre de la imagen de contenedor.

Si actualiza la aplicación en el explorador, todo debería parecer y funcionar de la misma forma. Sin embargo, ahora se está ejecutando la aplicación a través del registro de Docker privado. Una vez actualizada la aplicación, etiquete e inserte los cambios como realizó anteriormente y actualice la etiqueta en la configuración del contenedor de App Service.

## <a name="configuring-a-custom-domain-name"></a>Configuración de un nombre de dominio personalizado

Mientras la dirección URL `*.azurewebsites.net` es muy útil para pruebas, en algún momento puede querer agregar un nombre de dominio personalizado a la aplicación web. Cuando tenga un nombre de dominio en un registrador de dominios, solo necesitará agregarle un registro `A` que señala a la IP externa de la aplicación web (que es realmente un equilibrador de carga). Puede recuperar esta IP mediante la ejecución del siguiente comando:

```shell
az webapp config hostname get-external-ip
```

Además de agregar un registro `A`, también debe agregar un registro `TXT` a su dominio que apunta al dominio `*.azurewebsites.net` que ha estado utilizando hasta ahora. La combinación de los registros `A` y `TXT` permite a Azure comprobar que posee el dominio.

Cuando se crean los registros y se han propagado los cambios de DNS, registre el dominio personalizado con Azure para que pueda esperar el tráfico entrante correctamente. 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> El comando no funcionará hasta que se hayan propagado los cambios de DNS.

Abra un explorador y vaya a su dominio personalizado para ver que se resuelve ahora en la aplicación implementada en Azure.

## <a name="scaling-up-and-out"></a>Escalado vertical y horizontal

En algún momento, la aplicación web puede convertirse en lo suficientemente popular sus recursos asignados (CPU y RAM) no sean ya suficientes para controlar el aumento de demandas de tráfico y operacionales. El plan de App Service que creó anteriormente (**B1**) viene con una CPU de 1 núcleo y 1,75 GB de RAM, que puede sobrepasarse con bastante rapidez. El plan **B2** incluye el doble de RAM y CPU, por lo que si observa que la aplicación comienza a agotarlos, puede escalar verticalmente la máquina virtual subyacente mediante la ejecución el comando siguiente:

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> Para obtener información sobre especificaciones y detalles del plan App de Azure, consulte el artículo, [Precios de App Service](https://azure.microsoft.com/pricing/details/app-service/)

Poco después, la aplicación web se migrará al hardware solicitado y podrá empezar a sacar partido de los recursos asociados. Además de escalarla verticalmente, también puede reducirla verticalmente mediante la ejecución del mismo comando que antes, especifique una opción `--sku` que proporciona menos recursos a un precio menor. 

Además de escalar verticalmente las especificaciones de máquina virtual, mientras la aplicación web no tenga estado, también tiene la opción de *escalarla horizontalmente* mediante la adición de más instancias de máquinas virtuales subyacentes. El plan de App Service que creó anteriormente incluía una sola máquina virtual (un *trabajo*) y, por tanto, todo el tráfico entrante en última instancia estaba limitado por los límites de los recursos disponibles de esa instancia. Si quiere agregar una segunda instancia de máquina virtual, puede ejecutar el mismo comando que ejecutó anteriormente, pero en lugar de escalar verticalmente el SKU, reduzca verticalmente el número de máquinas virtuales de trabajo.

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

Al escalar horizontalmente una aplicación web similar a la siguiente, el tráfico entrante equilibrará la carga de manera transparente entre todas las instancias, lo que permite aumentar de inmediato su capacidad sin realizar ningún cambio en el código ni preocuparse de la infraestructura necesaria. 

Las aplicaciones web sin estado se consideran un procedimiento recomendado, ya que permiten la capacidad de escalarlos (verticalmente, horizontalmente y reducirlos verticalmente) de forma completamente determinista ya que ninguna máquina virtual o instancia de la aplicación incluye el estado que es necesario para poder funcionar. 

> [!NOTE]
> Aunque el tutorial de este tema muestra la ejecución de una aplicación web individual como parte de un plan de App Service, puede crear e implementar varias aplicaciones web en el mismo plan, lo que le permite aprovisionar y pagar por un único plan. 

## <a name="clean-up"></a>Limpieza

Para asegurarse de que no se le cobre por ningún recurso de Azure que no esté usando, ejecute el siguiente comando desde el terminal de Visual Studio Code para eliminar todos los recursos aprovisionados durante este tutorial.

```shell
az group delete
```

> [!NOTE]
> El proceso de limpieza puede tardar varios minutos en completarse. 

Una vez finalizado, el comando `az group delete` deja la cuenta de Azure en el mismo estado que tenía antes de iniciar el tutorial. La capacidad de organizar, implementar y eliminar recursos de Azure como una sola unidad es una de las principales ventajas de los grupos de recursos. Por lo tanto, como procedimiento recomendado, se deben agrupar aquellos recursos que puedan tener la misma duración.