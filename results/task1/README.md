# Tarea 1: Intel Advisor

## Preguntas
* Antes de comenzar a realizar ningún análisis es interesante conocer las características de tu arquitectura, para ello contesta a las siguientes preguntas:
    * Indica tu modelo de procesador y de cuantos núcleos dispones
    
            Enrique: Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz | 8 cores disponibles
            Pedro: Intel(R) Core(TM) i7-10750H CPU @ 2.60GHz | 12 cores disponibles
    * ¿Cuantos hilos pueden ser ejecutados por núcleo?
    
            Enrique: 2 hilos pueden ejecutarse por core
            Pedro: 2 hilos pueden ejecutarse por core

* A continuación procede a realizar anotaciones en todos los bucles que deben ser paralelizados (señalados con un TODO: Paralellize). En total debes indicar tres Sites para analizar. Estas anotaciones permitirán al programa de análisis considerar que esos bucles serán paralelizados y hacer las estimaciones oportunas. Guarda el nuevo programa con las anotaciones con el nombre matmul_annotated.cpp (ten en cuenta que además de añadir las anotaciones tienes que incluir un nuevo archivo de cabecera).

* Indica el comando que usarías para compilar el programa con las anotaciones (Consejos: Mirar la opción -I y buscad la ruta del archivo advisor-annotate.h dentro del directorio intel/oneapi).
        g++ -g -openmp matmul_annotated.cpp -lm -o ejecutable -I ~/intel/oneapi/advisor/2022.3.0/include -lgomp -ldl
