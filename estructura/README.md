# Segmentación en la Arquitectura de Memoria

## Descripción de la Segmentación

La **segmentación** es una técnica de gestión de memoria que divide la memoria en **segmentos lógicos de tamaño variable**. A diferencia de la paginación, que utiliza bloques de tamaño fijo, la segmentación permite que cada segmento tenga un tamaño ajustado al tipo de datos o código que contiene.

Esta técnica facilita una organización más flexible de la memoria, permitiendo que un segmento almacene diferentes tipos de información, como código ejecutable, datos o pilas, según las necesidades del programa.

---

## Tabla de Segmentos

La **tabla de segmentos** es un componente clave que almacena información sobre cada segmento, incluyendo:

- **Dirección base:** Inicio del segmento en memoria física.  
- **Límite:** Tamaño del segmento.  

Esta tabla permite al procesador traducir **direcciones lógicas** (usadas por el programa) a **direcciones físicas** (en la memoria real).

---

## Fragmentación

La segmentación puede sufrir **fragmentación**, que afecta la eficiencia del uso de memoria:

1. **Fragmentación externa:** Espacios libres en la memoria demasiado pequeños para contener un segmento completo, generando desperdicio de memoria.  
2. **Fragmentación interna:** Ocurre cuando un segmento es más grande de lo necesario, dejando espacio sin usar dentro del mismo.  

En general, la segmentación es más propensa a **fragmentación externa**.

---

## Punto de Vista del Usuario

La segmentación ofrece varias ventajas para los usuarios y programadores:

- **Flexibilidad:** Permite dividir programas en bloques lógicos de tamaño variable.  
- **Protección y aislamiento:** Cada segmento puede ser protegido, evitando que un error afecte a otros segmentos.  
- **Facilidad de programación:** Los programadores pueden organizar el código, los datos y la pila de manera modular.  

El principal inconveniente es la fragmentación, que puede reducir la eficiencia de la memoria y afectar el rendimiento del sistema.

---

## Paradigma de la Segmentación

La segmentación sigue el **paradigma estructurado**, que organiza los programas en bloques o módulos lógicos. Cada segmento puede contener un tipo específico de información, como código o datos, lo que facilita la modularidad y el mantenimiento del programa. La segmentación refleja la estructura lógica del programa en la memoria y permite una administración más eficiente de los recursos.

---

# Estructura de un Programa en Assembly 8086

En la arquitectura 8086, la memoria se organiza en **segmentos de hasta 64 KB**, accesibles mediante **registros de segmento**. Esta estructura permite separar y proteger código, datos y pila.

## Registros de Segmento

Los cuatro registros principales son:

1. **Code Segment (CS):** Contiene la dirección base del segmento de código ejecutable.  
   Se combina con el puntero de instrucción (IP) para determinar la dirección de la instrucción a ejecutar.

2. **Data Segment (DS):** Contiene la dirección base del segmento de datos, donde se almacenan variables y datos estáticos.  

3. **Extra Segment (ES):** Segmento adicional utilizado para operaciones especiales y transferencias de datos.  

4. **Stack Segment (SS):** Contiene la dirección base del segmento de pila, utilizado para almacenamiento temporal y llamadas a subrutinas. El puntero de pila (SP) indica el desplazamiento dentro de este segmento.

---

Esta organización segmentada permite:

- Acceso controlado y seguro a la memoria.  
- Separación lógica de código, datos y pila.  
- Facilitar operaciones de programación modular y estructurada.