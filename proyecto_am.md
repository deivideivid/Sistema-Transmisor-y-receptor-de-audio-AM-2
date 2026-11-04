# Diseño e Implementación de un Sistema Transmisor y Receptor de Audio AM

**Materia:** Teoría de Señales
**Fecha:** 19 de octubre de 2026
**Ubicación:** Manizales, Caldas, Colombia

---

## 1. Introducción
La modulación de amplitud (AM) es una de las técnicas base de las telecomunicaciones. La idea es sencilla: una señal de audio, como la voz, no se puede mandar sola muy lejos, entonces la "montamos" sobre una onda de frecuencia mucho más alta, llamada portadora. Esa onda rápida es la que viaja, y en el otro extremo se le quita la portadora para quedarnos otra vez con la voz.

En este proyecto vamos a diseñar, analizar y armar un sistema transmisor y receptor de audio AM en protoboard. La idea es llevar a un circuito real lo que vemos en clase de Teoría de Señales: el modelo matemático de la señal AM, su espectro y el detector de envolvente. El sistema cubre todo el recorrido: captar la voz con un micrófono, amplificarla, modularla, transmitirla, recibirla, demodularla y escucharla en un parlante, tratando de que la voz llegue con la menor distorsión posible.

## 2. Objetivo general
Diseñar, analizar e implementar un sistema transmisor y receptor de audio AM, aplicando los modelos matemáticos de la Teoría de Señales para modular, transmitir y recuperar correctamente una señal de audio analógica.

## 3. Objetivos específicos
*   **Analizar el comportamiento espectral:** modelar las señales en el tiempo y en la frecuencia durante la modulación y la demodulación AM, y comprobar que se cumple la teoría.
*   **Diseñar las etapas de transmisión y recepción:** calcular los valores de los circuitos del oscilador de la portadora, el modulador, el filtro pasa banda, el detector de envolvente y los amplificadores de audio.
*   **Implementar y sintonizar el sistema:** armar los circuitos y ajustar el índice de modulación para que no haya sobremodulación.
*   **Evaluar el rendimiento:** comparar la señal de audio original con la recuperada en el receptor, mirando el ruido, el ancho de banda y la fidelidad de la señal.

---

## 4. Modelo matemático
Si la voz (mensaje) es $v_m(t) = V_m\cos(2\pi f_m t)$ y la portadora es $v_c(t) = V_c\cos(2\pi f_c t)$, la señal AM queda:

$$v_{AM}(t) = \big[V_c + v_m(t)\big]\cos(2\pi f_c t)$$

Ojo: el modulador **no solo multiplica**. Primero le **suma un nivel fijo** ($V_c$) a la voz y después multiplica por la portadora. Si solo multiplicara, la portadora se apagaría cada vez que la voz pasa por cero y el detector de envolvente no podría recuperar nada.

El índice de modulación es $\mu = V_m / V_c$. Tiene que quedar entre 0 y 1; si pasa de 1 hay **sobremodulación** y la voz sale distorsionada.

Al desarrollar la expresión aparecen tres componentes en el espectro: la portadora en $f_c$ y dos bandas laterales en $f_c - f_m$ y $f_c + f_m$, cada una con amplitud $\mu V_c/2$. El ancho de banda es $B = 2f_m$.

---

## 5. Propuesta técnica: "Híbrido de IC y discretos"
Usamos un circuito integrado para la modulación (más preciso y fácil de controlar) y componentes discretos sencillos para la demodulación. Así el proyecto es barato, cabe en una protoboard y se ve claramente cada etapa.

**Valores de diseño:** portadora de **1 MHz**, voz entre **300 Hz y 3 kHz**, índice de modulación entre **0.5 y 0.8**.

¿Por qué 1 MHz? Porque cae dentro de la banda AM comercial (530–1700 kHz), así que podemos probar el transmisor con un radio AM normal antes de tener listo el receptor. Además, a esa frecuencia el CA3080 y la protoboard todavía se comportan bien.

### 5.1. Transmisor
*   **Micrófono electret:** capta la voz. Necesita una resistencia de alimentación (entre 2.2 kΩ y 10 kΩ) y un condensador para pasar la señal a la siguiente etapa.
*   **Preamplificador (LM358):** sube la voz a un nivel útil. En este punto también se ajusta cuánta voz entra al modulador, o sea, el índice de modulación.
*   **Oscilador de portadora (cristal de 1 MHz + 2N2222):** genera la onda rápida y estable de 1 MHz. Para las primeras pruebas se puede reemplazar por el generador de señales del laboratorio.
*   **Modulador (CA3080):** la portadora entra por las entradas del chip, pero bastante reducida con un divisor de voltaje, porque el CA3080 solo acepta unos pocos milivoltios. La voz, sumada a una corriente fija, entra por el pin de control (pin 5). A la salida queda la señal AM.

### 5.2. Receptor
*   **Filtro pasa banda LC:** una bobina de 100 µH con un condensador de unos 250 pF, sintonizados en 1 MHz. Deja pasar nuestra señal y frena las demás.
*   **Diodo detector:** deja pasar solo la mitad positiva de la señal. Lo ideal es un diodo de germanio (1N34A) o Schottky (BAT41, 1N5711). Como la señal llega por cable y con buena amplitud, un 1N4148 también funciona.
*   **Filtro pasa bajos RC:** un potenciómetro de 10 kΩ con un condensador de 2.2 nF ($\tau \approx 22\ \mu s$). El condensador se carga en cada pico de la portadora y se descarga despacio por la resistencia, y así va "dibujando" la envolvente, que es la voz.
*   **Buffer (segundo LM358):** separa el detector del amplificador para que el amplificador no le "robe" señal al filtro RC.
*   **Amplificador de audio (LM386):** le da potencia a la voz recuperada. Se alimenta entre +9 V y tierra.
*   **Parlante de 8 Ω:** convierte la señal eléctrica en sonido.

### 5.3. Alimentación
Usamos dos baterías de 9 V en serie para tener **+9 V, 0 V (tierra) y −9 V**. El CA3080 usa +9 V y −9 V. El LM386 va **solo entre +9 V y tierra**, porque no aguanta los 18 V que hay entre +9 V y −9 V.

---

## 6. Cómo funciona el sistema paso a paso
1.  **Captura:** el micrófono capta la voz y el LM358 la amplifica.
2.  **Portadora:** el oscilador de cristal genera una onda estable de 1 MHz.
3.  **Modulación:** el CA3080 hace que la amplitud de la portadora suba y baje siguiendo la forma de la voz. Ese contorno es la envolvente. Se ajusta $\mu$ para que no pase de 1.
4.  **Transmisión:** la señal AM viaja por un cable (o una antena corta) hasta el receptor.
5.  **Selección:** el filtro LC deja pasar solo lo que está alrededor de 1 MHz.
6.  **Detección:** el diodo corta la parte negativa y el filtro RC sigue los picos, quitando la portadora y dejando la voz.
7.  **Reproducción:** el LM386 amplifica la voz recuperada y la manda al parlante.

## 7. Cómo vamos a evaluar el sistema
La universidad no tiene osciloscopio, así que vamos a medir con herramientas que sí tenemos al alcance:

*   **Tarjeta de sonido del PC como osciloscopio de audio:** con una tarjeta de sonido USB y un programa gratuito (Soundcard Oscilloscope o Audacity) vemos la voz original (salida del preamplificador) y la voz recuperada (salida del buffer del receptor), y las comparamos en el tiempo y en la frecuencia (FFT). La señal entra por un divisor de voltaje y un condensador para no pasarle más de 1 V a la tarjeta. Con esto cubrimos la comparación de fidelidad, ruido y ancho de banda del audio.
*   **Radio AM comercial:** sintonizada en unos 1000 kHz, confirma que el transmisor está funcionando y que la voz se entiende.
*   **Índice de modulación con multímetro y tono de prueba:** con un tono fijo en el micrófono, la salida del detector tiene una parte fija (que equivale a $V_c$) y una parte que sube y baja (que equivale a $V_m$). Midiendo la parte fija con el multímetro y la parte variable con la tarjeta de sonido, calculamos $\mu = V_m / V_c$.
*   **Espectro de la señal AM (opcional):** con un receptor RTL-SDR conectado al PC se ve el espectro real alrededor de 1 MHz: la portadora y las dos bandas laterales en $f_c \pm f_m$.
*   **Simulación:** las formas de onda que no podemos medir directamente (la portadora y la señal AM en el tiempo) se muestran con el dashboard del proyecto y una simulación del circuito.