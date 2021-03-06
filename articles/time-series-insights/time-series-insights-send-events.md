---
title: "Envío de eventos al entorno de Azure Time Series Insights | Microsoft Docs"
description: "Este tutorial describe cómo se insertan eventos en el entorno de Time Series Insights"
keywords: 
services: time-series-insights
documentationcenter: 
author: venkatgct
manager: almineev
editor: cgronlun
ms.assetid: 
ms.service: time-series-insights
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: big-data
ms.date: 04/21/2017
ms.author: venkatja
ms.translationtype: Human Translation
ms.sourcegitcommit: 6efa2cca46c2d8e4c00150ff964f8af02397ef99
ms.openlocfilehash: 9f2d3b57a42efb7b04566278d3267b3cdbed713a
ms.contentlocale: es-es
ms.lasthandoff: 07/01/2017

---
<a id="send-events-to-a-time-series-insights-environment-via-event-hub" class="xliff"></a>

# Envío de eventos a un entorno de Time Series Insights mediante un centro de eventos

Este tutorial explica cómo crear y configurar el centro de eventos y ejecutar una aplicación de ejemplo para insertar eventos. Si tiene un centro de eventos existente con eventos en formato JSON, pase por alto este tutorial y vea su entorno en [Time Series Insights](https://insights.timeseries.azure.com).

<a id="configure-an-event-hub" class="xliff"></a>

## Configuración de un centro de eventos
1. Para crear un centro de eventos, siga las instrucciones de la [documentación](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) de Event Hubs.

2. Asegúrese de crear un grupo de consumidores que sea utilizado exclusivamente por el origen de eventos de Time Series Insights.

  > [!IMPORTANT]
  > Asegúrese de que el grupo de consumidores no es utilizado por ningún otro servicio (como un trabajo de Stream Analytics u otro entorno de Time Series Insights). Si otros servicios utilizan el grupo de consumidores, la operación de lectura se ve afectada negativamente en este entorno y en los otros servicios. Utilizar “$Default” como grupo de consumidores podría provocar que otros lectores lo reutilicen.

  ![Selección del grupo de consumidores del centro de eventos](media/send-events/consumer-group.png)

3. En el centro de eventos, cree "MySendPolicy", que se usa para enviar eventos en el ejemplo de csharp.

  ![Seleccione Directivas de acceso compartido y haga clic en el botón Agregar](media/send-events/shared-access-policy.png)  

  ![Agregar nueva directiva de acceso compartido](media/send-events/shared-access-policy-2.png)  

<a id="create-time-series-insights-event-source" class="xliff"></a>

## Creación de un origen de eventos de Time Series Insights
1. Si no ha creado el origen de eventos, siga las instrucciones que se especifican [aquí](time-series-insights-add-event-source.md) para crear un origen de eventos.

2. Especifique "deviceTimestamp" como nombre de la propiedad de marca de tiempo: esta propiedad se utiliza como marca de tiempo real en el ejemplo de csharp. El nombre de la propiedad de marca de tiempo distingue mayúsculas de minúsculas y los valores deben tener el formato __yyyy-MM-ddTHH:mm:ss.FFFFFFFK__ cuando se envían como JSON al centro de eventos. Si la propiedad no existe en el evento, se utiliza la hora de puesta en la cola del centro de eventos.

  ![Creación de un origen de eventos](media/send-events/event-source-1.png)

<a id="sample-code-to-push-events" class="xliff"></a>

## Código de ejemplo para insertar eventos
1. Vaya a la directiva del centro de eventos "MySendPolicy" y copie la cadena de conexión con la clave de directiva.

  ![Copia de la cadena de conexión de MySendPolicy](media/send-events/sample-code-connection-string.png)

2. Ejecute el código siguiente para enviar 600 eventos para cada uno de los tres dispositivos. Reemplace `eventHubConnectionString` por su cadena de conexión.

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.IO;
using Microsoft.ServiceBus.Messaging;

namespace Microsoft.Rdx.DataGenerator
{
    internal class Program
    {
        private static void Main(string[] args)
        {
            var from = new DateTime(2017, 4, 20, 15, 0, 0, DateTimeKind.Utc);
            Random r = new Random();
            const int numberOfEvents = 600;

            var deviceIds = new[] { "device1", "device2", "device3" };

            var events = new List<string>();
            for (int i = 0; i < numberOfEvents; ++i)
            {
                for (int device = 0; device < deviceIds.Length; ++device)
                {
                    // Generate event and serialize as JSON object:
                    // { "deviceTimestamp": "utc timestamp", "deviceId": "guid", "value": 123.456 }
                    events.Add(
                        String.Format(
                            CultureInfo.InvariantCulture,
                            @"{{ ""deviceTimestamp"": ""{0}"", ""deviceId"": ""{1}"", ""value"": {2} }}",
                            (from + TimeSpan.FromSeconds(i * 30)).ToString("o"),
                            deviceIds[device],
                            r.NextDouble()));
                }
            }

            // Create event hub connection.
            var eventHubConnectionString = @"Endpoint=sb://...";
            var eventHubClient = EventHubClient.CreateFromConnectionString(eventHubConnectionString);

            using (var ms = new MemoryStream())
            using (var sw = new StreamWriter(ms))
            {
                // Wrap events into JSON array:
                sw.Write("[");
                for (int i = 0; i < events.Count; ++i)
                {
                    if (i > 0)
                    {
                        sw.Write(',');
                    }
                    sw.Write(events[i]);
                }
                sw.Write("]");

                sw.Flush();
                ms.Position = 0;

                // Send JSON to event hub.
                EventData eventData = new EventData(ms);
                eventHubClient.Send(eventData);
            }
        }
    }
}

```
<a id="supported-json-shapes" class="xliff"></a>

## Formas de JSON admitidas
<a id="sample-1" class="xliff"></a>

### Ejemplo 1

<a id="input" class="xliff"></a>

#### Entrada

Un objeto JSON simple.

```json
{
    "id":"device1",
    "timestamp":"2016-01-08T01:08:00Z"
}
```
<a id="output---1-event" class="xliff"></a>

#### Salida: 1 evento

|id|timestamp|
|--------|---------------|
|device1|2016-01-08T01:08:00Z|

<a id="sample-2" class="xliff"></a>

### Ejemplo 2

<a id="input" class="xliff"></a>

#### Entrada
Una matriz JSON con dos objetos JSON. Cada objeto JSON se convertirá en un evento.
```json
[
    {
        "id":"device1",
        "timestamp":"2016-01-08T01:08:00Z"
    },
    {
        "id":"device2",
        "timestamp":"2016-01-17T01:17:00Z"
    }
]
```
<a id="output---2-events" class="xliff"></a>

#### Salida: 2 eventos

|id|timestamp|
|--------|---------------|
|device1|2016-01-08T01:08:00Z|
|device2|2016-01-08T01:17:00Z|
<a id="sample-3" class="xliff"></a>

### Ejemplo 3

<a id="input" class="xliff"></a>

#### Entrada

Un objeto JSON con una matriz JSON anidada que contiene dos objetos JSON.
```json
{
    "location":"WestUs",
    "events":[
        {
            "id":"device1",
            "timestamp":"2016-01-08T01:08:00Z"
        },
        {
            "id":"device2",
            "timestamp":"2016-01-17T01:17:00Z"
        }
    ]
}

```
<a id="output---2-events" class="xliff"></a>

#### Salida: 2 eventos
Tenga en cuenta que la propiedad "location" se copia en cada uno de los eventos.

|location|events.id|events.timestamp|
|--------|---------------|----------------------|
|WestUs|device1|2016-01-08T01:08:00Z|
|WestUs|device2|2016-01-08T01:17:00Z|

<a id="sample-4" class="xliff"></a>

### Ejemplo 4

<a id="input" class="xliff"></a>

#### Entrada

Un objeto JSON con una matriz JSON anidada que contiene dos objetos JSON. Esta entrada muestra que las propiedades globales se pueden representar mediante el objeto JSON complejo.

```json
{
    "location":"WestUs",
    "manufacturer":{
        "name":"manufacturer1",
        "location":"EastUs"
    },
    "events":[
        {
            "id":"device1",
            "timestamp":"2016-01-08T01:08:00Z",
            "data":{
                "type":"pressure",
                "units":"psi",
                "value":108.09
            }
        },
        {
            "id":"device2",
            "timestamp":"2016-01-17T01:17:00Z",
            "data":{
                "type":"vibration",
                "units":"abs G",
                "value":217.09
            }
        }
    ]
}
```
<a id="output---2-events" class="xliff"></a>

#### Salida: 2 eventos

|location|manufacturer.name|manufacturer.location|events.id|events.timestamp|events.data.type|events.data.units|events.data.value|
|---|---|---|---|---|---|---|---|
|WestUs|manufacturer1|EastUs|device1|2016-01-08T01:08:00Z|pressure|psi|108.09|
|WestUs|manufacturer1|EastUs|device2|2016-01-08T01:17:00Z|vibration|abs G|217.09|

<a id="next-steps" class="xliff"></a>

## Pasos siguientes

* Vea el entorno en el [portal de Time Series Insights](https://insights.timeseries.azure.com)

