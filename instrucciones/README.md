# Instrucciones en Assembly 8086

## ¿Qué es una Instrucción?

Una **instrucción** es un comando que la CPU puede ejecutar. Cada instrucción en ensamblador se traduce en una operación básica, como mover datos, realizar cálculos o controlar el flujo de ejecución. En la arquitectura 8086, las instrucciones operan sobre registros y memoria, representándose como secuencias de bytes en la memoria.

---

## Ciclo de Vida de una Instrucción

El ciclo de vida de una instrucción describe cómo la CPU procesa cada instrucción y generalmente consta de las siguientes fases:

1. **Búsqueda (Fetch):** La CPU lee la instrucción desde la memoria.  
2. **Decodificación (Decode):** La CPU interpreta la instrucción y determina la operación a realizar.  
3. **Ejecución (Execute):** Se realiza la operación especificada por la instrucción.  
4. **Acceso a Memoria (Memory Access):** Si es necesario, se leen o escriben datos en memoria.  
5. **Escritura de Resultados (Write-back):** Los resultados se almacenan en los registros o en memoria.  

Este ciclo se repite continuamente durante la ejecución del programa.

---

## CISC vs RISC

- **CISC (Complex Instruction Set Computing):** Arquitectura con instrucciones complejas que pueden realizar múltiples operaciones en un solo ciclo de reloj. La 8086 es un ejemplo de arquitectura CISC.  
- **RISC (Reduced Instruction Set Computing):** Arquitectura con instrucciones simples que generalmente requieren un número constante de ciclos para ejecutarse. Cada instrucción realiza una única operación, pero se necesitan más instrucciones para tareas complejas.

---

## Microcódigo

El **microcódigo** descompone las instrucciones de alto nivel en microoperaciones que la CPU puede ejecutar. En arquitecturas CISC como la 8086, el microcódigo permite que instrucciones complejas se traduzcan en operaciones elementales dentro de los ciclos de reloj.

---

## Traductores del Lenguaje

Los **traductores** convierten código fuente en un formato que la CPU puede ejecutar:

- **Ensambladores (Assembler):** Transforman código en ensamblador a código de máquina ejecutable. Ejemplo: **MASM (Microsoft Macro Assembler)**.

---

## Fuente y Destino

En las instrucciones de ensamblador:

- **Fuente:** Valor que se va a operar.  
- **Destino:** Registro o memoria donde se almacenará el resultado.  

Las instrucciones operan tomando el valor de la fuente y almacenando el resultado en el destino.

---

## Modificación de Banderas

Al ejecutar instrucciones, las **banderas** del procesador pueden cambiar. Estas reflejan el resultado de operaciones y controlan el flujo del programa. Ejemplos: **Carry Flag**, **Zero Flag**, **Overflow Flag**.

---

## Tipos de Instrucciones en Assembly 8086

### 1. Instrucciones de Datos

Permiten mover, cargar, almacenar y manipular datos en registros o memoria:

- **MOV:** Mueve datos de la fuente al destino.  
- **PUSH / POP:** Colocan o extraen valores de la pila.

---

### 2. Instrucciones de Control de Flujo

Alteran el orden de ejecución de las instrucciones, permitiendo bucles, saltos y decisiones:

- **JMP:** Salto incondicional.  
- **JE / JZ:** Salto si los valores comparados son iguales.  
- **JNE / JNZ:** Salto si los valores comparados son diferentes.

---

### 3. Instrucciones Aritméticas

Realizan operaciones matemáticas con registros o memoria:

- **ADD:** Suma.  
- **SUB:** Resta, usando el complemento a 2 en la arquitectura 8086.  
- **MUL:** Multiplicación, afectando registros específicos según el tamaño del operando.  
- **DIV:** División, generando cociente y residuo en registros específicos, con manejo de división por cero y tamaño de los resultados.

---

### 4. Instrucciones Lógicas

Operan a nivel de bits, permitiendo manipulación mediante **mascaras**:

- **AND / OR / XOR / NOT**: Operaciones básicas a nivel de bits.  

#### Uso de Mascaras

- **Activación de bits:** Establece bits específicos en 1.  
- **Desactivación de bits:** Establece bits específicos en 0.  
- **Conmutación de bits:** Cambia el estado de bits de 0 a 1 o de 1 a 0.  
- **Prueba de bits:** Verifica el estado de bits específicos.

---

### 5. Instrucciones de Comparación

Permiten comparar valores y actualizar banderas de la CPU:

- **CMP:** Compara dos valores y ajusta las banderas.  
- **TEST:** Operación AND que solo afecta las banderas, sin almacenar resultados.

---

### 6. Instrucciones de Entrada y Salida

Permiten la comunicación con dispositivos periféricos mediante puertos:

- **IN:** Lee datos desde un puerto de entrada.  
- **OUT:** Escribe datos a un puerto de salida.
