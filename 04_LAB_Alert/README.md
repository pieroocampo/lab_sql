<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Práctica LAB 04 - Creación de una ALERTA

Entrenamiento práctico en la plataforma Databricks centrado en las funcionalidades de análisis (SQL, Query, Dask, DataViz, SQL end-point).

## Objetivos del Ejercicio

El objetivo de este laboratorio es explorar las funcionalidades de creación de una ALERTA.

</br></br>

## Ejercicio 04.01 - Creación de la consulta

``` sql

select dolar_cotizacion as valor_dolar
FROM <tu_login>.bronze_dolar
order by dolar_dia DESC;


```
</br></br>
Guarda la Consulta. Sugerencia: "Query_Alerta"+ <tu_login>
</br></br>


Ejercicio 04.02 - Creando la Alerta
Vamos a usar la opción del menú "ALERTA".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab04_1.png" style="height: 200px;">
</br></br>

Haz clic en el botón CREAR y configura la ALERTA como se muestra a continuación:

</br></br>

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab04_2.png" style="height: 700px;">
```


