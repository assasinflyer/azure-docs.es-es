---
title: Uso de Pig de Hadoop en HDInsight | Microsoft Docs
description: Aprenda a usar Pig con Hadoop en HDInsight.
services: hdinsight
documentationcenter: 
author: Blackmist
manager: jhubbard
editor: cgronlun
tags: azure-portal
ms.assetid: acfeb52b-4b81-4a7d-af77-3e9908407404
ms.service: hdinsight
ms.custom: hdinsightactive
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: big-data
ms.date: 05/26/2017
ms.author: larryfr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8f987d079b8658d591994ce678f4a09239270181
ms.openlocfilehash: e7519981642c438ca25b0479324ee159545bac8e
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017


---
# <a name="use-pig-with-hadoop-on-hdinsight"></a>Uso de Pig con Hadoop en HDInsight

Aprenda a usar [Apache Pig](http://pig.apache.org/) con HDInsight...

Pig es una plataforma para crear programas de Hadoop mediante un lenguaje de procedimientos que se conoce como *Pig Latin*. Pig es una alternativa a Java para crear soluciones *MapReduce* y se incluye con HDInsight de Azure. Utilice la tabla siguiente para conocer las distintas formas de usar Pig con HDInsight:

| **Utilícelo** si desea... | ...un shell **interactivo** | ...procesamiento por**lotes** | ...con este **sistema operativo de clúster** | ...desde este **sistema operativo de cliente** |
|:--- |:---:|:---:|:--- |:--- |
| [SSH](hdinsight-hadoop-use-pig-ssh.md) |✔ |✔ |Linux |Linux, Unix, Mac OS X o Windows |
| [API DE REST](hdinsight-hadoop-use-pig-curl.md) |&nbsp; |✔ |Linux o Windows |Linux, Unix, Mac OS X o Windows |
| [.NET SDK para Hadoop](hdinsight-hadoop-use-pig-dotnet-sdk.md) |&nbsp; |✔ |Linux o Windows |Windows (por ahora) |
| [Windows PowerShell](hdinsight-hadoop-use-pig-powershell.md) |&nbsp; |✔ |Linux o Windows |Windows |
| [Escritorio remoto](hdinsight-hadoop-use-pig-remote-desktop.md) (HDInsight 3.2 y 3.3) |✔ |✔ |Windows |Windows |

> [!IMPORTANT]
> Linux es el único sistema operativo que se usa en la versión 3.4 de HDInsight, o en las superiores. Consulte la información sobre la [retirada de HDInsight en Windows](hdinsight-component-versioning.md#hdi-version-33-nearing-retirement-date).

## <a id="why"></a>¿Por qué usar Pig?

Uno de los desafíos del procesamiento de datos mediante el uso de MapReduce en Hadoop es la implementación de la lógica de procesamiento únicamente con un mapa y una función de reducción. Para el procesamiento complejo, a menudo debe interrumpir el procesamiento en varias operaciones de MapReduce que están encadenadas para lograr el resultado deseado.

Pig permite definir los procesos como una serie de transformaciones por la que fluyen los datos para producir el resultado deseado.

El lenguaje de Pig Latin le permite describir el flujo de datos desde entrada sin formato, a través de una o varias transformaciones, para producir el resultado deseado. Los programas de Pig Latin siguen este patrón general:

* **Carga**: Los datos leídos que se van a manipular desde el sistema de archivos.

* **Transformación**: manipula los datos.

* **Volcado o almacén**: generar datos en la pantalla o almacenarlos para su procesamiento.

### <a name="user-defined-functions"></a>Funciones definidas por el usuario

Pig Latin también admite las funciones definidas por el usuario (UDF), que le permiten invocar componentes externos que implementan la lógica que es difícil de modelar en Pig Latin.

Para más información sobre Pig Latin, consulte el [manual de referencia de Pig Latin 1](http://pig.apache.org/docs/r0.7.0/piglatin_ref1.html) y el [manual de referencia de Pig Latin 2](http://pig.apache.org/docs/r0.7.0/piglatin_ref2.html).

Para obtener un ejemplo del uso de UDF con Pig, vea los siguientes documentos:

* [Utilice DataFu con Pig en HDInsight](hdinsight-hadoop-use-pig-datafu-udf.md) - DataFu es una colección de UDF útiles mantenida por Apache
* [Uso de Python con Pig y Hive en HDInsight](hdinsight-python.md)
* [Uso de C# con Hive y Pig en HDInsight](hdinsight-hadoop-hive-pig-udf-dotnet-csharp.md)

## <a id="data"></a>Datos de ejemplo

HDInsight proporciona diversos conjuntos de datos de ejemplo que se almacenan en los directorios `/example/data` y `/HdiSamples`. Estos directorios están en el almacenamiento predeterminado del clúster. El ejemplo de Pig de este documento utiliza el archivo *log4j* de `/example/data/sample.log`.

Cada registro del archivo consta de una línea de campos que contiene un campo `[LOG LEVEL]` para mostrar el tipo y la gravedad, por ejemplo:

    2012-02-03 20:26:41 SampleClass3 [ERROR] verbose detail for id 1527353937

En el ejemplo anterior, el nivel de registro es ERROR.

> [!NOTE]
> También puede generar un archivo log4j con la herramienta de registro [Apache Log4j](http://en.wikipedia.org/wiki/Log4j) y luego cargarlo en el blob. Consulte [Carga de datos en HDInsight](hdinsight-upload-data.md) para obtener instrucciones. Para obtener más información sobre el uso de los blobs en Azure Storage con HDInsight, consulte [Uso de Azure Blob Storage con HDInsight](hdinsight-hadoop-use-blob-storage.md).

## <a id="job"></a>Trabajo de ejemplo

El siguiente trabajo de Pig Latin carga el archivo `sample.log` desde el almacenamiento predeterminado para el clúster de HDInsight. A continuación, realiza una serie de transformaciones que generan un recuento de cuántas veces se ha producido cada nivel de registro en los datos de entrada. Los resultados se escriben en STDOUT.

    LOGS = LOAD 'wasbs:///example/data/sample.log';
    LEVELS = foreach LOGS generate REGEX_EXTRACT($0, '(TRACE|DEBUG|INFO|WARN|ERROR|FATAL)', 1)  as LOGLEVEL;
    FILTEREDLEVELS = FILTER LEVELS by LOGLEVEL is not null;
    GROUPEDLEVELS = GROUP FILTEREDLEVELS by LOGLEVEL;
    FREQUENCIES = foreach GROUPEDLEVELS generate group as LOGLEVEL, COUNT(FILTEREDLEVELS.LOGLEVEL) as COUNT;
    RESULT = order FREQUENCIES by COUNT desc;
    DUMP RESULT;

En la siguiente imagen se muestra un resumen de lo que hace cada transformación a los datos.

![Representación gráfica de las transformaciones][image-hdi-pig-data-transformation]

## <a id="run"></a>Ejecutar el trabajo de Pig Latin

HDInsight puede ejecutar trabajos de Pig Latin mediante una variedad de métodos. Use la tabla siguiente para decidir cuál es el método adecuado para usted luego siga el vínculo para ver un tutorial.

| **Utilícelo** si desea... | ...un shell **interactivo** | ...procesamiento por**lotes** | ...con este **sistema operativo de clúster** | ...de este **cliente** |
|:--- |:---:|:---:|:--- |:--- |
| [SSH](hdinsight-hadoop-use-pig-ssh.md) |✔ |✔ |Linux |Linux, Unix, Mac OS X o Windows |
| [Curl](hdinsight-hadoop-use-pig-curl.md) |&nbsp; |✔ |Linux o Windows |Linux, Unix, Mac OS X o Windows |
| [.NET SDK para Hadoop](hdinsight-hadoop-use-pig-dotnet-sdk.md) |&nbsp; |✔ |Linux o Windows |Windows (por ahora) |
| [Windows PowerShell](hdinsight-hadoop-use-pig-powershell.md) |&nbsp; |✔ |Linux o Windows |Windows |
| [Escritorio remoto](hdinsight-hadoop-use-pig-remote-desktop.md) (HDInsight 3.2 y 3.3) |✔ |✔ |Windows |Windows |

> [!IMPORTANT]
> Linux es el único sistema operativo que se usa en la versión 3.4 de HDInsight, o en las superiores. Consulte la información sobre la [retirada de HDInsight en Windows](hdinsight-component-versioning.md#hdi-version-33-nearing-retirement-date).

## <a name="pig-and-sql-server-integration-services"></a>Pig y SQL Server Integration Services

Puede usar SQL Server Integration Services (SSIS) para ejecutar un trabajo de Pig. El paquete de características de Azure para SSIS proporciona los siguientes componentes que funcionan con trabajos de Pig en HDInsight.

* [Tarea de Pig de Azure HDInsight][pigtask]

* [Administrador de conexiones de suscripción de Azure][connectionmanager]

Obtenga más información sobre el paquete de características de Azure para SSIS [aquí][ssispack].

## <a id="nextsteps"></a>Pasos siguientes
Ahora que aprendió a usar Pig con HDInsight, use los siguientes vínculos para explorar otras formas de trabajar con HDInsight de Azure.

* [Carga de datos en HDInsight][hdinsight-upload-data]
* [Uso de Hive con HDInsight][hdinsight-use-hive]
* [Uso de Sqoop con HDInsight](hdinsight-use-sqoop.md)
* [Uso de Oozie con HDInsight](hdinsight-use-oozie.md)
* [Uso de trabajos de MapReduce con HDInsight][hdinsight-use-mapreduce]

[apachepig-home]: http://pig.apache.org/
[putty]: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
[curl]: http://curl.haxx.se/
[pigtask]: http://msdn.microsoft.com/library/mt146781(v=sql.120).aspx
[connectionmanager]: http://msdn.microsoft.com/library/mt146773(v=sql.120).aspx
[ssispack]: http://msdn.microsoft.com/library/mt146770(v=sql.120).aspx


[hdinsight-upload-data]: hdinsight-upload-data.md

[hdinsight-admin-powershell]: hdinsight-administer-use-powershell.md

[hdinsight-use-hive]: hdinsight-use-hive.md
[hdinsight-use-mapreduce]: hdinsight-use-mapreduce.md

[hdinsight-provision]: hdinsight-hadoop-provision-linux-clusters.md
[hdinsight-submit-jobs]: hdinsight-submit-hadoop-jobs-programmatically.md#mapreduce-sdk

[Powershell-install-configure]: /powershell/azureps-cmdlets-docs

[powershell-start]: http://technet.microsoft.com/library/hh847889.aspx


[image-hdi-pig-data-transformation]: ./media/hdinsight-use-pig/HDI.DataTransformation.gif

