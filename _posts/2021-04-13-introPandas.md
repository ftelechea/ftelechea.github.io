---
layout: post
title: Introducción a Pandas
subtitle: Conceptos Básicos
tags: [pandas, python]
comments: true
---

## ¿Qué es pandas?

<img src="https://pandas.pydata.org/static/img/pandas.svg"
     alt="Pandas Logo"
     style="float: left; margin-right: 10px;" width="200" />
     
Pandas es una biblioteca de software, para ser usada con el lenguaje de programación Python, con el fin de procesar y analizar datos desde distintas fuentes.
A continuación aparecen algunos conceptos fundamentales, para poder trabajar con esta biblioteca.   
Para poder utilizar Pandas, luego de su instalación (con los manejadores de paquetes de Python pip o conda), deberá importar la biblioteca con la siguiente línea de código:

```python
import pandas as pd
```

## Objetos principales de pandas

Hay dos tipos de objetos principales en pandas: El **DataFrame** y las **Series**

El Dataframe es una tabla, es decir su estructura está compuesta por filas y columnas. Es posible crear un Dataframe a partir de un diccionario de Python, donde cada clave del diccionario corresponde al nombre de una columna y los valores para esta columna están dados por un array. Por ejemplo:


```python
pd.DataFrame({"Vendedor": ["Juan", "Fernando", "Claudia", "Sofia"], "Ventas": [22000, 27560, 32550, 19760]})
```

| | Vendedor | Ventas |
| :------ |:--- | :--- |
| 0 | Juan | 22000 |
| 1 | Fernando | 27560 |
| 2 | Claudia | 32550 |
| 3 | Sofia | 19760 |

Un objeto **Series** hace referencia a una columna del DataFrame, podemos conceptualizar al DataFrame como un grupo de Series.
Es importante tener claro el concepto de estos objetos (Dataframe y Series), aunque la mayoría de las veces no creamos estas estructuras a mano, sino que se generan a partir de distintas fuentes de datos. La biblioteca pandas cuenta con métodos que nos permiten leer datos desde archivos CSV (formato de texto plano, muy utilizado en ciencia de datos), planillas de Excel, bases de datos, etc. A continuación veremos como crear Dataframes a partir de algunas de estas fuentes de datos.

## Leer archivos CSV (Comma Separated Values)

Este tipo de fuente de datos, refiere a archivos de texto plano que contienen columnas separadas por comas y filas de datos en cada línea de texto del archivo. Esto se ajusta perfectamente a la estructura de tabla de un Dataframe. 
En el catálogo de datos abiertos, se encuentra un gran conjunto de datos en formato CSV para su análisis. Por ejemplo, podemos acceder a un conjunto de datos con información de siniestros de tránsito en el siguiente link: 

[Catálogo de Datos Abiertos - Siniestros de Tránsito](https://catalogodatos.gub.uy/dataset/unasev-fallecidos_siniestros_transito/resource/39e86b6b-ae19-4f71-a75a-4a83bfcb2d14)

Para generar un DataFrame a partir de los datos de un archivo CSV, la biblioteca pandas cuenta con el método read_csv. Veamos un ejemplo a continuación:

```python
pd.read_csv("fallecidos-nueva-2019.csv", encoding = "Latin")
```
El parámetro opcional encoding es necesario utilizarlo en este caso, ya que el archivo no fue generado con el encoding UTF.

Si en un cuaderno de Jupyter, escribiéramos en una celda de código lo que aparece a continuación, en la celda "Out" veríamos los primeros registros del Dataframe generado a partir de los datos del archivo CSV.

```python
#generar un DataFrame con el método read_csv que se asignará a la variable df
#Luego se ejecuta el método head(), para visualizar los primeros 5 registros del DataFrame
df = pd.read_csv("fallecidos-nueva-2019.csv", encoding = "Latin")
df.head()
```

![View Dataframe](/images/result_read_csv.png)






