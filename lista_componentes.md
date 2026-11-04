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



| # | Componente | Valor / Referencia | Cantidad | Estado actual / Observación |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **Micrófono** | Electret (cables rojo/negro) | 1 | ¡Lo tienes! |
| **2** | **Preamplificador** | IC **LM358P** (8 pines) | 2 | ¡Los tienes! |
| **3** | **Modulador AM** | IC **CA3080E** (8 pines) | 1 | ¡Lo tienes! |
| **4** | **Amplificador Audio**| IC **LM386N-1** (8 pines) | 1 | ¡Lo tienes! |
| **5** | **Transistor NPN** | **2N2222A** | 2 | ¡Los tienes! |
| **6** | **Cristal de Cuarzo** | **20 MHz** (Metálico) | 1 | ¡Lo tienes! (Ojo con las capacidades parásitas en protoboard) |
| **7** | **Diodo Detector** | Germanio / Schottky | 1 | Lo tiene tu compañero |
| **8** | **Diodos de Silicio** | 1N4148 (vidrio) | 2 | ¡Los tienes! |
| **9** | **Potenciómetros** | **B10K** ($10\text{ k}\Omega$) y **B100K** ($100\text{ k}\Omega$) | 2 | ¡Los tienes! |
| **10**| **Resistencias** | $10\text{ k}\Omega$ (Café-Negro-Naranja-Oro) | 1 | **¡FALTA! Comprar de 5 a 10 más variadas ($1\text{ k}\Omega$ a $100\text{ k}\Omega$)** |
| **11**| **Capacitores Electrolíticos**| $1\ \mu\text{F}$, $10\ \mu\text{F}$, $100\ \mu\text{F}$ | 3 | ¡Los tienes! |
| **12**| **Capacitores Cerámicos** | Tipo "lenteja" ($1\text{ nF}$ a $100\text{ nF}$) | 0 | **¡FALTA! Comprar para el filtro y desacoples** |
| **13**| **Alimentación** | Baterías de **9V** + Clips | 2 | Las tiene tu compañero (para fuente dual $\pm 9\text{V}$) |
