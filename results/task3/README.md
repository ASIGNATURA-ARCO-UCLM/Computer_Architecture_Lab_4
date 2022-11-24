# Tarea 3: Paralelización con OpenMP

## Preguntas
* Una vez realizados los análisis correspondientes paraleliza el programa todo lo que puedas, fíjate en los comentarios marcados con "TODO" para ver donde tienes que incorporar código. Ten en cuenta que es posible que requiera usar modificadores de memoria o mecanismos de sincronización.

* ¿Cuántas hebras hay disponibles? ¿A qué crees que se debe este resultado?
   
   Uno, creemos que es por temas de eficiencia por no hacer un trabajo creando hilos extra que luego a lo mejor ni usa. Además si vemos cuantos hilos          disponibles dentro de un bucle que hemos paralelizado si que pone mas de uno.

* Comprueba que la ejecucion paralela y secuencial es la misma. Recuerda que estás trabajando con números decimales
    * ¿Cómo lo has comprobado?
    
    Sí, da el mismo resultado y lo que hemos hecho es ejecutar ambos códigos primero con los datos que venían por defecto y luego hemos cambiado algunos
    datos por si cambiaba el resultado pero también daba el mismo resultado.

* Realiza mediciones de tiempo para 2, 4, 8, 16, 32 y 64 hilos y añade los resultados de tiempo en una tabla junto a los resultados secuenciales. Además añade la ganancia obtenida por cada ejecución en comparación con la secuencial ¿Estos resultados se corresponden o se parecen a los estimados por intel advisor? Justifica tu respuesta.

    | Número de hilos | Tiempo | Ganancia |
    |--| -- | -- |
    |2|0,24 segundos| 
    |4|0,12 segundos|
    |8|0,09 segundos|
    |16|[0,12 - 0,08] segundos|
    |32|[0,12 - 0,08] segundos|
    |64|[0,12 - 0,09] segundos|
    
    Mientras que el resultado secuencial oscila entre los 0,006 y 0,005 segundos de media. Todos estos resultados se han obtenido con la opción -xCORE-AVX2     de compilación.

