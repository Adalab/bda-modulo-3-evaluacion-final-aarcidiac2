**CUSTOMER FLIGHT ACTIVITY**
Customer Flight Activity: todas las columnas son numéricas. Concretamente INT a excepción de Points Accumulated  que es FLOAT.

+ 40.000 registros, 9 columnas.

Según .info() no hay nulos en el flight activity. Reviso con isnull y si confirmo, paso a buscar duplicados teniendo en cuenta que la columna Loyalty Number son números identificativos de clientes.

Después de varios intentos con distintos métodos me doy cuenta de que hay clientes que tienen 0 vuelos en el total. Creo que quiero borrarlos. Pero antes voy a explorar el segundo dataframe

No hay NULOS! HAY CEROS!!!! df_flight_activity[(df_flight_activity == 0)] para ver cuantos

Quiero borrar filas. Pero antes voy a explorar el otro dataframe

**CUSTOMER LOYALTY HISTORY**

Veo NaN's sólo en las columnas de cancellation month y cancellation year. 14670 registros NaN. Significa que la mayoría de clientes no han cancelado aunque también significa que tenemos 2000 clientes que sí cancelaron y es posible que sean los 0 del otro dataframe

Voy a ver qué hay en los registros donde no hay nulos en cancellation year con notna()