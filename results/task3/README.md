# Tarea 3: Paralelización con OpenMP

## Preguntas
* Una vez realizados los análisis correspondientes paraleliza el programa todo lo que puedas, fíjate en los comentarios marcados con "TODO" para ver donde tienes que incorporar código. Ten en cuenta que es posible que requiera usar modificadores de memoria o mecanismos de sincronización.

* ¿Cuántas hebras hay disponibles? ¿A qué crees que se debe este resultado?
   
   Uno, creemos que es por temas de eficiencia por no hacer un trabajo creando hilos extra que luego a lo mejor ni usa. Además si vemos cuantos hilos disponibles dentro de un bucle que hemos paralelizado si que pone mas de uno.

* Comprueba que la ejecucion paralela y secuencial es la misma. Recuerda que estás trabajando con números decimales
    * ¿Cómo lo has comprobado?
    
    Sí, da el mismo resultado. Para realizar la comprobación, tras la ejecución de ambos programas decidimos imprimir por pantalla el contenido de la matriz C que se consigue tras la multiplicación de otras 2. Una vez hecho eso , nos dedicamos a comparar valores concretos de forma aleatoria y todos ellos coincidieron (como máximo fuimos subiendo hasta una precisión de 20 decimales).

* Realiza mediciones de tiempo para 2, 4, 8, 16, 32 y 64 hilos y añade los resultados de tiempo en una tabla junto a los resultados secuenciales. Además añade la ganancia obtenida por cada ejecución en comparación con la secuencial ¿Estos resultados se corresponden o se parecen a los estimados por intel advisor? Justifica tu respuesta.

    | Número de hilos | Tiempo | Ganancia | Ganacia por bucle |
    |--| -- | -- | -- |
    |2|0,0065 segundos|2,06|B1: 1,80 / B2: 1,13 / B3: 1,99|
    |4|0,004 segundos|1,53|B1: 3,09 / B2: 1,38 / B3: 3,95|
    |8|[0,0055 - 0,004] segundos|1,53|B1: 4,05 / B2: 0,97 / B3: 7,86|
    |16|0,006 segundos|1,04|B1: 4,21 / B2: 0,65 / B3: 15,53|
    |32|0,0065 segundos|1,09|B1: 2,08 / B2: 0,26 / B3: 28,65|
    |64|0,007 segundos|1,04|B1: 1,65 / B2: 0,20 / B3: 45,57|
    
    Mientras que el resultado secuencial oscila entre los 0,006 y 0,005 segundos de media. Todos estos resultados se han obtenido con la opción -xCORE-AVX2     de compilación.

