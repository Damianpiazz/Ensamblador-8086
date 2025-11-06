# Uso de Cadenas en Assembly 8086

En la arquitectura 8086, las **cadenas de caracteres** se representan como secuencias de bytes en memoria, donde cada carácter está codificado en **ASCII**. La CPU cuenta con instrucciones especiales para manipular estas cadenas de manera eficiente, utilizando registros de índice (`SI`, `DI`) y la **bandera de dirección (DF)**.

---

## Instrucciones Principales para Cadenas

### 1. MOVSB (Move String Byte)
Copia un **byte** de memoria desde la dirección apuntada por `SI` a la dirección apuntada por `DI`.  
- Ajuste automático de `SI` y `DI` según la **bandera DF**:  
  - `DF = 0` → incrementa los registros.  
  - `DF = 1` → decrementa los registros.

### 2. MOVSW (Move String Word)
Similar a `MOVSB`, pero mueve una **palabra (2 bytes)** de memoria.  
- Ajuste automático de `SI` y `DI` según `DF`.

### 3. LODSB (Load String Byte)
Carga un **byte** desde la dirección apuntada por `SI` al registro `AL`.  
- `SI` se ajusta automáticamente según la bandera `DF`.

### 4. LODSW (Load String Word)
Carga una **palabra (2 bytes)** desde la dirección apuntada por `SI` al registro `AX`.  
- Ajuste automático de `SI` según `DF`.

### 5. STOSB (Store String Byte)
Almacena el valor del registro `AL` en la dirección apuntada por `DI`.  
- `DI` se ajusta automáticamente según `DF`.

### 6. STOSW (Store String Word)
Almacena el valor del registro `AX` (2 bytes) en la dirección apuntada por `DI`.  
- Ajuste automático de `DI` según `DF`.

### 7. SCASB (Scan String Byte)
Compara un **byte** en `AL` con un byte en la dirección apuntada por `DI`.  
- Actualiza las **banderas de estado** de la CPU.  
- `DI` se ajusta automáticamente según `DF`.  
- Se utiliza para **buscar caracteres** dentro de cadenas.

### 8. SCASW (Scan String Word)
Compara una **palabra** en `AX` con la palabra en la dirección apuntada por `DI`.  
- Ajuste automático de `DI` según `DF`.  
- Afecta las banderas de estado.

### 9. CMPSB (Compare String Byte)
Compara un **byte** en la dirección apuntada por `SI` con un byte en la dirección apuntada por `DI`.  
- Ajusta automáticamente `SI` y `DI` según `DF`.  
- Actualiza las banderas de estado para reflejar el resultado de la comparación.

### 10. CMPSW (Compare String Word)
Compara una **palabra** en la dirección apuntada por `SI` con una palabra en la dirección apuntada por `DI`.  
- Ajuste automático de `SI` y `DI` según `DF`.  
- Afecta las banderas de estado.

---

## Notas Adicionales
- La **bandera DF (Direction Flag)** determina la dirección en la que avanzan los registros de índice (`SI` y `DI`).  
- Estas instrucciones permiten manipular cadenas de manera eficiente, ideal para copiar, comparar, buscar o procesar secuencias de bytes en memoria.  
- La combinación de estas instrucciones con bucles y condiciones permite implementar operaciones complejas sobre cadenas sin necesidad de múltiples instrucciones manuales.