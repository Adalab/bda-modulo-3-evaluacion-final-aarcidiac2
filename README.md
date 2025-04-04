# README: Módulo 3 Ejercicio de evaluación final 

Mediante este proyecto analizamos los datos de dos archivos en los que se almacenan información sobre la actividad y la lealtad de los clientes de una aerolínea. Utilizando Pandas, observamos y analizamos los datos de los dos archivos .csv que se nos facilitan. Posteriormente los limpiamos, los unimos, y realizamos distintas visualizaciones para sacar conclusiones de los datos finales que tenemos.

## Exploración de datos

Mediante métodos como .describe() o .info() revisamos los tipos de datos que tenemos en estos .csv's.

### Customer Flight Activity

Está formado por más de 40.000 registros y 9 columnas. En este csv nos hemos encontrado una mayoría de columnas numéricas y muchos ceros. Cubren solo los años 2017 y 2018.

Analizamos dónde se encuentran la mayoría de los ceros lo cual nos ayuda a posteriormente elegir las columnas a eliminar o modificar.

### Customer Loyalty History

Es un conjunto de datos más diverso donde encontramos también columnas categóricas y NaN's en vez de 0. También encontramos que el dato mínimo que nos da la columna salary es negativo, lo cual no es posible.

## Limpieza

Para que los datos sean lo más precisos y coherentes posibles y que estén en un formato adecuado, hacemos lo que llamamos "limpieza de datos".

### Customer Flight Activity

En este conjunto de datos eliminamos duplicados y creamos una funcion para cambiar los nombres de las columnas por un nombre más fácil de utilizar.

### Customer Loyalty History

Para este conjunto arreglamos el problema del salary asegurándonos de que los valores negativos no intenten señalarnos algo importante sino que sean un error. 

##

Seleccionamos las columnas que no nos hacen falta, no nos aporta información relevante, o que acumulan demasiados nulos para eliminarlas. Tenemos mucho cuidado al eliminar datos. Existen columnas que, aunque el cliente no nos pregunte por la información que contienen, no las borramos porque creemos que pueden resultar interesantes en futuros análisis.

## Unión

Para la unión de los DataFrames utilizo el método merge() porque permite utilizar dataframes basándonos en las columnas comunes. Esto lo hacemos teniendo en cuenta que queremos preservar las filas de los dos csv's. Utilizando df_flight_activity como "left" conseguiremos ese resultado ya que tiene más filas que df_loyalty_history.

## Visualización

Respondemos a las distintas preguntas que se nos hace en la evaluación a través de los métodos de visualización estudiados de las librerías de matplotlib y seaborn 

**PREGUNTAS A RESPONDER**
1. ¿Cómo se distribuye la **cantidad de vuelos** reservados por mes durante el año?
2. ¿Existe una relación entre la **distancia de los vuelos** y los **puntos acumulados** por los cliente?
3. ¿Cuál es la distribución de los clientes por **provincia o estado**?
4. ¿Cómo se compara el **salario** promedio entre los diferentes **niveles educativos** de los clientes?
5. ¿Cuál es la proporción de clientes con diferentes tipos de **tarjetas de fidelidad**?
6. ¿Cómo se distribuyen los clientes según su **estado civil y género**?

Escogemos los tipos de representación de datos en función a los tipos de datos que contienen en las columnas por las que nos preguntan y si buscan un conteo de registros u otro tipo de comparaciones