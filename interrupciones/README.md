# Interrupciones en Assembly 8086

Las **interrupciones** son mecanismos que permiten al procesador interrumpir su flujo de ejecución normal para atender solicitudes especiales, como la entrada/salida de datos o la gestión de errores. Este mecanismo asegura que eventos críticos sean atendidos de manera inmediata, manteniendo la eficiencia y estabilidad del sistema.

---

## Tipos de Interrupciones

### 1. Interrupciones de Software

- Generadas por instrucciones del programa para solicitar servicios específicos del sistema operativo.  
- Permiten acceder a funciones críticas como operaciones de entrada/salida, gestión de archivos, o control de recursos del sistema.  
- Facilitan la comunicación entre aplicaciones y el sistema operativo, abstraiendo los detalles del hardware.

### 2. Interrupciones de Hardware

- Provienen de dispositivos externos, como teclados, temporizadores o controladores de disco.  
- Permiten al procesador responder a eventos asíncronos sin necesidad de que la CPU consulte constantemente el estado del dispositivo.  

---

## Tabla de Vectores de Interrupción

El 8086 utiliza una **tabla de vectores de interrupción**, donde cada vector contiene la dirección de memoria de la rutina encargada de atender una interrupción específica.  

- Cada vector corresponde a un tipo de interrupción.  
- Cuando se genera una interrupción, el procesador consulta esta tabla para determinar qué rutina ejecutar.  
- La rutina de interrupción se encarga de atender el evento y, al finalizar, el procesador retoma la ejecución normal, restaurando el contexto previo.

---

## Proceso de Manejo de Interrupciones

1. **Identificación:** El procesador determina el tipo de interrupción y localiza la dirección de la rutina correspondiente en la tabla de vectores.  
2. **Salvado del contexto:** Se guardan los registros y el contador de programa para preservar el estado actual de ejecución.  
3. **Ejecución de la rutina de interrupción:** Se atiende la solicitud del sistema o dispositivo.  
4. **Restauración del contexto:** Una vez completada la rutina, la CPU retorna al flujo de ejecución original.

---

## Secuencia de Interrupciones en Software

1. Se carga el número de la interrupción en un registro específico, que identifica la rutina a ejecutar.  
2. Se genera la interrupción mediante la instrucción de software correspondiente (`INT`).  
3. La CPU guarda su contexto y transfiere el control a la rutina de interrupción.  
4. Tras ejecutar la rutina, la CPU restaura el contexto y retoma la ejecución normal del programa.

---

## Interrupciones Comunes del 8086

| Interrupción | Función Principal |
|--------------|-----------------|
| **INT 21h**  | Servicios del sistema operativo: manejo de archivos, E/S, control de dispositivos, gestión de memoria y funciones de consola. |
| **INT 10h**  | Funciones de video: cambio de modo gráfico, manipulación del cursor, lectura/escritura de texto y control de paleta de colores. |
| **INT 13h**  | Acceso a discos: lectura/escritura de sectores, formateo, detección de unidades y manejo del almacenamiento. |
| **INT 14h**  | Comunicación serie: lectura/escritura de datos en puertos COM, configuración de velocidad y manejo de errores de comunicación. |
| **INT 0Dh**  | División por cero: activa la rutina de manejo de errores matemáticos al ocurrir una división inválida. |
| **INT 08h**  | Temporizador del sistema: genera interrupciones periódicas para tareas de temporización y sincronización del sistema. |
| **INT 09h**  | Teclado: lectura de pulsaciones, incluyendo teclas especiales como Shift, Ctrl, Alt y teclas de función. |
| **INT 04h**  | Desbordamiento de pila: activa la rutina de manejo de errores cuando la pila excede su capacidad. |
| **INT 0Ah**  | Desbordamiento de BCD: ocurre cuando un valor en formato BCD excede el rango permitido por el procesador. |
| **INT 1Bh**  | Control de puertos paralelos: gestión de comunicación con impresoras y otros dispositivos conectados a puertos paralelos. |

---

## Resumen

Las interrupciones son esenciales para:

- Permitir que la CPU responda a eventos críticos sin perder eficiencia.  
- Facilitar la comunicación entre hardware, software y sistema operativo.  
- Gestionar errores y excepciones de manera controlada.  
- Implementar servicios del sistema operativo de manera organizada y modular.  

En el 8086, tanto interrupciones de hardware como de software son gestionadas a través de vectores de interrupción y rutinas específicas, asegurando un flujo de ejecución seguro y eficiente.