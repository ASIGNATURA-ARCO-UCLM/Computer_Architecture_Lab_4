# Tarea 2: Análisis de Threading
## Preguntas

* Procede a realizar el análisis de threading hasta el análisis **Suitability**

* Antes de comenzar a interpretar los resultados es importante saber la información representada. Ve a la pestaña Suitability Report y responde a las siguientes preguntas:
    * ¿Qué representa el gráfico Scalability of Maximum Site Gain? ¿Para que sirven las opciones Avg. Number of Iterations y Avg. Iteration Duration?
    * Explica que significa cada campo de las columnas **Combined Site Metrics, All Instances** y **Site Instance Metrics, Parallel Time**

* Analiza la escalabilidad de la ganancia por cada Site que has declarado:
    * En primer lugar configura el reporte acorde a tu sistema y al modelo de paralelización con hilos que vayas a utilizar.
    * Realiza una captura y almacenala con el nombre task2 en la carpeta [task2](/results/task2)
    * Indica para cada uno de los sites definidos, a partir de qué número de CPUs la ganancia deja de mejorar o incluso empeora, y justifica la razón por la cual ocurre.
    * ¿Cuál de los bucles definidos en el código se beneficia más del incremento de CPUs? ¿Cómo afectaría a la ganancia de este Site si, usando el máximo número de CPUs de la simulación, en vez de usar arrays de tamaño 300 lo aumentamos a 37500? Indica cómo has obtenido este nueva ganancia.