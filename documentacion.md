# EXPLORACIÓN
## CUSTOMER FLIGHT ACTIVITY
Customer Flight Activity: todas las columnas son numéricas. Concretamente INT a excepción de Points Accumulated  que es FLOAT.

+ 40.000 registros, 9 columnas.

**Describe**
- 1º Número de cliente(min): 100018 - 999986
- 1º Año a contar (min): 2017
- Último año(max): 2018
- Flights booked: min = 0; max = 21
- Companions: max 11
- Total flights: max 32
- Distancias: 0 - 6293
- Puntos acumulados: 0 - 676.5
- P. Canjeados: 0 - 876
- Dólares canjeados: 0 - 71

**.info()**

No hay nulos en el flight activity. Reviso con isnull y si confirmo, paso a buscar duplicados teniendo en cuenta que la columna Loyalty Number son números identificativos de clientes.

**.isnull().sum()**

Después de varios intentos con distintos métodos me doy cuenta de que hay clientes que tienen 0 vuelos en el total. Creo que quiero borrarlos. Pero antes voy a explorar el segundo dataframe

No hay NULOS! HAY CEROS!!!! 

**Inspirada, se me ocurre, de repente, crear una maravillosa función para crear un diccionario con las columnas con ceros y el número de ceros que tiene cada una de ellas**

{'flights_booked': 196128,
 'flights_with_companions': 295023, **> 50%**
 'total_flights': 196128, 
 'distance': 196128,
 'points_accumulated': 196128,
 'points_redeemed': 379579, **casi 100%**
 'dollar_cost_points_redeemed': 379579 **casi 100%**}

 Algunas columnas son casi el 100%, flights with companions supera el 50% y el resto está muy cerca de llegar al 50%

 Esto me ayudará a revisar qué columnas me interesa eliminar

## CUSTOMER LOYALTY HISTORY

Varios tipos de columnas. Veo NaN's sólo en las columnas de cancellation month y cancellation year. 

filas 16737, columnas 16

**Describe**

- Loyalty Number: 100100018 - 999986 (igual que en flight activity)
- Salary: **MINIMO NEGATIVO(?)** - max 407228
- CLV : minimo 1898 - maximo 83325
- Enrollment year: 2012 - 2018
- Cancellation Year: 2013 - 2018
- Cancellation Month: 1 - 12 (tiene sentido porque son los meses del año)

**Info**

Solo hay NaN's efectivamente en las columnas salary y  de cancelación (year y month)ç
Confirmo con isnull()


14670 registros NaN. Significa que la mayoría de clientes no han cancelado aunque también significa que tenemos 2000 clientes que sí cancelaron y es posible que sean los 0 del otro dataframe

He hecho un df con los not nulls en cancellation (O SEA, LOS QUE SÍ HAN CANCELADO) = df_not_null_history

**Arreglamos el problema de la columna salary (tiene un mínimo con un número negativo)**


# LIMPIEZA


**PREGUNTAS A RESPONDER**
1. ¿Cómo se distribuye la **cantidad de vuelos** reservados por mes durante el año?
2. ¿Existe una relación entre la **distancia de los vuelos** y los **puntos acumulados** por los cliente?
3. ¿Cuál es la distribución de los clientes por **provincia o estado**?
4. ¿Cómo se compara el **salario** promedio entre los diferentes **niveles educativos** de los clientes?
5. ¿Cuál es la proporción de clientes con diferentes tipos de **tarjetas de fidelidad**?
6. ¿Cómo se distribuyen los clientes según su **estado civil y género**?

**EN LAS PREGUNTAS SE MENCIONA:**

- Cantidad de vuelos
- Distancia de vuelos
- Puntos acumulados
- Provincias y Estados clientes
- Salarios
- Niveles educativos
- Tarjetas de fidelidad
- Estado civil y género

La mayoría de estos datos están en el segundo df y no en el primero. Hago listados de columnas a borrar.
## FLIGHT ACTIVITY
### LIMPIANDO DUPLICADOS Y OTROS
**Duplicados**
Examino y elimino

**He creado una función para cambiar los nombres la columnas. Lo utilizaré también en el siguiente df**
Con tanto 0, seguro que hay duplicados. Reviso duplicados. 1864. Los elimino.

## LOYALTY HISTORY
### Arreglamos el problema de la columna salary (tiene un mínimo con un número negativo)


## LISTA COLUMNAS FLIGHT ACTIVITY
 0. loyalty_number *  
 1. year  *     
 2. month *
 3. flights_booked  * 
 4. flights_with_companions (borrar)
 5. total_flights (borrar)     
 6. distance *            
 7. points_accumulated *   
 8. points_redeemed   (borrar)    
 9. dollar_cost_points_redeemed (borrar)

 ## LISTA COLUMNAS LOYALTY HISTORY
 0. loyalty_number *
 1. country*
 2. province*
 3. city *
 4. postal_code (borrar)
 5. gender * 
 6. education *
 7. salary *
 8. marital_status  *
 9. loyalty_card  *
 10. clv (borrar)
 11. enrollment_type *
 12. enrollment_year 
 13. enrollment_month 
 14. cancellation_year
 15. cancellation_month