# Lista de Componentes para el Proyecto AM

## 1. Etapa de Transmisión

*   **Preamplificador de Audio:**
    *   **Opción principal:** LM358 o TL072.
    *   *Alternativa:* Transistores 2N3904 o 2N2222.
*   **Oscilador de Portadora (RF):**
    *   **Opción principal:** Cristal de Cuarzo de 1 MHz y transistor 2N2222.
*   **Modulador (Multiplicador):**
    *   **Opción principal:** CA3080.
    *   *Alternativas:* AD633, MC1496 o LM1496.

## 2. Etapa de Recepción

*   **Diodo Detector (Detector de Envolvente):**
    *   **Opción principal:** 1N34A (Germanio) o 1N5711, BAT41 (Schottky).
    *   *Alternativa:* 1N4148 (Silicio - menos recomendado por su mayor caída de voltaje).
*   **Filtro Pasa-Bajos (RC):**
    *   **Componentes necesarios:** Potenciómetro (ej. 10 kΩ o 100 kΩ) y capacitores (1 nF, 10 nF, 100 nF).
*   **Amplificador de Audio Final:**
    *   **Opción principal:** LM386.

**Nota:** Puedes utilizar tu propio micrófono y bocina/parlante (8 Ω) para el proyecto.