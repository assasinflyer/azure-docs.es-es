---
title: "Introducción al escritorio de Windows en Azure AD v2: configuración | Microsoft Docs"
description: "Cómo puede obtener una aplicación .NET de escritorio de Windows (XAML) un token de acceso y llamar a una API protegida por un punto de conexión de Azure Active Directory v2."
services: active-directory
documentationcenter: dev-center-name
author: andretms
manager: mbaldwin
editor: 
ms.assetid: 820acdb7-d316-4c3b-8de9-79df48ba3b06
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 05/09/2017
ms.author: andret
ms.custom: aaddev
ms.translationtype: Human Translation
ms.sourcegitcommit: ef74361c7a15b0eb7dad1f6ee03f8df707a7c05e
ms.openlocfilehash: 5e83171846517496e221f0a84565cdf7b77514df
ms.contentlocale: es-es
ms.lasthandoff: 07/06/2017


---

## <a name="add-the-applications-registration-information-to-your-app"></a>Adición de información de registro de la aplicación a su aplicación
En este paso, debe agregar el identificador de aplicación a su proyecto.

1.  Abra `App.xaml.cs` y reemplace la línea que contiene el `ClientId` con:

```csharp
private static string ClientId = "[Enter the application Id here]";
```

### <a name="what-is-next"></a>Pasos siguientes

[Probar y validar](active-directory-mobileanddesktopapp-windowsdesktop-test.md)

