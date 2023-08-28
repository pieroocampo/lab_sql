<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Laboratorio Práctico 05 - Explorando el Tablero (Panel de Control)

Entrenamiento práctico en la plataforma Databricks enfocado en las funcionalidades de análisis (SQL, Query, Dask, DataViz, SQL end-point).

## Objetivos del Ejercicio

El objetivo de este laboratorio es explorar las funcionalidades de consultas con Gráficos de Visualización y Filtros para luego montar un Panel de Control.

Vamos a utilizar el "Editor SQL".

## Ejercicio 05.01 - Creación de la Consulta

``` sql
SELECT * FROM academy.<tu_login>.bronze_dolar;


```
Resultado de la consulta:
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_01.png" style="height: 200px;">


</br></br>

## Ejercicio 05.02 - Creando la Visualización y el Filtro
En la barra de resultados, haz clic en el botón "+", y elige la opción "Visualización".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_02.png" style="height: 200px;">
En Tipo de Visualización, elige "LINE":

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_03.png" style="height: 200px;">
En la "X Column" (eje X), elige la variable "dolar_dia".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_04.png" style="height: 200px;">
En la "Y Columns" (eje Y), elige la variable "dolar_cotizacion".
Elige también la forma de agregación: Media (Promedio).

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_05.png" style="height: 200px;">
Haz clic en el título de la visualización y renómbralo a "grafico_dolar".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_06.png" style="height: 150px;">
El resultado esperado es igual al gráfico de abajo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_07.png" style="height: 500px;">
Haz clic nuevamente en el botón "+", y añade un FILTRO:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_09.png" style="height: 150px;">
Elige la columna "dolar_anio" para usar en el FILTRO:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_10.png" style="height: 300px;">
El resultado se verá así:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_11.png" style="height: 250px;">
Guarda el resultado de la Consulta, con el nombre: "Query_Historico_dolar_" + <tu_login>.
</br></br></br>

## Ejercicio 05.03 - Creando el Dashboard
En el Menú Lateral, elige la opción DASHBOARDS:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_08.png" style="height: 150px;">
Haz clic en la opción CREATE DASHBOARD.

En la pantalla del Dashboard, haz clic en el botón "ADD", y elige la opción: "TEXT BOX".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_12.png" style="height: 100px;">
En el campo texto, escribe lo siguiente:

``` md

![alt text](https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png)


```

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_13.png" style="height: 300px;">

Repite la operación.  haz clic en el botón "ADD", y elige la opción: "TEXT BOX". Escribe lo siguiente:

``` md


![alt text](https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_dolar.png)

```

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_14.png" style="height: 200px;">

Haz clic nuevamente en el botón ADD, y selecciona la opción "VISUALIZATION".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_15.png" style="height: 200px;">

Elige el nombre de la consulta que se guardó en el ejercicio anterior.

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_16.png" style="height: 250px;">

Haz clic nuevamente en el botón ADD, y selecciona la opción "FILTRO", y configura según lo siguiente:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_17.png" style="height: 200px;">

</br></br></br>

El resultado final debería verse como sigue. Guarda tu dashboard.

</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_final.png" style="height: 600px;">
