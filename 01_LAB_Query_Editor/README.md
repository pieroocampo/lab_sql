
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Práctica LAB 01 - Explorando el Editor de Consultas

Entrenamiento práctico en la plataforma Databricks con enfoque en las funcionalidades de Análisis (SQL, Query, Dask, DataViz, SQL end-point).

## Objetivos del Ejercicio

El objetivo de este laboratorio es conocer las funcionalidades de consulta (_Query_) de la plataforma Databricks, utilizando el lenguaje SQL (y las interfaces visuales), explorando las potencialidades Analíticas.
Los ejercicios deben ser ejecutados en la opción del Menú lateral "**SQL Editor**".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab01_editor_sql.png">

## Sesión 01: Estructura de TABLAS, BASE DE DATOS y CATÁLOGO

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab01_uc.png">

| Tópico | Comando |
| -- | -- |
| **Catálogo** | CREATE CATALOG <nombre_catalogo> |
| **Schema** | CREATE DATABASE IF NOT EXISTS <nombre_catalogo>.<nombre_base_datos>; |
| **Tabla** | CREATE OR REPLACE TABLE <nombre_catalogo>.<nombre_base_datos>.<nombre_tabla>; |
| **Vista** | CREATE OR REPLACE VIEW <nombre_catalogo>.<nombre_base_datos>.<nombre_tabla> AS ...; |

#### Referencia:
* [Databricks Ayuda - Sintaxis DDL](https://docs.databricks.com/sql/language-manual/sql-ref-syntax-ddl-create-table.html)

## Ejercicio 01.01 - Creación de la base de datos

``` sql
USE CATALOG academy;

CREATE DATABASE IF NOT EXISTS <tu_login>;

USE <tu_login>;
```

## Ejercicio 01.02 - Creación de la tabla

``` sql

CREATE OR REPLACE TABLE bronze_tipo_empresa 
  ( tipo_empresa      INT    COMMENT "Código del tipo de empresa",
    desc_tipo_empresa STRING COMMENT "Descripción del tipo de empresa" )
COMMENT "Tabla auxiliar, tipo de empresa"
```

 ## Ejercicio 01.03 - Insertando datos en la Tabla a través de SQL INSERT

 ``` sql
 INSERT INTO bronze_tipo_empresa VALUES (1, "NO DISPONIBLE") ;
 INSERT INTO bronze_tipo_empresa VALUES (2, "MICRO EMPRESA") ;
 INSERT INTO bronze_tipo_empresa VALUES (3, "PEQUENA EMPRESA") ;
 INSERT INTO bronze_tipo_empresa VALUES (4, "NO SE") ;
 INSERT INTO bronze_tipo_empresa VALUES (5, "NULL") ;
```

 ## Ejercicio 01.04 - Verificando el contenido de la TABLA

 ``` sql
SELECT * 
FROM bronze_tipo_empresa 
ORDER BY tipo_empresa
```

 ## Ejercicio 01.05 - Modificando el contenido de la TABLA

 ``` sql
UPDATE bronze_tipo_empresa  
SET desc_tipo_empresa = "OTRO" 
WHERE tipo_empresa = 5;


DELETE 
FROM bronze_tipo_empresa 
WHERE tipo_empresa = 4;
```

## Ejercicio 01.06 - Visualizando el Historial de Actualizaciones de la tabla

 ``` sql
DESCRIBE HISTORY bronze_tipo_empresa 
```

## Ejercicio 01.07 - Visualizando el contenido de la tabla en la versión anterior (TIME TRAVEL)

 ``` sql
SELECT * FROM bronze_tipo_empresa VERSION AS OF 5
```

## Ejercicio 01.08 - RESTAURANDO el contenido de la tabla a la versión anterior (TIME TRAVEL)

 ``` sql
RESTORE TABLE bronze_tipo_empresa TO VERSION AS OF 5 
```

## Ejercicio 01.09 - Visualizando las propiedades de la Tabla

 ``` sql
DESCRIBE DETAIL bronze_tipo_empresa 
```

## Ejercicio 01.10 - Visualizando las informaciones DETALLADAS de la Tabla

 ``` sql
DESCRIBE TABLE EXTENDED bronze_tipo_empresa
```
