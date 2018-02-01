---
title: "Creación de una entidad de servicio de Azure con Node.js"
description: "Aprenda a usar la autenticación de entidad de servicio a través de Node.js."
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 73afa36571abcb7c87273e9c2b3665e199786931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Creación de una entidad de servicio de Azure con Node.js 

Cuando una aplicación necesite acceder a recursos, puede configurar una identidad para la aplicación y autenticarla con sus propias credenciales. Esta identidad se conoce como *entidad de servicio*. En resumen, puede crear claves para su cuenta de Azure Active Directory que proporciona a los SDK para autenticarse, en lugar de requerir la intervención del usuario o el nombre de usuario/contraseña.

El enfoque de la entidad de servicio le permite:
- Asignar permisos a la identidad de la aplicación que sean diferentes a los suyos propios. Normalmente, estos permisos están restringidos a exactamente aquello que la aplicación debe hacer.
- Usar un certificado para la autenticación al ejecutar un script desatendido.

En este tema se muestran tres técnicas para crear una entidad de servicio.

- Azure Portal
- CLI de Azure 2.0
- SDK de Azure para Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Creación de una entidad de servicio con Azure Portal

Siga los pasos descritos en el tema [Uso del portal para crear una aplicación de Azure Active Directory y una entidad de servicio con acceso a los recursos](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) para generar la entidad de servicio.

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Creación de una entidad de servicio con la CLI de Azure 2.0

La creación de una entidad de servicio mediante la [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) puede realizarse mediante los pasos siguientes:

1. Descargue la [CLI de Azure 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

2. Abra una ventana del terminal.

3. Escriba el comando siguiente para iniciar el proceso de inicio de sesión:

    ```shell
    $ az login
    ```

4. Al llamar a `az login` da como resultado una dirección URL y un código. Vaya a la dirección URL especificada, escriba el código e inicie sesión con su identidad de Azure (esto puede ocurrir automáticamente si ya inició sesión). Después, podrá tener acceso a su cuenta a través de la CLI.

5. Obtenga los identificadores de suscripción y de inquilino:

    ```shell
    $ az account list
    ```

    El siguiente texto muestra un ejemplo de la salida:

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **Anote el identificador de suscripción, pues lo utilizará en el paso 7.**

6. Cree una entidad de servicio para obtener un objeto JSON que contenga las otras partes de información que necesita para autenticarse con Azure.

    ```shell
    $ az ad sp create-for-rbac
    ```

    El siguiente texto muestra un ejemplo de la salida:

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Anote los valores de inquilino, nombre y contraseña, ya que se van a utilizar en el paso 7.**

7. Configure las variables de entorno: reemplace los marcadores de posición &lt;Id. suscripción>, &lt;inquilino>, &lt;nombre> y &lt;contraseña> con los valores obtenidos en los pasos 4 y 5. 

    **Con Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Uso de PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Creación de una entidad de servicio con el SDK de Azure para Node.js

Para crear mediante programación una entidad de servicio con JavaScript, use el [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Uso de la entidad de servicio

Cuando tenga una entidad de servicio, el siguiente fragmento de código JavaScript muestra cómo utilizar las claves de entidad de servicio para autenticarse con el SDK de Azure para Node.js. Modifique los siguientes marcadores de posición: &lt;clientId o appId>, &lt;secret o password> y &lt;domain o tenant>,

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
