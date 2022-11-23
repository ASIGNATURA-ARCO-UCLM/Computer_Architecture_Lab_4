# Tarea 2: Análisis de Threading
## Preguntas

* Procede a realizar el análisis de threading hasta el análisis **Suitability**

* Antes de comenzar a interpretar los resultados es importante saber la información representada. Ve a la pestaña Suitability Report y responde a las siguientes preguntas:
    * ¿Qué representa el gráfico Scalability of Maximum Site Gain? ¿Para que sirven las opciones Avg. Number of Iterations y Avg. Iteration Duration?
        **El gráfico Scalability of Maximum Site Gain** representa en el eje de las X el número de cores usados (y por tanto de hilos generados); mientras que en el eje de las Y se describe la ganancia en términos de velocidad de ejecución del programa usando dicho número de cores (podría incluso decirte enalgunos casos a partir de qué cantidad se empieza a perder tiempo por tener que coordinar tantos hilos a la vez).

        **Avg. Number of Iterations** permite seleccionar la cantidad media de veces (instancias) que se ejecutarán las zonas anotadas como "tasks" para cada iteración del bucle del que se sacan las estadísticas.

        **Avg. Iteration Duration** permite seleccionar la duración media de ejecución de las zonas anotadas como "tasks" para cada iteración del bucle del que se sacan las estadísticas.



    * Explica que significa cada campo de las columnas **Combined Site Metrics, All Instances** y **Site Instance Metrics, Parallel Time**
        Del campo **Combined Site Metrics, All Instances**:
        - **Total Serial Time:** Especifica el tiempo en segundos que la zona anotada tardaría en ejecutar todas sus instancias de manera secuencial
        - **Total Parallel Time:**Especifica el tiempo en segundos que la zona anotada tardaría en ejecutar todas sus instancias de manera paralela
        - **Site Gain:**Predicción de la ganancia máxima de rendimiento ue podría alcanzarse paralelizando todas las instancias de la zona anotada

        Del campo **Site Instance Metrics, Parallel Time**:
        - **Average Serial Time:**ESpecifica el tiempo medio en segundos que una instancia de la zona anotada tardará en ejecutarse.

* Analiza la escalabilidad de la ganancia por cada Site que has declarado:
    * En primer lugar configura el reporte acorde a tu sistema y al modelo de paralelización con hilos que vayas a utilizar.
    * Realiza una captura y almacenala con el nombre task2 en la carpeta [task2](/results/task2)
    * Indica para cada uno de los sites definidos, a partir de qué número de CPUs la ganancia deja de mejorar o incluso empeora, y justifica la razón por la cual ocurre.

        **ESTAS JUSTIFICACIONES SE HAN REALIZADO CON "Avg. Number of Iterations" y "Avg. Iteration Duration" APLICADOS A X1**

        - Bucle1: Ni siquiera llegando a las 64 CPUs parece reducirse significativamente la inclinación de la curva que determina la ganancia de rendimiento en su ejecución.

        - Bucle2: 
        
        - Bucle3: Parece aplanarse la curva de ganancia de rendimiento al llegar a 64 CPUs, pero no puede comprobarse debido a que dicho valor es el máximo representado en el eje de abscisas del gráfico. 
        
       

    * ¿Cuál de los bucles definidos en el código se beneficia más del incremento de CPUs? ¿Cómo afectaría a la ganancia de este Site si, usando el máximo número de CPUs de la simulación, en vez de usar arrays de tamaño 300 lo aumentamos a 37500? Indica cómo has obtenido este nueva ganancia.