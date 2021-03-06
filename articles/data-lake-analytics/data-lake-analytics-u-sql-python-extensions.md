---
title: "Extensión de los scripts de U-SQL con Python en Azure Data Lake Analytics | Microsoft Docs"
description: "Obtenga información acerca de cómo ejecutar código de Python en scripts de U-SQL"
services: data-lake-analytics
documentationcenter: 
author: saveenr
manager: sukvg
editor: cgronlun
ms.assetid: c1c74e5e-3e4a-41ab-9e3f-e9085da1d315
ms.service: data-lake-analytics
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: big-data
ms.date: 12/05/2016
ms.author: saveenr
translationtype: Human Translation
ms.sourcegitcommit: 624b0370a85827cb9feaa48924bfa76d9ae19d0f
ms.openlocfilehash: b3a9434df566d391e50e7755f9ab7fa880fe1d53


---

# <a name="tutorial-get-started-with-extending-u-sql-with-python"></a>Tutorial: Introducción a la extensión de U-SQL con Python

Las extensiones de Python para U-SQL permiten a los desarrolladores realizar la ejecución en paralelo de forma masiva de código Python. En el ejemplo siguiente se muestran los pasos básicos:

* Uso de la instrucción de REFERENCE ASSEMBLY para habilitar las extensiones de Python para el script de U-SQL
* Uso de la operación REDUCE para la partición de datos de entrada en una clave
* Las extensiones de Python para U-SQL incluyen un reductor integrado (Extension.Python.Reducer) que ejecuta código de Python en cada vértice asignado al reductor
* El script de U-SQL contiene el código de Python incrustado que tiene una función denominada usqlml_main que acepta un DataFrame de pandas como entrada y devuelve un DataFrame de pandas como resultado.

--

    REFERENCE ASSEMBLY [ExtPython];

    DECLARE @myScript = @"
    def get_mentions(tweet):
        return ';'.join( ( w[1:] for w in tweet.split() if w[0]=='@' ) )

    def usqlml_main(df):
        del df['time']
        del df['author']
        df['mentions'] = df.tweet.apply(get_mentions)
        del df['tweet']
        return df
    ";

    @t  = 
        SELECT * FROM 
           (VALUES
               ("D1","T1","A1","@foo Hello World @bar"),
               ("D2","T2","A2","@baz Hello World @beer")
           ) AS 
               D( date, time, author, tweet );

    @m  =
        REDUCE @t ON date
        PRODUCE date string, mentions string
        USING new Extension.Python.Reducer(pyScript:@myScript);

    OUTPUT @m
        TO "/tweetmentions.csv"
        USING Outputters.Csv();

## <a name="how-python-integrates-with-u-sql"></a>¿Cómo se integra Python con U-SQL?

### <a name="datatypes"></a>Tipos de datos

* Columnas numéricas y de cadena de U-SQL convertidas tal cual entre pandas y U-SQL
* Valores Null de U-SQL convertidos a valores "NA" de Pandas y a partir de ellos

### <a name="schemas"></a>Esquemas

* Los vectores de índice en Pandas no son compatibles en U-SQL. Todas las tramas de datos de entrada en la función Python siempre tienen un índice numérico de 64 bits comprendido entre 0 y el número de filas menos 1. 
* Los conjuntos de datos de U-SQL no pueden tener nombres de columna duplicados
* Los nombres de columna de conjuntos de datos de U-SQL que no son cadenas. 

### <a name="python-versions"></a>Versiones de Python
Se admite solo Python 3.5.1 (compilado para Windows). 

### <a name="standard-python-modules"></a>Módulos estándar de Python
Se incluyen todos los módulos estándar de Python.

### <a name="additional-python-modules"></a>Módulos adicionales de Python
Además de las bibliotecas estándar de Python, se incluyen varias bibliotecas de python de uso frecuente:

    pandas
    numpy
    numexpr

### <a name="exception-messages"></a>Mensajes de excepción
Actualmente, se muestra una excepción en el código de Python como un error genérico de vértices. En el futuro, los mensajes de error de trabajo de U-SQL mostrarán el mensaje de excepción de Python.

### <a name="input-and-output-size-limitations"></a>Limitaciones de tamaño de entrada y salida
Cada vértice tiene una cantidad limitada de memoria asignada a él. Actualmente, ese límite es de 6 GB para AU. Dado que las DataFrames de entrada y salida deben existir en la memoria en el código de Python, el tamaño total de la entrada y salida no puede superar los 6 GB.

## <a name="see-also"></a>Consulte también
* [Información general de Análisis de Microsoft Azure Data Lake](data-lake-analytics-overview.md)
* [Desarrollo de scripts de U-SQL mediante Data Lake Tools for Visual Studio](data-lake-analytics-data-lake-tools-get-started.md)
* [Uso de funciones de ventana de U-SQL para trabajos de Análisis de Azure Data Lake](data-lake-analytics-use-window-functions.md)




<!--HONumber=Dec16_HO3-->


