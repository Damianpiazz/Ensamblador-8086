# Saltos y Control de Flujo en Assembly 8086

En Assembly, los **saltos** permiten modificar el flujo de ejecución de un programa. Dependiendo de la lógica del programa, los saltos pueden ser **incondicionales**, que siempre redirigen el flujo, o **condicionales**, que dependen del resultado de operaciones previas.

---

## Cálculo de la Dirección de Salto

El destino de un salto se determina mediante un **desplazamiento** relativo a la instrucción siguiente a la instrucción de salto. Este desplazamiento puede ser positivo o negativo y se suele expresar en formato hexadecimal.

- **Salto hacia adelante:** Desplazamiento positivo, que indica que la ejecución debe continuar en instrucciones posteriores.  
- **Salto hacia atrás:** Desplazamiento negativo, que indica que la ejecución debe regresar a instrucciones anteriores. Los valores negativos se representan en **complemento a dos** en hexadecimal.

---

## Tipos de Saltos

### 1. Salto Incondicional

- **JMP:** Redirige la ejecución a otra instrucción sin evaluar ninguna condición.  
- Útil para cambios de flujo de control que deben ocurrir siempre, como saltar a subrutinas o reinicios de bucles.

### 2. Saltos Condicionales

Estas instrucciones modifican el flujo únicamente si se cumple una condición específica evaluada por las banderas del procesador:

| Instrucción | Condición de salto |
|------------|------------------|
| **JE / JZ**  | Salta si los operandos son iguales o el resultado de la comparación es cero |
| **JNE / JNZ** | Salta si los operandos no son iguales o el resultado no es cero |
| **JG / JNLE** | Salta si el primer operando es mayor que el segundo |
| **JL / JNGE** | Salta si el primer operando es menor que el segundo |

### 3. Bucle

- **LOOP:** Decrementa automáticamente el registro de contador (`CX`) y salta a una dirección especificada si `CX` no ha llegado a cero.  
- Es útil para iteraciones controladas por un número fijo de repeticiones.

---

## Resumen del Flujo de Saltos

- **Desplazamiento positivo:** indica un salto hacia adelante.  
- **Desplazamiento negativo:** indica un salto hacia atrás, representado en complemento a dos en hexadecimal.  
- **Incondicional:** siempre redirige el flujo.  
- **Condicional:** depende del estado de las banderas del procesador.  
- **Bucle:** combina decrementar un contador con un salto condicional según el valor del contador.