# Modularización de Programas con las Instrucciones CALL y RET en Assembly 8086

En el **8086**, la modularización de programas se logra mediante subrutinas y funciones, que permiten organizar el código en bloques independientes y reutilizables. Las instrucciones clave para esta modularización son **CALL** y **RET**.

---

## CALL

La instrucción **CALL** se utiliza para realizar una **llamada a una subrutina**.  

Cuando se ejecuta un CALL, el procesador realiza los siguientes pasos:

1. **Empuja la dirección de retorno** en la pila. Esta dirección corresponde a la instrucción que sigue a la llamada, garantizando que la ejecución pueda continuar correctamente tras finalizar la subrutina.  
2. **Cambia el flujo de control** al inicio de la subrutina, comenzando la ejecución del bloque de código llamado.

Esta instrucción permite que los programas se dividan en módulos, mejorando la organización y la reutilización del código.

---

## RET

La instrucción **RET** se utiliza para **regresar de una subrutina** al punto del programa donde se realizó la llamada.  

Al ejecutarse RET, el procesador:

1. **Extrae la dirección de retorno** desde la pila, la cual fue previamente guardada por la instrucción CALL.  
2. **Ajusta el puntero de instrucción (IP)** a la dirección extraída, retomando la ejecución del programa justo después de la llamada.

Si la subrutina recibe parámetros a través de la pila, RET puede incluir un valor que indica el número de bytes que deben eliminarse de la pila al finalizar, asegurando que la pila quede correctamente balanceada.

---

## Resumen del flujo de ejecución

| Instrucción | Acción principal |
|------------|-----------------|
| **CALL**  | Empuja la dirección de retorno en la pila y transfiere el control al inicio de la subrutina. |
| **RET**   | Extrae la dirección de retorno desde la pila y regresa la ejecución al punto posterior a la llamada. |

---

### Beneficios de la modularización

- **Reutilización de código:** Subrutinas pueden llamarse desde distintos puntos del programa.  
- **Organización del programa:** Permite dividir el código en bloques más manejables y comprensibles.  
- **Mantenimiento más sencillo:** Cambios en la subrutina se reflejan automáticamente en todas las llamadas.  
- **Optimización de la pila:** La pila mantiene temporalmente direcciones y parámetros, asegurando un flujo de ejecución controlado y seguro.
