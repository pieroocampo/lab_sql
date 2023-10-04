
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Práctica LAB 03 - Explorando el Query Profiler

Entrenamiento práctico en la plataforma Databricks centrado en las funcionalidades de análisis (SQL, Query, Dask, DataViz, SQL end-point).

## Objetivos del Ejercicio

El objetivo de este laboratorio es explorar las funcionalidades del plan de ejecución de consultas (Query Profiler). Identificando los cuellos de botella y oportunidades de mejora en rendimiento.
</br></br>

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/desnormaliza.png">

Vamos a usar el "Editor SQL".

## Ejercicio 03.01 - Creación de la Consults

``` sql

USE <tu_login>;


CREATE OR REPLACE TABLE silver_empresas AS
SELECT 
  est.cnpj_basico AS cnpj_basico,
  matriz_filial AS nombre_matriz,
  nombre_comercial AS nombre_comercial_empresa,
  razon_social AS nombre_razon_social,
  codigo_situacion_cadastral AS codigo_situacion_cadastral,
  data_situacion_cadastral AS data_situacion_cadastral,
  motivo_situacion_cadastral AS motivo_situacion_cadastral,
  inicio_actividades AS inicio_actividades,
  cnae_principal AS cnae_principal,
  cnae.descripcion AS cnae_descripcion,
  tipo_via AS direccion_tipo_via,
  via AS direccion_nombre_via,
  numero AS direccion_numero_via,
  colonia AS direccion_colonia,
  cp AS direccion_codigo_postal,
  uf AS direccion_entidad_federativa,
  codigo_municipio_siafi AS codigo_municipio_siafi,
  calificacion_responsable AS calificacion_responsable,
  capital_social AS val_capital_social,
  emp.tipo_empresa AS cod_tipo_empresa,
  tipo.desc_tipo_empresa AS desc_tipo_empresa,
  entidad_federativa_responsable AS entidad_federativa_responsable
from bronze_estabelecimentos est
join bronze_empresas emp
on est.cnpj_basico = emp.cnpj_basico
left join bronze_cnae cnae
on est.cnae_principal = cnae.cod_cnae
left join bronze_tipo_empresa tipo
on emp.tipo_empresa = tipo.tipo_empresa


```

## Ejercicio 03.02 - Visualizando el Historial de ejecución de las Consultas


En el Menú, elija la opción "Historial de Consultas"

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_1.png" style="height: 200px;">
Filtre las Consultas (por ejemplo, seleccione sus propias Queries):

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_2.png" style="height: 300px;">


## Ejercicio 03.03 - Analizando el Detalle de la Ejecución

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_3.png" style="height: 200px;">


## Ejercicio 03.04 - Analizando el Query Profiler

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_4.png" style="height: 200px;">


## Ejercicio 03.05 - Analizando el Plan de Ejecución

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_5.png" style="height: 250px;">

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_6.png" style="height: 700px;">


## Ejercicio 03.06 - Añadiendo Comentarios en la Tabla y en las Columnas

``` sql
USE CATALOG academy;

USE <tu_login>;

COMMENT ON TABLE silver_empresas IS 'Tabla con datos de las empresas';

ALTER TABLE silver_empresas ALTER COLUMN cnpj_basico COMMENT 'Identificador';
ALTER TABLE silver_empresas ALTER COLUMN nombre_matriz COMMENT 'Nombre de la Matriz';
ALTER TABLE silver_empresas ALTER COLUMN nombre_comercial_empresa COMMENT 'Nombre Comercial';
ALTER TABLE silver_empresas ALTER COLUMN nombre_razon_social COMMENT 'Razón Social';
ALTER TABLE silver_empresas ALTER COLUMN codigo_situacion_cadastral COMMENT 'Código da Situación Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN data_situacion_cadastral COMMENT 'Datos de Situación Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN motivo_situacion_cadastral COMMENT 'Motivo de Situación Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN inicio_actividades COMMENT 'Inicio de actividaddes';
ALTER TABLE silver_empresas ALTER COLUMN cnae_principal COMMENT 'Código de Naturaleza Económica';
ALTER TABLE silver_empresas ALTER COLUMN cnae_descripcion COMMENT 'Descripción de Naturaleza Económica';
ALTER TABLE silver_empresas ALTER COLUMN direccion_tipo_via COMMENT 'Dirección - Tipo de Vía';
ALTER TABLE silver_empresas ALTER COLUMN direccion_nombre_via COMMENT 'Dirección - Nombre de Vía';
ALTER TABLE silver_empresas ALTER COLUMN direccion_numero_via COMMENT 'Dirección - Número de Vía';
ALTER TABLE silver_empresas ALTER COLUMN direccion_colonia COMMENT 'Dirección - Colonia';
ALTER TABLE silver_empresas ALTER COLUMN direccion_codigo_postal COMMENT 'Dirección - Código Postal';
ALTER TABLE silver_empresas ALTER COLUMN direccion_entidad_federativa COMMENT 'Dirección - Entidad Federativa';
ALTER TABLE silver_empresas ALTER COLUMN codigo_municipio_siafi COMMENT 'Código de Municipio';
ALTER TABLE silver_empresas ALTER COLUMN calificacion_responsable COMMENT 'Calificación del Responsable';
ALTER TABLE silver_empresas ALTER COLUMN val_capital_social COMMENT 'Valor del capital social';
ALTER TABLE silver_empresas ALTER COLUMN cod_tipo_empresa COMMENT 'Código del Tipo de Empresa';
ALTER TABLE silver_empresas ALTER COLUMN desc_tipo_empresa COMMENT 'Descripción del Tipo de Empresa';
ALTER TABLE silver_empresas ALTER COLUMN entidad_federativa_responsable COMMENT 'Entidad Federativa Responsable';
```

