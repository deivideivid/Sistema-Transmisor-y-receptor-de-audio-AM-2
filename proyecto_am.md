# Diseño e Implementación de un Sistema Transmisor y Receptor de Audio AM

**Materia:** Teoría de Señales
**Fecha:** 19 de Octubre de 2026
**Ubicación:** Manizales, Caldas, Colombia

---

## 1. Introducción
En el estudio de las telecomunicaciones y el procesamiento de señales, la modulación de amplitud (AM) es una de las técnicas fundamentales que permite la transmisión de información a largas distancias. Este proyecto semestral tiene como propósito el diseño, análisis e implementación de un Sistema Transmisor y receptor de audio AM. En la práctica, esto implica trasladar el espectro de frecuencias de una señal de audio (la señal moduladora o mensaje) hacia una frecuencia mucho más alta (la señal portadora), lo que hace posible su radiación y propagación electromagnética. A lo largo del curso de Teoría de Señales, este proyecto servirá para materializar los modelos matemáticos y el análisis espectral en un sistema real. El desarrollo del trabajo abarcará todas las etapas críticas del proceso de comunicación: desde la captación y acondicionamiento de la voz, pasando por el proceso de modulación, hasta su posterior recepción, demodulación (mediante detector de envolvente) y amplificación final; todo con el objetivo de recuperar la información original con la menor pérdida y distorsión posible.

## 2. Objetivo General
Diseñar, analizar e implementar un Sistema Transmisor y receptor de audio AM, aplicando los modelos matemáticos y físicos de la Teoría de Señales para lograr la modulación, transmisión y correcta recuperación de una señal de audio analógica.

## 3. Objetivos Específicos
*   **Analizar el comportamiento espectral:** Modelar matemáticamente las señales en el dominio del tiempo y de la frecuencia durante los procesos de modulación y demodulación AM, verificando el cumplimiento de la teoría.
*   **Diseñar las etapas de transmisión y recepción:** Dimensionar y establecer los requerimientos de los circuitos correspondientes al oscilador de la portadora, el modulador, el filtro pasa banda, el detector de envolvente y los amplificadores de audio.
*   **Implementar y sintonizar el sistema:** Construir los circuitos diseñados ajustando el índice de modulación para evitar fenómenos de sobremodulación.
*   **Evaluar el rendimiento:** Comparar y medir las características de la señal de audio original frente a la señal recuperada en el receptor, analizando factores como el ruido, el ancho de banda y la fidelidad de la señal.

---

## 4. Propuesta Técnica Recomendada: "Híbrido de IC y Discretos"
Esta propuesta equilibra costo, facilidad de implementación en protoboard y valor didáctico, basándose en la bibliografía clásica de sistemas de comunicaciones electrónicas[cite: 5, 8]. Consiste en utilizar un circuito integrado (IC) para la modulación (asegurando precisión matemática) y componentes discretos simples para la demodulación.

### 4.1. Transmisor (Modulador AM)
*   **Micrófono / Generador de Mensaje:** Capta la señal de audio de baja frecuencia[cite: 6, 8]. Se puede usar un micrófono propio preamplificado o inyectado mediante un condensador.
*   **Preamplificador de Audio:** Eleva la amplitud de la señal de voz a un nivel de voltaje útil (ej. **LM358**, **TL072**, o transistores BJT como **2N3904** / **2N2222**)[cite: 8].
*   **Oscilador de Portadora de RF:** Genera la señal de alta frecuencia[cite: 6, 8, 9]. Para pruebas iniciales, se puede usar un generador de señales de laboratorio (ej. a 1 MHz o 5 MHz)[cite: 5]. Para la implementación final, se sugiere un oscilador controlado por **Cristal de Cuarzo de 1 MHz** con un transistor **2N2222**[cite: 7].
*   **Modulador (Multiplicador Analógico):** Realiza la multiplicación de la señal portadora por la señal de mensaje[cite: 6, 8, 9]. Se recomienda el chip **CA3080** (Amplificador de Transconductancia Operacional) por su facilidad de uso en protoboard[cite: 8]. Alternativas: **AD633**, **MC1496** o **LM1496** (requieren más configuración externa).

### 4.2. Receptor (Demodulador / Detector de Envolvente)
*   **Filtro Pasa Banda / Antena:** Capta y selecciona la frecuencia portadora específica[cite: 4, 9, 11]. Se construye con un arreglo LC (inductor y condensador).
*   **Diodo Detector:** Corta la mitad inferior de la señal modulada (rectificación de media onda)[cite: 5, 9]. Es crucial usar un diodo de baja caída de voltaje (0.2V - 0.3V), como los de Germanio (**1N34A**) o Schottky (**1N5711**, **BAT41**)[cite: 5]. Un diodo de silicio estándar (1N4148) es menos sensible[cite: 5].
*   **Filtro Pasa-Bajos (RC):** Un conjunto de potenciómetro (ej. 10 kΩ o 100 kΩ) y condensador cerámico/poliéster (ej. 1nF, 10nF, 100nF) que "suaviza" los picos de RF y recupera la forma de onda de baja frecuencia original[cite: 5, 7, 8, 9].
*   **Amplificador de Audio:** Eleva la potencia de la señal recuperada[cite: 4]. Se recomienda el integrado **LM386**.
*   **Bocina / Parlante:** Convierte la señal eléctrica en sonido[cite: 4]. Se puede usar un parlante pequeño de 8 Ω[cite: 5].

---

## 5. Simulación Lógica del Sistema (Paso a Paso)
1.  **Generación:** Se produce una onda senoidal lenta (voz/mensaje, ej. 1 kHz)[cite: 6, 8] y una onda senoidal rápida y estable (portadora, ej. 1 MHz)[cite: 6, 8].
2.  **Modulación:** El chip multiplicador (CA3080) combina ambas señales. La amplitud de la portadora rápida de 1 MHz varía siguiendo el contorno de la señal lenta de 1 kHz, creando la "envolvente"[cite: 6, 8, 10]. Se ajusta el índice de modulación para evitar sobremodulación[cite: 10].
3.  **Transmisión:** La señal modulada viaja por el canal (cable jumper en protoboard o antena real)[cite: 8].
4.  **Selección:** El filtro pasa banda del receptor elimina frecuencias no deseadas, dejando solo la señal alrededor de 1 MHz[cite: 9].
5.  **Detección (Demodulación):** El diodo (1N34A) elimina la parte negativa de la señal de RF[cite: 5, 9]. El circuito RC se carga en los picos de RF y se descarga lentamente, "dibujando" la envolvente y eliminando la alta frecuencia[cite: 5, 8, 9]. La salida es la onda original de 1 kHz[cite: 5, 8, 9].
6.  **Reproducción:** La señal demodulada se amplifica (LM386) y se envía al parlante[cite: 4].