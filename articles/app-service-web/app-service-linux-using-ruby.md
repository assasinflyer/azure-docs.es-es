---
title: Uso de Ruby en Web App on Linux de Azure App Service | Microsoft Docs
description: Uso de Ruby en Web App on Linux de Azure App Service
keywords: "azure app service, web app, preguntas más frecuentes, linux, oss, ruby"
services: app-service
documentationCenter: 
authors: aelnably
manager: erikre
editor: 
ms.assetid: 
ms.service: app-service
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/16/2017
ms.author: aelnably;wesmc
ms.translationtype: Human Translation
ms.sourcegitcommit: 71fea4a41b2e3a60f2f610609a14372e678b7ec4
ms.openlocfilehash: 5aeef6f31dacb1b27c605d39a35a81bd0211e06a
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017


---

# <a name="using-ruby-in-web-app-on-linux"></a>Uso de Ruby en Web App on Linux #

Con la última actualización de nuestro back-end, se introdujo la compatibilidad con Ruby v.2.3. Al establecer la configuración de la aplicación web de Linux, puede cambiar la pila de la aplicación.

## <a name="using-the-azure-portal"></a>Uso del portal de Azure ##

En el menú nuevo de [Azure Portal](https://portal.azure.com), puede elegir crear una aplicación web en Linux desde la opción Web y móvil como se muestra en la siguiente imagen:

![Inicio de creación de una aplicación web en Azure Portal][1]

Aparecerá la hoja de **creación**, como se muestra en la siguiente imagen:

![Hoja de creación][2]

1. Asigne un nombre a la aplicación web.
2. Elija un grupo de recursos existente o cree uno. (Consulte las regiones disponibles en la [sección de limitaciones](app-service-linux-intro.md)).
3. Seleccione un plan de Azure App Service existente o cree uno. (Consulte las notas del plan de App Service en la [sección de limitaciones](app-service-linux-intro.md)).
4. Seleccione Ruby entre las pilas en tiempo de ejecución integradas.

Una vez que se crea la aplicación web de Ruby, puede implementarla mediante Git o FTP.

## <a name="next-steps"></a>Pasos siguientes
* [¿Qué es Web App on Linux?](app-service-linux-intro.md)
* [Creación de aplicaciones web en Web App on Linux](app-service-linux-how-to-create-web-app.md)
* [Implementación de Git local en Azure App Service](app-service-deploy-local-git.md)
* [Preguntas más frecuentes sobre Web App on Linux de Azure App Service](app-service-linux-faq.md)

<!--Image references-->
[1]: ./media/app-service-linux-using-ruby/New-Linux.png
[2]: ./media/app-service-linux-using-ruby/Ruby-UX.png
