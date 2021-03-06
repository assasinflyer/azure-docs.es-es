# Información general
## [Azure y IoT](iot-hub-what-is-azure-iot.md)
## [¿Qué es Azure IoT Hub?](iot-hub-what-is-iot-hub.md)
## [Introducción a la administración de dispositivos](iot-hub-device-management-overview.md)

# [Introducción](iot-hub-get-started.md)

## Instalación de su dispositivo
### [Simulación de un dispositivo en su PC](iot-hub-get-started-simulated.md)
#### [.NET](iot-hub-csharp-csharp-getstarted.md)
#### [Java](iot-hub-java-java-getstarted.md)
#### [Node.js](iot-hub-node-node-getstarted.md)
#### [Python](iot-hub-python-getstarted.md)

### [Uso de un simulador en línea](iot-hub-raspberry-pi-web-simulator-get-started.md)

### [Uso de un dispositivo físico](iot-hub-get-started-physical.md)
#### [Raspberry Pi con Node.js](iot-hub-raspberry-pi-kit-node-get-started.md)
#### [Raspberry Pi con C](iot-hub-raspberry-pi-kit-c-get-started.md)

#### [Intel Edison con Node.js](iot-hub-intel-edison-kit-node-get-started.md)
#### [Intel Edison con C](iot-hub-intel-edison-kit-c-get-started.md)

#### [Adafruit Feather HUZZAH ESP8266 con Arduino IDE](iot-hub-arduino-huzzah-esp8266-get-started.md)
#### [Sparkfun ESP8266 Thing Dev con Arduino IDE](iot-hub-sparkfun-esp8266-thing-dev-get-started.md)
#### [Adafruit Feather M0 con Arduino IDE](iot-hub-adafruit-feather-m0-wifi-kit-arduino-get-started.md)

#### Uso de IoT Gateway Starter Kit
##### [Configuración de Intel NUC como una puerta de enlace](iot-hub-gateway-kit-c-lesson1-set-up-nuc.md)
##### [Conexión de la puerta de enlace a IoT Hub](iot-hub-gateway-kit-c-iot-gateway-connect-device-to-cloud.md)
##### [Uso de la puerta de enlace para la conversión de datos](iot-hub-gateway-kit-c-use-iot-gateway-for-data-conversion.md)

## Escenarios de IoT ampliados
### [Administración de la mensajería de dispositivos en la nube con iothub-explorer](iot-hub-explorer-cloud-device-messaging.md)
### [Guardado de los mensajes de IoT Hub en el almacenamiento de datos de Azure](iot-hub-store-data-in-azure-table-storage.md)
### [Visualización de datos en Power BI](iot-hub-live-data-visualization-in-power-bi.md)
### [Visualización de datos con Web Apps](iot-hub-live-data-visualization-in-web-apps.md)
### [Previsión meteorológica con Azure Machine Learning](iot-hub-weather-forecast-machine-learning.md)
### [Administración de dispositivos con iothub-explorer](iot-hub-device-management-iothub-explorer.md)
### [Supervisión remota y notificaciones con Logic Apps](iot-hub-monitoring-notifications-with-azure-logic-apps.md)

# Procedimientos
## Plan
### [Comparación de IoT Hub con Event Hubs](iot-hub-compare-event-hubs.md)
### [Escalado de la solución](iot-hub-scaling.md)
### [Alta disponibilidad y recuperación ante desastres](iot-hub-ha-dr.md)
### [Compatibilidad con otros protocolos](iot-hub-protocol-gateway.md)
## [Desarrollo](iot-hub-how-to.md)
### [Guía del desarrollador](iot-hub-devguide.md)
#### [Guía de características de dispositivo a nube](iot-hub-devguide-d2c-guidance.md)
#### [Guía de características de nube a dispositivo](iot-hub-devguide-c2d-guidance.md)
#### [Envío y recepción de mensajes](iot-hub-devguide-messaging.md)
##### [Envío de mensajes de dispositivos a la nube a IoT Hub](iot-hub-devguide-messages-d2c.md)
##### [Lectura de mensajes de dispositivos a la nube desde el punto de conexión integrado](iot-hub-devguide-messages-read-builtin.md)
##### [Uso de puntos de conexión y reglas de enrutamiento personalizados para mensajes de dispositivos a la nube](iot-hub-devguide-messages-read-custom.md)
##### [Envío de mensajes de nube a dispositivo desde IoT Hub](iot-hub-devguide-messages-c2d.md)
##### [Creación y lectura de mensajes de IoT Hub](iot-hub-devguide-messages-construct.md)
##### [Elección de un protocolo de comunicación](iot-hub-devguide-protocols.md)
#### [Carga de archivos desde un dispositivo](iot-hub-devguide-file-upload.md)
#### [Administración de identidades de dispositivo](iot-hub-devguide-identity-registry.md)
#### [Control del acceso a IoT Hub](iot-hub-devguide-security.md)
#### [Descripción de dispositivo gemelos](iot-hub-devguide-device-twins.md)
#### [Invocación de métodos directos en un dispositivo](iot-hub-devguide-direct-methods.md)
#### [Programación de trabajos en varios dispositivos](iot-hub-devguide-jobs.md)
#### [Puntos de conexión de IoT Hub](iot-hub-devguide-endpoints.md)
#### [Lenguaje de consulta](iot-hub-devguide-query-language.md)
#### [Cuotas y limitación](iot-hub-devguide-quotas-throttling.md)
#### [Ejemplos de precios](iot-hub-devguide-pricing.md)
#### [SDK de dispositivos y servicios](iot-hub-devguide-sdks.md)
#### [Soporte para MQTT](iot-hub-mqtt-support.md)
#### [Glosario](iot-hub-devguide-glossary.md)
### [Uso del SDK de dispositivo IoT para C](iot-hub-device-sdk-c-intro.md)
#### [Uso de IoTHubClient](iot-hub-device-sdk-c-iothubclient.md)
#### [Uso del serializador](iot-hub-device-sdk-c-serializer.md)
### Procesamiento de mensajes de dispositivo a la nube
#### [.NET](iot-hub-csharp-csharp-process-d2c.md)
#### [Java](iot-hub-java-java-process-d2c.md)
### Envío de mensajes de nube a dispositivo
#### [.NET](iot-hub-csharp-csharp-c2d.md)
#### [Java](iot-hub-java-java-c2d.md)
#### [Node.js](iot-hub-node-node-c2d.md)
### [Carga de archivos desde dispositivos](iot-hub-csharp-csharp-file-upload.md)
### Introducción a los dispositivos gemelos
#### [Back-end de Node.js/Dispositivo de Node.js](iot-hub-node-node-twin-getstarted.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-twin-getstarted.md)
#### [Back-end de .NET/Dispositivo de .NET](iot-hub-csharp-csharp-twin-getstarted.md)
### Uso de métodos directos
#### [Back-end de Node.js/Dispositivo de Node.js](iot-hub-node-node-direct-methods.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-direct-methods.md)
#### [Back-end de Java/Dispositivo de Java](iot-hub-java-java-direct-methods.md)
### Introducción a la administración de dispositivos
#### [Back-end de Node.js/Dispositivo de Node.js](iot-hub-node-node-device-management-get-started.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-device-management-get-started.md)
#### [Back-end de Java/Dispositivo de Java](iot-hub-java-java-device-management-getstarted.md)
### Uso de propiedades gemelas
#### [Back-end de Node.js/Dispositivo de Node.js](iot-hub-node-node-twin-how-to-configure.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-twin-how-to-configure.md)
### Uso de trabajos de dispositivos para actualizar el firmware del dispositivo
#### [Back-end de Node/Dispositivo de Node](iot-hub-node-node-firmware-update.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-firmware-update.md)
### Programación y difusión de trabajos
#### [Back-end de Node.js/Dispositivo de Node.js](iot-hub-node-node-schedule-jobs.md)
#### [Back-end de .NET/Dispositivo de Node.js](iot-hub-csharp-node-schedule-jobs.md)
## administración
### Crear un centro de IoT 
#### [Uso del portal](iot-hub-create-through-portal.md)
#### [Uso de PowerShell](iot-hub-create-using-powershell.md)
#### [Uso de la CLI 2.0](iot-hub-create-using-cli.md)
#### [Uso de la CLI](iot-hub-create-using-cli-nodejs.md)
#### [Uso de la API de REST](iot-hub-rm-rest.md)
#### [Uso de una plantilla de PowerShell](iot-hub-rm-template-powershell.md)
#### [Uso de una plantilla de .NET](iot-hub-rm-template.md)
### Configuración de la carga de archivos
#### [Uso del portal](iot-hub-configure-file-upload.md)
#### [Uso de PowerShell](iot-hub-configure-file-upload-powershell.md)
#### [Uso de la CLI 2.0](iot-hub-configure-file-upload-cli.md)
### [Administración de identidades de dispositivos de Centro de IoT de forma masiva](iot-hub-bulk-identity-mgmt.md)
### [Métricas de uso](iot-hub-metrics.md)
### [Supervisión de operaciones](iot-hub-operations-monitoring.md)
### [Configuración de filtrado de IP](iot-hub-ip-filtering.md)
## Protección
### [Seguridad total](iot-hub-security-ground-up.md)
### [Procedimientos de seguridad recomendados](iot-hub-security-best-practices.md)
### [Arquitectura de seguridad](iot-hub-security-architecture.md)
### [Protección de su implementación de IoT](iot-hub-security-deployment.md)
## Azure IoT Edge
### [Información general](iot-hub-iot-edge-overview.md)
### Introducción
#### [Linux](iot-hub-linux-iot-edge-get-started.md)
#### [Windows](iot-hub-windows-iot-edge-get-started.md)
### Simulación de un dispositivo
#### [Linux](iot-hub-linux-iot-edge-simulated-device.md)
#### [Windows](iot-hub-windows-iot-edge-simulated-device.md)
### [Uso de un dispositivo real](iot-hub-iot-edge-physical-device.md)
### Creación de un módulo
#### [Java](iot-hub-iot-edge-create-module-java.md)
#### [.NET Framework](https://github.com/Azure-Samples/iot-edge-samples#how-to-run-the-net-module-sample-windows-10)
#### [.NET Standard](iot-hub-iot-edge-create-module-dotnet-core.md)
#### [Node.js](iot-hub-iot-edge-create-module-js.md)
### Compilación
#### [.NET Framework](https://github.com/Azure/iot-edge/tree/master/samples/dotnet_binding_sample)
#### [Módulo de .NET Core](https://github.com/Azure/iot-edge/tree/master/samples/dotnet_core_module_sample)
#### [Puerta de enlace administrada de .NET Core](https://github.com/Azure/iot-edge/tree/master/samples/dotnet_core_managed_gateway)
#### [Java](https://github.com/Azure/iot-edge/tree/master/samples/java_sample)
#### [Node.js](https://github.com/Azure/iot-edge/tree/master/samples/nodejs_simple_sample)
#### [Incorporación de un módulo dinámicamente](https://github.com/Azure/iot-edge/tree/master/samples/dynamically_add_module_sample)
#### [Módulo proxy fuera de proceso](https://github.com/Azure/iot-edge/tree/master/samples/proxy_sample)
#### [Host de módulo nativo](https://github.com/Azure/iot-edge/tree/master/samples/native_module_host_sample)

# Referencia
## [CLI de Azure](/cli/azure/iot)
## [.NET (servicio)](/dotnet/api/microsoft.azure.devices)
## [.NET (dispostivos)](/dotnet/api/microsoft.azure.devices.client)
## [Java (servicio)](/java/api/com.microsoft.azure.sdk.iot.service)
## [Java (dispositivos)](/java/api/com.microsoft.azure.sdk.iot.device)
## [SDK para Node.js](http://azure.github.io/azure-iot-sdk-node/)
## [SDK para dispositivos C](https://azure.github.io/azure-iot-sdk-c/index.html)
## [Azure IoT Edge](http://azure.github.io/iot-edge/)
## [REST (proveedor de recursos)](https://docs.microsoft.com/rest/api/iothub/iothubresource)
## [REST (identidades de dispositivos)](https://docs.microsoft.com/rest/api/iothub/deviceapi)
## [REST (dispositivos gemelos)](https://docs.microsoft.com/rest/api/iothub/devicetwinapi)
## [REST (Device Messaging)](https://docs.microsoft.com/rest/api/iothub/httpruntime)
## [REST (trabajos)](https://docs.microsoft.com/rest/api/iothub/jobapi)

# Temas relacionados
## [Conjunto de aplicaciones de IoT de Azure](https://azure.microsoft.com/documentation/suites/iot-suite/)
## [Azure Event Hubs](https://azure.microsoft.com/documentation/services/event-hubs/)
## [Stream Analytics](https://azure.microsoft.com/documentation/services/stream-analytics/)
## [Machine Learning](https://azure.microsoft.com/documentation/services/machine-learning/)

# Recursos
## [Catálogo de dispositivos de Azure Certified for IoT](https://catalog.azureiotsuite.com/)
## [Centro para desarrolladores de Azure IoT](https://azure.microsoft.com/develop/iot/)
## [Azure Roadmap](https://azure.microsoft.com/roadmap/)
## [herramienta DeviceExplorer](https://github.com/Azure/azure-iot-sdk-csharp/tree/master/tools/DeviceExplorer)
## [herramienta iothub-diagnostics](https://github.com/Azure/iothub-diagnostics)
## [herramienta iothub-explorer](https://github.com/Azure/iothub-explorer)
## [Ruta de aprendizaje](https://azure.microsoft.com/documentation/learning-paths/iot-hub/)
## [Foro de MSDN](https://social.msdn.microsoft.com/Forums/azure/en-US/home?forum=azureiothub)
## [Precios](https://azure.microsoft.com/pricing/details/iot-hub/)
## [Actualizaciones del servicio](https://azure.microsoft.com/updates/?product=iot-hub)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/azure-iot-hub)
## [Casos prácticos técnicos](https://microsoft.github.io/techcasestudies/#technology=IoT&sortBy=featured)
## [Vídeos](https://azure.microsoft.com/documentation/videos/index/?services=iot-hub)
