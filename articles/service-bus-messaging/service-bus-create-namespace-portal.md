---
title: "Creación de un espacio de nombres de Service Bus en Azure Portal | Microsoft Docs"
description: "Creación de un espacio de nombres de Service Bus mediante Azure Portal."
services: service-bus-messaging
documentationcenter: .net
author: sethmanheim
manager: timlt
editor: 
ms.assetid: fbb10e62-b133-4851-9d27-40bd844db3ba
ms.service: service-bus-messaging
ms.devlang: tbd
ms.topic: get-started-article
ms.tgt_pltfrm: dotnet
ms.workload: na
ms.date: 06/27/2017
ms.author: sethm
ms.translationtype: Human Translation
ms.sourcegitcommit: 857267f46f6a2d545fc402ebf3a12f21c62ecd21
ms.openlocfilehash: ffb134085c8555b22a317213622ca6c9490497d8
ms.contentlocale: es-es
ms.lasthandoff: 06/28/2017


---
<a id="create-a-service-bus-namespace-using-the-azure-portal" class="xliff"></a>

# Creación de un espacio de nombres de Service Bus mediante Azure Portal

Un espacio de nombres es un contenedor con un ámbito para todos los componentes de la mensajería. Varias colas y temas pueden residir en un único espacio de nombres, y los espacios de nombres suelen servir de contenedores de aplicación. Existen dos formas diferentes de crear espacios de nombres de Service Bus:

1. Azure Portal (este artículo)
2. [Plantillas de Resource Manager][create-namespace-using-arm]

<a id="create-a-namespace-in-the-azure-portal" class="xliff"></a>

## Creación de un espacio de nombres en Azure Portal

[!INCLUDE [service-bus-create-namespace-portal](../../includes/service-bus-create-namespace-portal.md)]

¡Enhorabuena! Ha creado un espacio de nombres de mensajería de Service Bus.

<a id="next-steps" class="xliff"></a>

## Pasos siguientes

Consulte nuestros [ejemplos de GitHub][github-samples], que muestran algunas de las características más avanzadas de la mensajería de Azure Service Bus.

[create-namespace-using-arm]: service-bus-resource-manager-overview.md
[github-samples]: https://github.com/Azure-Samples/azure-servicebus-messaging-samples

