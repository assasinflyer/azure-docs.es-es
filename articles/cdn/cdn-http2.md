---
title: Compatibilidad con HTTP/2 en la red CDN de Azure | Microsoft Docs
description: Aprenda sobre la compatibilidad con HTTP/2 y la red CDN.
services: cdn
documentationcenter: 
author: lichard
manager: erikre
editor: 
ms.service: cdn
ms.workload: tbd
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 5/04/2017
ms.author: rli
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ae7e129b381d3034433e29ac1f74cb843cb5aa6
ms.openlocfilehash: 4f8dd685c3ae89535217d7a17a01c5129ca7e6e4
ms.contentlocale: es-es
ms.lasthandoff: 05/08/2017


---

<a id="http2-support-in-azure-cdn" class="xliff"></a>

# Compatibilidad con HTTP/2 en la red CDN de Azure

HTTP/2 es una revisión principal de HTTP/1.1\. Proporciona un rendimiento web más rápido, tiempo de respuesta reducido y experiencia de usuario mejorada, al tiempo que se mantienen los métodos HTTP conocidos, los códigos de estado y la semántica. Aunque HTTP/2 está diseñado para trabajar con HTTP y HTTPS, muchos exploradores web de cliente solo admiten HTTP/2 sobre TLS.

<a id="http2-benefits" class="xliff"></a>

###Ventajas HTTP/2

Las ventajas de HTTP/2 incluyen:

*   **Multiplexación y simultaneidad**

    Mediante HTTP 1.1, para realizar varias solicitudes de varios recursos se requieren varias conexiones TCP y cada conexión tiene asociada una sobrecarga de rendimiento. HTTP/2 permite que se soliciten varios recursos en una única conexión TCP.

*   **Compresión de encabezados**

    Al comprimir los encabezados HTTP de los recursos atendidos, el tiempo en la red se reduce considerablemente.

*   **Dependencias de secuencias**

    Las dependencias de secuencias permiten al cliente indicar al servidor qué recursos tiene prioridad.


<a id="http2-browser-support" class="xliff"></a>

##Compatibilidad con exploradores HTTP/2

Todos los exploradores principales han implementado la compatibilidad con HTTP/2 en sus versiones actuales. Los exploradores no compatibles conmutarán automáticamente a HTTP/1.1.

|Browser|Versión mínima|
|-------------|------------|
|Microsoft Edge| 12|
|Google Chrome| 43|
|Mozilla Firefox| 38|
|Opera| 32|
|Safari| 9|

<a id="enabling-http2-support-in-azure-cdn" class="xliff"></a>

##Habilitación de la compatibilidad con HTTP/2 en la red CDN de Azure

La compatibilidad con HTTP/2 se encuentra actualmente activa para los perfiles de **red CDN de Azure de Akamai** y la **red CDN de Azure de Verizon**. No es necesaria ninguna otra acción por parte de los clientes.

<a id="next-steps" class="xliff"></a>

##Pasos siguientes

Para ver las ventajas de HTTP/2 en acción, consulte [esta demostración de Akamai](https://http2.akamai.com/demo).

Para más información sobre HTTP/2, consulte los siguientes recursos:

*   [Página principal de especificación de HTTP/2](https://http2.github.io/)
*   [Preguntas más frecuentes oficiales de HTTP/2](https://http2.github.io/faq/)
*   [Información de HTTP/2 de Akamai](https://http2.akamai.com/)

Para más información sobre las características disponibles de la red CDN de Azure, consulte la [información general sobre la red CDN de Azure](https://azure.microsoft.com/documentation/articles/cdn-overview/).
