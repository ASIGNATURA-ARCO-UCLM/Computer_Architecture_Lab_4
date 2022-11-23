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
        - **Total Parallel Time:** Especifica el tiempo en segundos que la zona anotada tardaría en ejecutar todas sus instancias de manera paralela
        - **Site Gain:** Predicción de la ganancia máxima de rendimiento ue podría alcanzarse paralelizando todas las instancias de la zona anotada

        Del campo **Site Instance Metrics, Parallel Time**:
        - **Average Serial Time:** ESpecifica el tiempo medio en segundos que una instancia de la zona anotada tardará en ejecutarse.

* Analiza la escalabilidad de la ganancia por cada Site que has declarado:
    * En primer lugar configura el reporte acorde a tu sistema y al modelo de paralelización con hilos que vayas a utilizar.
    * Realiza una captura y almacenala con el nombre task2 en la carpeta [task2](/results/task2)
    * Indica para cada uno de los sites definidos, a partir de qué número de CPUs la ganancia deja de mejorar o incluso empeora, y justifica la razón por la cual ocurre.

        **ESTAS JUSTIFICACIONES SE HAN REALIZADO CON "Avg. Number of Iterations" y "Avg. Iteration Duration" APLICADOS A X1**

        - Bucle1: Parece aplanarse la curva de ganancia de rendimiento al llegar a **64 CPUs**, pero no puede comprobarse debido a que dicho valor es el máximo representado en el eje de abscisas del gráfico. 
        Esto se debe a que a pesar de que se paralelizarían una serie de operaciones cuyos resultados se almacena en diferentes posiciones de una matriz, ellas no son suficientemente complejas, apareceriendo así un leve desbalanceo de carga **(7.3%)** entre los diferentes hilos a crear junto con una pequeña sobrecarga **(8.0%)** por su coordinación.

        - Bucle2: En este caso, a partir de los **16 CPUs**, la ganancia empieza de hecho a decrecer de forma drástica. 
        Esto se debe a que se paralelizaría un bucle que realiza simples asignaciones de los valores de las posiciones de una matriz a otra. El generar hilos que trabajen de forma concurrente sólo acarrearía problemas como lo su la alta sobrecarga de coordinación **(39%)** o su gran desbalanceo **(39.7%)** potencial (si ciertos hilos cuentan con más instrucciones a ejecutar) que podría darse.
        
        - Bucle3: **Ni siquiera llegando a las 64 CPUs** parece reducirse significativamente la inclinación de la curva que determina la ganancia de rendimiento en su ejecución.
        Esto se debe a que ahora sí se paralelizaría un bucle en el que se requeriría de una serie de operaciones que conllevan más tiempo como lo es el acceso y multiplicación de diferentes posicones de matrices, además del registro de los resultados en otra. Estas tareas se completarían realizándose en paralelo mucho antes que en serie y saldría más a cuenta la creación masiva de hilos debido a la baja sobrecarga **(0.2%)** que supondrían y desbalanceo que tendrían **(1.2%)**.
        
       

    * ¿Cuál de los bucles definidos en el código se beneficia más del incremento de CPUs? ¿Cómo afectaría a la ganancia de este Site si, usando el máximo número de CPUs de la simulación, en vez de usar arrays de tamaño 300 lo aumentamos a 37500? Indica cómo has obtenido este nueva ganancia.

        Es el tercer bucle el que más se beneficia del incremento de CPUs. La ganancia, usando el máximo número de CPUs de la simulación con arrays de tamaño 37500 pasaría de 58,33 (con el 8 CPUs y 300 el tamaño de los arrays)a  

        Para llegar a ese dato, lo primero que hay que hacer es cambiar el valor de la constante SIZE de 300 a 37500 y compilarlo de nuevo. Una vez contemos con su ejecutable, lanzaremos la herramienta Intel Advisor para realizar un proyecto en el que lo seleccionemos como archivo fuente. Tras elegir la opción de "threading", se lanzará un análisis marcando la opción Suitability, que nos permitirá acceder al gráfico que representa la ganancia de rendimiento en función del número de CPUs usadas. Por último, simplemente estableceremos la opción "CPU Count" a 64, por ser ésta cantidad la máxima seleccionabe.
