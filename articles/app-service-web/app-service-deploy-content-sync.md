---
title: "Sincronización de contenido de una carpeta de nube al Servicio de aplicaciones de Azure"
description: "Descubra cómo implementar su aplicación en el Servicio de aplicaciones de Azure mediante una sincronización de contenido desde una carpeta de la nube."
services: app-service
documentationcenter: 
author: dariagrigoriu
manager: erikre
editor: mollybos
ms.assetid: 88d3a670-303a-4fa2-9de9-715cc904acec
ms.service: app-service
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/13/2016
ms.author: dariagrigoriu
translationtype: Human Translation
ms.sourcegitcommit: 2ea002938d69ad34aff421fa0eb753e449724a8f
ms.openlocfilehash: ddda0e60dc9d5414142791175b77a5a65e3f40e3
ms.lasthandoff: 11/17/2016


---
# <a name="sync-content-from-a-cloud-folder-to-azure-app-service"></a>Sincronización de contenido de una carpeta de nube al Servicio de aplicaciones de Azure
En este tutorial se muestra cómo implementar en el [Servicio de aplicaciones de Azure](http://go.microsoft.com/fwlink/?LinkId=529714) mediante la sincronización de su contenido desde servicios de almacenamiento en nube populares, como Dropbox y OneDrive. 

## <a name="a-nameoverviewaoverview-of-content-sync-deployment"></a><a name="overview"></a>Información general sobre la implementación de la sincronización de contenido
La implementación de la sincronización de contenido a petición funciona con el [motor de implementación Kudu](https://github.com/projectkudu/kudu/wiki) integrado con el Servicio de aplicaciones. En el [Portal de Azure](https://portal.azure.com), puede designar una carpeta especial en el almacenamiento en la nube, trabajar con el código de la aplicación y el contenido de dicha carpeta, y sincronizar con el Servicio de aplicaciones con solo hacer clic en un botón. La sincronización de contenido utiliza el proceso de Kudu para la compilación e implementación. 

## <a name="a-namecontentsyncahow-to-enable-content-sync-deployment"></a><a name="contentsync"></a>Habilitación de la implementación de la sincronización de contenido
Para habilitar la sincronización de contenido en el [Portal de Azure](https://portal.azure.com), siga estos pasos:

1. En la hoja de su aplicación de Azure Portal, haga clic en **Configuración** > **Origen de implementación**. Haga clic en **Elegir origen** y, después, seleccione **OneDrive** o **Dropbox** como origen de la implementación. 
   
    ![Sincronización de contenido](./media/app-service-deploy-content-sync/deployment_source.png)
   
   > [!NOTE]
   > Debido a diferencias subyacentes en las API, **OneDrive para la empresa** no se admite en este momento. 
   > 
   > 
2. Complete el flujo de trabajo de autorización para permitir que el Servicio de aplicaciones acceda a una ruta designada y predefinida específica para OneDrive o Dropbox en la que se almacenará todo su contenido del Servicio de aplicaciones.  
    Tras la autorización, la plataforma Servicio de aplicaciones le ofrecerá la opción de crear una carpeta de contenido en la ruta de contenido designada o de elegir una carpeta existente en dicha ruta. Las rutas de contenido designadas en sus cuentas de almacenamiento en nube utilizadas para la sincronización del Servicio de aplicaciones son las siguientes:  
   
   * **OneDrive**: `Apps\Azure Web Apps` 
   * **Dropbox**: `Dropbox\Apps\Azure`
3. Después de la sincronización de contenido inicial, se puede iniciar la sincronización a petición desde el Portal de Azure. El historial de implementación está disponible en la hoja **Implementaciones** .
   
    ![Historial de implementaciones](./media/app-service-deploy-content-sync/onedrive_sync.png)

Puede obtener más información sobre la implementación de Dropbox en [Deploy from Dropbox](http://blogs.msdn.com/b/windowsazure/archive/2013/03/19/new-deploy-to-windows-azure-web-sites-from-dropbox.aspx). 


