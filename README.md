# Ensamblador-8086

Repositorio dedicado a la materia **Arquitectura de Computadoras** (UTN), enfocado en la programación en **ensamblador 8086** y la comprensión de la arquitectura de la CPU a nivel de hardware.

El lenguaje ensamblador convierte código simbólico en **código máquina**, permitiendo un control completo sobre la CPU, memoria y dispositivos de Entrada/Salida (E/S). Programar en ensamblador es **imperativo y orientado a la arquitectura**, dando al programador control total sobre el flujo de ejecución.

---

## 1. Arquitectura CISC y Microprogramación del 8086

El procesador **Intel 8086/8088** pertenece a la arquitectura **CISC (Complex Instruction Set Computer)**.

### Características CISC

- **Conjunto de instrucciones amplio y complejo:** Permite operaciones directas entre memoria y registros.  
- **Instrucciones de tamaño variable:** Pueden ir de 2 a 5 bytes, según los operandos.  
- **Manipulación directa de memoria:** Soporta operaciones directamente sobre datos en memoria.  
- **Ciclos de instrucción variables:** Cada instrucción puede requerir múltiples ciclos de reloj.  

### Unidad de Control Microprogramada

- **Microcódigo:** Secuencia de microoperaciones que ejecuta instrucciones complejas.  
- **Ubicación:** Almacenado en ROM interna del procesador.  
- **Eficiencia:** Determina la cantidad de operaciones necesarias por instrucción, afectando la velocidad de ejecución.  

---

## 2. Estructura Interna del Procesador

El 8086 coordina sus funciones mediante tres unidades esenciales:

| Unidad | Función Principal | Detalles |
|--------|-----------------|---------|
| **BIU (Bus Interface Unit)** | Acceso a memoria y E/S | Maneja buses de direcciones, datos y control. Mantiene cola FIFO de instrucciones. |
| **ALU (Arithmetic-Logic Unit)** | Operaciones aritméticas y lógicas | Realiza sumas, restas, multiplicaciones, divisiones y operaciones lógicas. Utiliza registros de almacenamiento temporal. |
| **EU (Execution Unit)** | Ejecución y decodificación de instrucciones | Controla el IP, decodifica instrucciones y proporciona direcciones lógicas a la BIU. |

### Ciclo de instrucción

1. Cálculo de la dirección de la instrucción (IAC)  
2. Captación de la instrucción (Fetch)  
3. Decodificación (IOD)  
4. Captación y cálculo del operando (OAC/OF)  
5. Ejecución de la operación sobre los datos (DO)  
6. Almacenamiento del resultado (Operand Store)  

---

## 3. Registros Internos y Gestión de Memoria

### Segmentación de Memoria

- Dirección lógica: Segmento + Desplazamiento (Offset)  
- Dirección física: `(Segmento × 16) + Desplazamiento`  
- Espacio de memoria total: 1 MB, dividido en segmentos de 64 KB  
- Operación típica: Modo real (MS-DOS)

**Ejemplo:**

- Segmento: 0x1234  
- Desplazamiento: 0x5678  
- Dirección Física: `(0x1234 × 16) + 0x5678 = 0x12340 + 0x5678 = 0x179B8`

### Características de la Segmentación

- Cada segmento puede contener hasta **64 KB**.  
- Los registros de segmento (**CS, DS, SS, ES**) definen la ubicación base de un segmento.  
- Se pueden usar registros como **SI** y **DI** para especificar desplazamientos dentro del segmento.  

### Lectura del Hexadecimal

El sistema hexadecimal utiliza 16 símbolos: `0-9` y `A-F`.  
Cada dígito hexadecimal representa 4 bits (un nibble).  

| Sistema | Valor |
|---------|-------|
| Decimal | 255   |
| Binario | 11111111 |
| Hexadecimal | 0xFF |

En el 8086, las direcciones y valores suelen expresarse en hexadecimal para simplificar la representación de datos binarios.

### Registros de Segmento

| Registro | Uso |
|----------|-----|
| **CS**  | Code Segment: ubicación del código ejecutable |
| **SS**  | Stack Segment: operaciones con la pila |
| **DS**  | Data Segment: direccionamiento de datos |
| **ES**  | Extra Segment: apuntador auxiliar |

### Registros de Uso General

| Registro | Subregistros | Función |
|----------|--------------|---------|
| **AX**  | AH, AL       | Acumulador, operaciones de E/S, multiplicación/división |
| **BX**  | BH, BL       | Base, direccionamiento de memoria |
| **CX**  | CH, CL       | Contador de bucles y operaciones de cadena |
| **DX**  | DH, DL       | Datos y puerto de E/S, multiplicación/división junto con AX |

### Registros Puntero e Índice

| Registro | Función |
|----------|---------|
| **SP**  | Stack Pointer, asociado con SS |
| **BP**  | Base Pointer, usado como auxiliar y en direccionamiento de memoria |
| **SI**  | Source Index, asociado con DS, operaciones con cadenas |
| **DI**  | Destination Index, asociado con ES, operaciones con cadenas |

### Registro de Control y Estado (Flags)

| Bandera | Función |
|---------|---------|
| **CF** | Acarreo (Carry) |
| **ZF** | Cero (Zero) |
| **SF** | Signo (Sign) |
| **IF** | Interrupciones habilitadas/deshabilitadas |
| **OF** | Overflow / desbordamiento |

### Modos de Direccionamiento

1. **Inmediato:** El dato está en la instrucción  
2. **Registro Directo:** Operando en un registro  
3. **Directo:** Dirección de memoria especificada  
4. **Registro Indirecto:** Registro contiene la dirección del operando  
5. **Relativo a la Base:** Registro base + desplazamiento  
6. **Relativo a Índice:** Registro índice + desplazamiento  
7. **Indexado a la Base:** Registro base + índice + desplazamiento  

---

## 4. Juego de Instrucciones

### Manipulación de Datos

- **Transferencia:** MOV  
- **Aritméticas:** ADD, ADC, MUL  
- **Lógicas:** OR, XOR, AND, NOT  
- **Comparación:** CMP, TEST  

### Control de Flujo

- **Saltos incondicionales:** JMP  
- **Saltos condicionales:** Jnnn  
- **Bucles:** LOOP (usa CX como contador)  

---

## 5. Administración de Entrada/Salida (E/S) e Interrupciones

### Interrupciones

- Evento que altera el flujo de ejecución normal.  
- Tipos:
  - **Externas (Hardware)**  
  - **Internas (Excepciones)**  
  - **Simuladas (Software)**  
- **Vectores de interrupción:** Dirección CS:IP de la rutina de servicio (ISR)  
- **Servicios DOS/BIOS:** INT 21H, INT 10H

### Métodos de Transferencia E/S

1. **Pooling (Encuesta):** CPU verifica estado del dispositivo periódicamente  
2. **Por interrupciones:** CPU responde solo cuando el dispositivo lo solicita  
3. **DMA (Acceso Directo a Memoria):** Transferencia directa entre periférico y memoria, liberando la CPU  

---

## 6. Entorno de Ejecución y Sistemas Operativos

- El ensamblador se ejecuta generalmente sobre un **sistema operativo**, como MS-DOS.  
- **Sistema operativo:** Coordina recursos, administra memoria y procesos.  
- **Proceso:** Programa en ejecución con registros y variables activas.  
- **Gestión de memoria:** Asigna espacio lógico a cada proceso y protege la memoria de accesos indebidos.  

---

## 7. Segmentación y Direccionamiento

- Cada segmento de memoria: 64 KB  
- Direcciones físicas se calculan combinando **Segmento + Offset**