---
title: "Aplicación Microsoft Authenticator para teléfonos móviles | Microsoft Docs"
description: "Aprenda a actualizar a la versión más reciente de Azure Authenticator."
services: multi-factor-authentication
documentationcenter: 
author: kgremban
manager: femila
editor: librown
ms.assetid: 3065a1ee-f253-41f0-a68d-2bd84af5ffba
ms.service: multi-factor-authentication
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/15/2017
ms.author: kgremban
ms.custom: H1Hack27Feb2017, end-user
ms.translationtype: Human Translation
ms.sourcegitcommit: 2db2ba16c06f49fd851581a1088df21f5a87a911
ms.openlocfilehash: c5d631aa2f03aee3df7a94bf62c9cd5dadb55eda
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
<a id="get-started-with-the-microsoft-authenticator-app" class="xliff"></a>

# Introducción a la aplicación Microsoft Authenticator
La aplicación Microsoft Authenticator proporciona un nivel de seguridad adicional para su cuenta profesional o educativa (por ejemplo, bsimon@contoso.com) o su cuenta de Microsoft (por ejemplo, bsimon@outlook.com).

La aplicación funciona de una de estas dos formas:

* **Notificación**. La aplicación puede ayudar a impedir el acceso no autorizado a las cuentas y detener las transacciones fraudulentas mediante el envío de una notificación al smartphone o a la tableta. Solo tiene que ver la notificación y, si es legítima, seleccionar **Comprobar**. De lo contrario, seleccione **Denegar**. Para más información sobre cómo denegar notificaciones, consulte How to use the Deny and Report Fraud Feature for Multi-Factor Authentication (Uso de la característica Denegar y notificar fraude para Multi-Factor Authentication).
* **Código de comprobación**. La aplicación puede utilizarse como token de software para generar un código de comprobación de OAuth. Después de escribir el nombre de usuario y la contraseña, especifique el código que facilita la aplicación en la pantalla de inicio de sesión. El código de comprobación es una forma adicional de autenticación.

La aplicación Microsoft Authenticator sustituye a la aplicación Azure Authenticator. La aplicación Azure Authenticator seguirá funcionando, pero si decide dar el paso a la nueva aplicación Microsoft Authenticator, este artículo puede servirle de ayuda.  

<a id="opt-in-for-two-step-verification" class="xliff"></a>

## Suscripción a la comprobación en dos pasos

La aplicación Microsoft Authenticator no funciona por sí misma. Deberá configurar sus cuentas para que le soliciten un segundo método de comprobación después de iniciar sesión con su nombre de usuario y contraseña. 

En cuentas profesionales o educativas, por lo habitual esto no tiene que elegirlo. Es el administrador de seguridad el que tendrá que suscribirse en su nombre y luego enviarle una notificación que necesita para registrar métodos de comprobación para su cuenta. Si este escenario se aplica en su caso, obtenga información en [¿Qué relevancia tiene Azure Multi-Factor Authentication para mí?](multi-factor-authentication-end-user.md).

En una cuenta personal, debe configurar la comprobación en dos pasos usted mismo. Si tiene una cuenta de Microsoft, esos pasos están disponibles en [Acerca de la verificación en dos pasos](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification). 

También puede usar Microsoft Authenticator con cuentas que no sean de Microsoft. Aunque es posible que llamen a la característica de comprobación en dos de otra manera, lo más seguro es que la encuentre en la configuración de seguridad o de inicio de sesión. 

<a id="install-the-app" class="xliff"></a>

## Instalación de la aplicación
La aplicación Microsoft Authenticator está disponible para [Windows Phone](http://go.microsoft.com/fwlink/?Linkid=825071), [Android](http://go.microsoft.com/fwlink/?Linkid=825072) e [IOS](http://go.microsoft.com/fwlink/?Linkid=825073).

<a id="add-accounts-to-the-app" class="xliff"></a>

## Incorporación de cuentas a la aplicación
Siga uno de los procedimientos siguientes para cada cuenta que desee agregar a la aplicación Microsoft Authenticator.

<a id="add-a-personal-microsoft-account-to-the-app" class="xliff"></a>

### Incorporación de una cuenta Microsoft personal a la aplicación

Para una cuenta Microsoft personal (una que use para iniciar sesión en Outlook.com, Xbox, Skype, etc.), lo único que debe hacer es iniciar sesión en su cuenta en la aplicación Microsoft Authenticator.

<a id="add-a-work-or-school-account-to-the-app-using-the-qr-code-scanner" class="xliff"></a>

### Incorporación de una cuenta profesional o educativa a la aplicación con el escáner de códigos QR
1. Vaya a la pantalla de configuración de comprobación de seguridad.  Para información sobre cómo ir a esta pantalla, consulte la sección sobre el [cambio de la configuración de seguridad](multi-factor-authentication-end-user-manage-settings.md#where-to-find-the-settings-page).
2. Active la casilla situada junto a **Aplicación Authenticator** y luego seleccione **Configurar**.

    ![Botón Configurar en la pantalla de configuración de la comprobación de seguridad](./media/authenticator-app-how-to/azureauthe.png)

    Aparecerá una pantalla con un código QR.

    ![Pantalla que proporciona el código QR](./media/authenticator-app-how-to/barcode2.png)
3. Abra la aplicación Microsoft Authenticator. En la pantalla **Cuentas**, seleccione **+** y especifique que quiere agregar una cuenta profesional o educativa.
4. Utilice la cámara para digitalizar el código QR y seleccione **Listo** para cerrar la pantalla de código QR.

    Si la cámara no funciona correctamente, puede [escribir manualmente la dirección URL y el código QR](#add-an-account-to-the-app-manually).

5. Cuando la aplicación muestra el nombre de cuenta con un código de seis dígitos debajo de él, ya ha terminado. 

    ![Pantalla Cuentas](./media/authenticator-app-how-to/accounts.png)

<a id="add-an-account-to-the-app-manually" class="xliff"></a>

### Incorporación manual de una cuenta a la aplicación
1. Vaya a la pantalla de configuración de comprobación de seguridad.  Para información sobre cómo ir a esta pantalla, consulte la sección sobre el [cambio de la configuración de seguridad](multi-factor-authentication-end-user-manage-settings.md).
2. Seleccione **Configurar**.

    ![Botón Configurar en la pantalla de configuración de la comprobación de seguridad](./media/authenticator-app-how-to/azureauthe.png)

    Aparecerá una pantalla con un código QR.  Anote la dirección URL y el código.

    ![Pantalla que proporciona el código QR y la dirección URL](./media/authenticator-app-how-to/barcode2.png)
3. Abra la aplicación Microsoft Authenticator. En la pantalla **Cuentas**, seleccione **+** y especifique que quiere agregar una cuenta profesional o educativa.

4. En el digitalizador, elija **escribir el código manualmente**.

    ![Pantalla para digitalizar un código QR](./media/multi-factor-authentication-end-user-first-time/scan2.png)
5. En la aplicación, escriba el código y la dirección URL en los cuadros correspondientes y luego seleccione **Finalizar**.

    ![Pantalla para escribir el código y la dirección URL](./media/authenticator-app-how-to/manual.png)

6. Cuando la aplicación muestra el nombre de cuenta con un código de seis dígitos debajo de él, ya ha terminado.

    ![Pantalla Cuentas](./media/authenticator-app-how-to/accounts.png)

<a id="add-an-account-to-the-app-using-touch-id" class="xliff"></a>

### Incorporación de una cuenta a la aplicación con Touch ID
La aplicación Microsoft Authenticator de iOS es compatible con Touch ID.  Azure Multi-Factor Authentication permite a las organizaciones pedir un PIN para los dispositivos. Con Touch ID, los usuarios de iOS no tienen por qué escribir un PIN. En su lugar, pueden digitalizar su huella y seleccionar **Aprobar**.

Configurar Touch ID con Microsoft Authenticator es sencillo. Un PIN supone un reto de comprobación normal. Si el dispositivo es compatible con Touch ID, Microsoft Authenticator lo configura automáticamente para esa cuenta.

![Comprobación de la configuración de Touch ID](./media/authenticator-app-how-to/touchid1.png)

A partir de ese momento, cuando se requiera que compruebe el inicio de sesión, seleccione la notificación push recibida y digitalice la huella dactilar en lugar de escribir su PIN.

![Notificación push](./media/authenticator-app-how-to/touchid2.png)

<a id="use-the-app-when-you-sign-in" class="xliff"></a>

## Uso de la aplicación al iniciar sesión

Después de que la cuenta se agregue a la aplicación, puede que se le solicite que realice una comprobación de prueba para asegurarse de que todo está configurado correctamente. Después de eso, habrá terminado. No es necesario hacer nada más hasta la próxima vez que inicie sesión.

Si eligió usar códigos de comprobación en la aplicación, comenzará a verlos en la página principal. Como cambian cada 30 segundos, siempre tendrá un código nuevo cuando lo necesite. Pero no tiene que hacer nada con ellos hasta que inicie sesión y se le solicite que escriba un código de comprobación.  
