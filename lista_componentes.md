# Lista de Componentes para el Proyecto AM

## 1. Etapa de Transmisión

*   **Preamplificador de Audio:**
    *   **Opción principal:** **LM358** o TL072.
    *   *Alternativa:* Transistores 2N3904 o 2N2222.
*   **Oscilador de Portadora (RF):**
    *   **Opción principal:** **Cristal de Cuarzo de 20 MHz** y **transistor 2N2222**.
*   **Modulador (Multiplicador):**
    *   **Opción principal:** **CA3080.**
    *   *Alternativas:* AD633, MC1496 o LM1496.

## 2. Etapa de Recepción

*   **Diodo Detector (Detector de Envolvente):**
    *   **Opción principal:** 1N34A (Germanio) o 1N5711, BAT41, **1N5819** (Schottky).
    *   *Alternativa:* 1N4148 (Silicio - menos recomendado por su mayor caída de voltaje).
*   **Filtro Pasa-Bajos (RC):**
    *   **Componentes necesarios:** Potenciómetro (ej.**10 kΩ o 100 kΩ** ) y capacitores (**1 nF, 10 nF, 100 nF**).
*   **Amplificador de Audio Final:**
    *   **Opción principal:** **LM386.**

**Nota:** Vamos a utilizar un micrófono electret y una bocina/parlante (8 Ω) para el proyecto.



| # | Componente / Material | Valor o Referencia | Cantidad | Estado actual / Observación |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Protoboard | 1 larga (60 pines / 830 puntos) | 1 | ¡Lo tienes! (Suficiente para todo el sistema) |
| **2** | Micrófono | Electret con cables (rojo/negro)[cite: 17] | 1 | ¡Lo tienes! |
| **3** | Preamplificador | IC **LM358P** (8 pines)[cite: 18] | 2 | ¡Los tienes! |
| **4** | Modulador AM | IC **CA3080E** (8 pines)[cite: 20, 26] | 1 | ¡Lo tienes! |
| **5** | Amplificador Audio | IC **LM386N-1** (8 pines) + Parlante[cite: 16] | 1 | ¡Lo tienes! |
| **6** | Oscilador RF | Transistor **2N2222A** + Cristal de **20 MHz**[cite: 12, 19] | 2 / 1 | ¡Lo tienes! |
| **7** | Diodo Detector | Germanio (1N34A) o Schottky (1N5819) | 1 | Lo tiene tu compañero[cite: 3, 5] |
| **8** | Diodos de Silicio | 2x **1N4148** (vidrio)[cite: 13] | 2 | ¡Los tienes! |
| **9** | Potenciómetros | **B10K** ($10\text{ k}\Omega$) y **B100K** ($100\text{ k}\Omega$)[cite: 7, 9, 10] | 2 | ¡Los tienes! |
| **10**| Resistencias fijas | $1\text{ k}\Omega$ (x3), $10\text{ k}\Omega$ (x4), $100\text{ k}\Omega$ (x3)[cite: 14] | 10 | **¡FALTA COMPRAR!** |
| **11**| Capacitores Electrolíticos | $1\ \mu\text{F}$, $10\ \mu\text{F}$, $100\ \mu\text{F}$[cite: 8, 11, 15] | 3 | ¡Los tienes! (Para etapas de audio) |
| **12**| Capacitores Cerámicos | Tipo lenteja ($10\text{ nF}$ y $100\text{ nF}$) | 4 | **¡FALTA COMPRAR!** (Para RF y filtros)[cite: 3, 5] |
| **13**| Fuente de Poder | 2x Baterías de 9V + Clips | 2 | Las tiene tu compañero (Para fuente dual $\pm 9\text{V}$)[cite: 5, 7] |
| **14**| Conexiones | Cables Jumper o UTP | 1 set | **¡FALTA COMPRAR!** |
