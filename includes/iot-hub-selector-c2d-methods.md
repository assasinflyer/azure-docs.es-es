> [!div class="op_single_selector"]
> * [Node.js](../articles/iot-hub/iot-hub-node-node-direct-methods.md)
> * [C#](../articles/iot-hub/iot-hub-csharp-node-direct-methods.md)
> * [Java](../articles/iot-hub/iot-hub-java-java-direct-methods.md)

Azure IoT Hub es un servicio totalmente administrado que permite la comunicación bidireccional confiable y segura entre millones de dispositivos y un back-end de la solución. En tutoriales anteriores ([Introducción a Iot Hub] y [Envío de mensajes de nube a dispositivo con IoT Hub]) se muestra cómo usar la funcionalidad básica de mensajería de dispositivo a nube y de nube a dispositivo de IoT Hub. IoT Hub también ofrece la capacidad de invocar métodos temporales en dispositivos desde la nube. Los métodos directos representan una interacción solicitud-respuesta con un dispositivo similar a una llamada HTTP en el sentido de que se completan correctamente o generan un error de inmediato (tras un tiempo de espera que especifica el usuario) para informar al usuario sobre el estado de la llamada. En el artículo [Invocación de un método directo en un dispositivo][lnk-devguide-methods], se describen los métodos directos con más detalle y se ofrece orientación sobre cuándo usarlos en lugar de mensajes de la nube al dispositivo o propiedades deseadas.

En este tutorial se muestra cómo realizar las siguientes acciones:

* Usar Azure Portal para crear un centro de IoT y una identidad de dispositivo en este.
* Crear una aplicación de dispositivo simulado con un método directo a la que se pueda llamar desde la nube.
* Crear una aplicación de consola que llame a un método directo en la aplicación de dispositivo simulado a través de su IoT Hub.

> [!NOTE]
> En la actualidad, los métodos directos solo son compatibles en dispositivos que se conecten a IoT Hub mediante el protocolo MQTT. Para instrucciones acerca de cómo convertir la aplicación de dispositivo existente para usar MQTT, consulte el artículo sobre [compatibilidad con MQTT][lnk-devguide-mqtt].


[lnk-devguide-methods]: ../articles/iot-hub/iot-hub-devguide-direct-methods.md
[lnk-devguide-mqtt]: ../articles/iot-hub/iot-hub-mqtt-support.md

[Envío de mensajes de nube a dispositivo con IoT Hub]: ../articles/iot-hub/iot-hub-csharp-csharp-c2d.md
[Introducción a Iot Hub]: ../articles/iot-hub/iot-hub-node-node-getstarted.md