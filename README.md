# 🔢 ALU Lógica con Comparador, Sumador y Display BCD – Logisim

## 📘 Descripción General
Este proyecto implementa una **Unidad Lógica Aritmética (ALU)** básica utilizando **Logisim**, capaz de realizar operaciones entre dos números binarios de 4 bits.  
Además, muestra los resultados en **LEDs o displays de 7 segmentos**, dependiendo de la operación seleccionada.

El diseño utiliza módulos combinacionales conectados mediante **multiplexores**, **comparadores**, y **decodificadores BCD**, simulando el comportamiento de un procesador simple con salidas visuales.

---

## ⚙️ Características del Proyecto

### 🔹 Entradas
- **A[3:0]** → Primer número binario (4 bits)  
- **B[3:0]** → Segundo número binario (4 bits)  
- **Selectores (Switches)** → Determinan la operación a ejecutar

### 🔹 Operaciones Disponibles
| Selector | Operación                  | Salida                        |
|-----------|---------------------------|--------------------------------|
| 00        | OR lógico (A ∨ B)         | LEDs                          |
| 01        | NOT (A) y NOT (B)         | LEDs                          |
| 10        | Comparador (A > B, A = B, A < B) | LEDs de estado              |
| 11        | Suma / Resta (según diseño)     | Displays de 7 segmentos (2 dígitos) |

---

## 💡 Funcionalidad Detallada

1. **Bloque OR:** realiza la operación lógica OR bit a bit entre A y B.  
2. **Bloques NOT:** generan los complementos de A y B.  
3. **Comparador:** determina si A es mayor, igual o menor que B.  
   - Salida `Igual` se activa cuando A == B  
   - Salida `Mayor` se activa cuando A > B  
   - Salida `Menor` se activa cuando A < B  
4. **Multiplexores (MUX):** seleccionan qué bloque se muestra en las salidas dependiendo del selector.  
5. **Bloque Aritmético (Suma/Resta):**
   - Calcula la suma o resta de A y B (5 bits con acarreo).
   - El resultado se convierte a **decimal BCD** y se muestra en dos **displays de 7 segmentos** (decenas y unidades).
6. **Selector de Salida:**
   - Permite elegir entre mostrar el resultado en **LEDs** (operaciones lógicas o comparador)  
     o en **displays** (operaciones aritméticas).

---

## 🧩 Componentes Principales en Logisim

- **Comparadores de 4 bits**
- **Sumador de 4+1 bits (con Carry Out)**
- **Puertas AND, OR, NOT**
- **Multiplexores (MUX 2:1 y 4:1)**
- **Decodificadores BCD a 7 segmentos**
- **Displays de 7 segmentos**
- **Switches y LEDs de salida**

---

## 🧠 Lógica de Conversión a BCD (para suma/resta)
El resultado binario (5 bits) se convierte en dos dígitos decimales:
- **Decenas:** obtenidas a partir de comparaciones (`>=10`, `>=20`, `>=30`)
- **Unidades:** mediante restas (`S-10`, `S-20`, `S-30`) seleccionadas con MUX

Esto permite representar correctamente valores del 0 al 30 en **dos displays**.

---

## 🧪 Pruebas Recomendadas
| A (bin) | B (bin) | Operación | Resultado esperado | Visualización |
|----------|----------|------------|--------------------|---------------|
| 0101 (5) | 0011 (3) | A > B      | Mayor = 1          | LED           |
| 0011 (3) | 0011 (3) | A = B      | Igual = 1          | LED           |
| 0100 (4) | 0110 (6) | A < B      | Menor = 1          | LED           |
| 0110 (6) | 0101 (5) | Suma       | 11 → "1" "1"       | Display BCD   |

---

## 🧰 Herramientas Utilizadas
- **Software:** Logisim Evolution  
- **Lenguaje:** Diseño digital (lógica combinacional)  
- **Archivo principal:** `ALU_CIRCUITO.circ`

---

## 🚀 Cómo Ejecutar
1. Abre Logisim Evolution.  
2. Carga el archivo `.circ` incluido (`Archivo → Abrir`).
3. Abrir el modulo principal (ALU_22)
4. Selecciona la operación deseada con el **switch selector**.  
5. Observa el resultado en los **LEDs o displays** según corresponda.

---

## 📄 Estructura del Repositorio
📁 ALU_CIRCUITO/
├── ALU_CIRCUITO.circ # Circuito principal de Logisim
├── README.md # Este archivo
