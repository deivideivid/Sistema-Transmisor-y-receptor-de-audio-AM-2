# Lista de Componentes — Sistema Transmisor y Receptor AM

**Estado:** ✅ Lo tenemos · 🛒 Falta comprar · ⚠️ No sirve / sobra · 🤝 Lo tiene el compañero

Cada componente tiene un link a Google Imágenes para ver cómo es físicamente.

---

## 0. Cómo leer los códigos

**Condensadores cerámicos (3 números):** los dos primeros son el número y el tercero es cuántos ceros se le ponen. El resultado está en **picofaradios (pF)**.
- `104` → 10 + 0000 = 100 000 pF = **100 nF**
- `222` → 22 + 00 = 2 200 pF = **2.2 nF**
- `471` → 47 + 0 = **470 pF**
- `22` (o `220`) → **22 pF**. ⚠️ No confundir con `221`, que es **220 pF**.

**Bobinas:** se miden en **microhenrios (µH)**. "100 µH" se lee "cien microhenrios". Algunas traen el código `101` (10 + 0 = 100 µH).

**Electrolíticos:** traen el valor escrito (ej. `10µF 25V`). El voltaje tiene que ser **16 V o más** (mejor 25 V). La pata larga es el **+**.

---

## 1. Lo que ya tenemos y sí sirve

| # | Componente | Referencia | Cant. | Estado | Para qué se usa | Imagen |
| :-- | :-- | :-- | :-: | :-: | :-- | :-- |
| 1 | Protoboard | MB-102, 830 puntos | 1 | ✅ | Montar todo el sistema | [Ver](https://www.google.com/search?tbm=isch&q=protoboard+MB-102+830+puntos) |
| 2 | Micrófono | Electret con cables | 1 | ✅ | Captar la voz | [Ver](https://www.google.com/search?tbm=isch&q=microfono+electret+con+cables) |
| 3 | Amplificador operacional | LM358P (8 pines) | 2 | ✅ | Uno de preamplificador en el TX y otro de buffer en el RX | [Ver](https://www.google.com/search?tbm=isch&q=LM358P+DIP-8) |
| 4 | Modulador | CA3080E (8 pines) | 1 | ✅ | Hacer la modulación AM | [Ver](https://www.google.com/search?tbm=isch&q=CA3080E+DIP-8) |
| 5 | Amplificador de audio | LM386N-1 (8 pines) | 1 | ✅ | Darle fuerza a la voz para el parlante | [Ver](https://www.google.com/search?tbm=isch&q=LM386N-1+DIP-8) |
| 6 | Parlante | 8 Ω (Stetron LS19C050) | 1 | ✅ | Salida de sonido | [Ver](https://www.google.com/search?tbm=isch&q=parlante+8+ohm+peque%C3%B1o) |
| 7 | Transistor | 2N2222A | 2 | ✅ | Oscilador de la portadora | [Ver](https://www.google.com/search?tbm=isch&q=transistor+2N2222A) |
| 8 | Diodo de silicio | 1N4148 | 2 | ✅ | Detector de envolvente (funciona bien porque la señal llega por cable) | [Ver](https://www.google.com/search?tbm=isch&q=diodo+1N4148) |
| 9 | Diodo detector | 1N34A o 1N5819 | 1 | 🤝 | Para comparar con el 1N4148 | [Ver](https://www.google.com/search?tbm=isch&q=diodo+1N34A+germanio) |
| 10 | Potenciómetro | B10K (10 kΩ) | 1 | ✅ | Resistencia del detector RC | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B10K) |
| 11 | Potenciómetro | B100K (100 kΩ) | 1 | ✅ | Ajustar el índice de modulación μ | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B100K) |
| 12 | Baterías + broches | 9 V | 2 | 🤝 | Fuente de +9 V / 0 V / −9 V | [Ver](https://www.google.com/search?tbm=isch&q=bateria+9V+con+broche) |
| 13 | Multímetro | UYUS TSD830 | 1 | ✅ | Continuidad, voltajes, medir μ | — |

## 2. Lo que no sirve o sobra

| Componente | Por qué |
| :-- | :-- |
| ⚠️ Cristal de 20 MHz | Es demasiado rápido para el CA3080 y para la protoboard. Solo se puede reusar con la **opción B** de la sección 5. |

---

## 3. 🛒 Lista EXACTA del circuito

Esto es **todo** lo que usa el circuito, ni más ni menos. **Todo va montado al mismo tiempo en la protoboard**: no son escenarios ni combinaciones.
- **"Usa el circuito"** = cuántas van puestas en la protoboard.
- **"Comprar"** = lo mismo + 1 de repuesto por si una se daña o se pierde. Si quieren ahorrar, compren exactamente lo de "Usa el circuito".
- **"Si no la hay, sirve…"** = solo se usa si en la tienda no está el valor principal.

Primero revisen qué tienen ya en casa y compren **solo lo que falte**.

### 3.0 Mapa: dónde va cada pieza

| Etapa | Piezas que lleva |
| :-- | :-- |
| **Fuente** | 2 electrolíticos de 100 µF (uno en +9 V y otro en −9 V) |
| **TX · Micrófono** | Micrófono, 1 resistencia de 4.7 kΩ, 1 electrolítico de 1 µF |
| **TX · Preamplificador** | LM358 #1, 1 resistencia de 1 kΩ, 1 de 100 kΩ, 2 cerámicos de 100 nF |
| **TX · Ajuste de μ** | Potenciómetro B100K, 1 electrolítico de 10 µF, 1 resistencia de 4.7 kΩ |
| **TX · Oscilador 1 MHz** | 2N2222, cristal de 1 MHz, resistencias de 47 kΩ, 10 kΩ y 1 kΩ, 2 cerámicos de 470 pF, 1 de 10 nF, 1 de 100 nF |
| **TX · Modulador** | CA3080, resistencias de 10 kΩ + 100 Ω (divisor), 1 de 100 Ω, 1 de 22 kΩ, 1 de 10 kΩ (carga), 2 cerámicos de 100 nF |
| **RX · Filtro LC** | 1 resistencia de 1 kΩ, bobina de 100 µH, cerámicos de 220 pF + 22 pF |
| **RX · Detector** | Diodo 1N4148, potenciómetro B10K, 1 cerámico de 2.2 nF |
| **RX · Buffer** | LM358 #2, 2 cerámicos de 100 nF |
| **RX · Amplificador** | LM386, potenciómetro B10K (volumen), 2 electrolíticos de 10 µF, 1 de 220 µF, 1 resistencia de 10 Ω, 1 cerámico de 47 nF, 1 de 100 nF, parlante |

**Totales montados:** 14 resistencias · 15 cerámicos · 7 electrolíticos · 3 potenciómetros · 4 chips · 1 transistor · 1 cristal · 1 bobina · 1 diodo · micrófono · parlante.

**¿Por qué tantos de 100 nF?** Cada chip lleva su propio "colchón" pegado a las patas de alimentación, para que los demás chips no le metan ruido por la fuente. Los chips que usan +9 V y −9 V llevan dos (uno por cada lado).

### No hace falta comprar
- Cristal de 20 MHz (sobra, salvo que se use la opción B de la sección 5).
- Diodo 1N34A/1N5819 del compañero: es opcional, solo para comparar con el 1N4148.
- Interruptor: opcional.
- Lo de la sección 4 (tarjeta de sonido, radio, RTL-SDR): es para medir, se decide después.

### 3.1 Resistencias (1/4 W)

| Valor | Colores | Usa el circuito | Comprar | Dónde va | Si no la hay, sirve… |
| :-- | :-- | :-: | :-: | :-- | :-- |
| 10 Ω | café-negro-negro | 1 | 2 | Red Zobel del LM386 | 8.2 Ω o 12 Ω |
| 100 Ω | café-negro-café | 2 | 3 | Divisor de entrada del CA3080 | 82 Ω a 150 Ω |
| 1 kΩ | café-negro-rojo | 3 | 4 | Preamp, oscilador, entrada del RX | 820 Ω a 1.2 kΩ |
| 4.7 kΩ | amarillo-violeta-rojo | 2 | 3 | Alimentación del micrófono, audio al CA3080 | 3.3 kΩ a 6.8 kΩ |
| 10 kΩ | café-negro-naranja | 3 | 4 | Oscilador, divisor del CA3080, carga del CA3080 | 8.2 kΩ a 12 kΩ |
| 22 kΩ | rojo-rojo-naranja | 1 | 2 | Corriente fija del CA3080 (pin 5) | 2 de 10 kΩ en serie (= 20 kΩ) |
| 47 kΩ | amarillo-violeta-naranja | 1 | 2 | Polarización del oscilador | 2 de 22 kΩ en serie (= 44 kΩ) |
| 100 kΩ | café-negro-amarillo | 1 | 2 | Ganancia del preamplificador | 2 de 47 kΩ en serie (= 94 kΩ) |

### 3.2 Condensadores cerámicos

| Valor | Código | Usa el circuito | Comprar | Dónde va | Si no lo hay, sirve… |
| :-- | :-- | :-: | :-: | :-- | :-- |
| 22 pF | `22` o `220` | 1 | 2 | Filtro LC (ajuste fino) | 18 pF a 33 pF |
| 220 pF | `221` | 1 | 2 | Filtro LC (principal) | Ver tabla de la bobina (3.4) |
| 470 pF | `471` | 2 | 3 | Oscilador de cristal | 390 a 560 pF, o 2 de 220 pF en paralelo |
| 2.2 nF | `222` | 1 | 2 | Detector RC (el condensador que "dibuja" la voz) | 1.5 a 3.3 nF, o 2 de 1 nF (`102`) en paralelo |
| 10 nF | `103` | 1 | 2 | Saca la portadora del oscilador | 4.7 nF a 22 nF |
| 47 nF | `473` | 1 | 2 | Red Zobel del LM386 | 33 nF a 100 nF |
| 100 nF | `104` | 8 | 10 | Desacople: uno pegado a la alimentación de cada chip | 47 nF a 220 nF |

### 3.3 Condensadores electrolíticos (16 V o más)

| Valor | Usa el circuito | Comprar | Dónde va | Si no lo hay, sirve… |
| :-- | :-: | :-: | :-- | :-- |
| 1 µF | 1 | 0 (ya lo tienen) | Micrófono → preamplificador | 1 µF a 4.7 µF |
| 10 µF | 3 | 4 | Audio al CA3080, buffer → LM386, pin 7 del LM386 | 4.7 µF a 22 µF |
| 100 µF | 2 | 2 | Filtro de la fuente (uno en +9 V y otro en −9 V) | 47 µF a 470 µF |
| 220 µF | 1 | 1 | Salida del LM386 al parlante | 100 µF a 470 µF (más grande = más bajos) |

### 3.4 Bobina, cristal, potenciómetro y otros

| Componente | Referencia | Usa | Comprar | Dónde va | Imagen |
| :-- | :-- | :-: | :-: | :-- | :-- |
| **Bobina** | **100 µH** axial (parece una resistencia gordita, colores café-negro-café) o radial tipo tambor (código `101`) | 1 | 2 | Filtro LC del receptor | [Axial](https://www.google.com/search?tbm=isch&q=inductor+axial+100uH) · [Radial](https://www.google.com/search?tbm=isch&q=inductor+radial+100uH+101) |
| **Cristal** | **1 MHz** (HC-49/U, dice `1.000` o `1.000MHz`) | 1 | 1 | Oscilador de la portadora | [Ver](https://www.google.com/search?tbm=isch&q=cristal+cuarzo+1MHz+HC-49) |
| Potenciómetro | B10K | 1 | 1 | Volumen del LM386 | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B10K) |
| Cables | Jumpers macho-macho (mínimo 30, ideal un paquete de 40) o 1 m de UTP sólido | 30 | 40 | Conexiones | [Ver](https://www.google.com/search?tbm=isch&q=cables+jumper+macho+macho+protoboard) |

**Si no consiguen bobina de 100 µH**, sirve otra cambiando el condensador del filtro (la fórmula es C [pF] = 25 330 ÷ L [µH] para 1 MHz):

| Bobina | Condensador del filtro | Cómo armarlo |
| :-- | :-- | :-- |
| 47 µH | ≈ 540 pF | 470 pF + 68 pF en paralelo |
| 82 µH | ≈ 310 pF | 330 pF, o 270 pF + 39 pF |
| **100 µH** | **≈ 253 pF** | **220 pF + 22 pF en paralelo** (principal) |
| 120 µH | ≈ 211 pF | 220 pF solo |
| 150 µH | ≈ 169 pF | 150 pF + 22 pF |
| 220 µH | ≈ 115 pF | 100 pF + 15 pF, o 120 pF |
| De un **radio AM viejo** | El condensador variable del mismo radio | Se saca la barra de ferrita con su bobina y el condensador variable (la perilla de sintonía). Así el filtro se sintoniza con la mano. |

---

## 4. 🛒 Para medir sin osciloscopio (ver sección 6 del proyecto)

| Componente | Referencia | Cant. | Prioridad | Para qué |
| :-- | :-- | :-: | :-: | :-- |
| Tarjeta de sonido USB | Cualquiera con entrada de micrófono (rosada) | 1 | 🟠 Recomendado | Ver la voz original y la recuperada en el PC |
| Cable de audio | 3.5 mm macho a 2 caimanes (o un cable 3.5 mm cortado) | 1 | 🟠 Recomendado | Conectar la protoboard a la tarjeta de sonido |
| Radio AM | Cualquiera (de pilas, del carro) | 1 | 🟠 Recomendado | Comprobar que el transmisor sale al aire en ~1000 kHz |
| RTL-SDR | RTL-SDR Blog V4 (USB) | 1 | 🟢 Opcional | Ver el espectro real de la señal AM (portadora + bandas laterales) |

---

## 5. Alternativas si no conseguimos el cristal de 1 MHz

En orden de preferencia. **Ojo:** si la frecuencia final no es exactamente 1 MHz, hay que cambiar el condensador del filtro LC con la fórmula: **C [pF] = 25 330 ÷ (L [µH] × f² [MHz])**.

### Opción A — Oscilador de cristal "en cajita" de 1 MHz (la más fácil)
Es una cajita metálica que ya trae el cristal y el circuito adentro: se alimenta y saca la onda.
- **Qué comprar:** oscilador de 1 MHz (dice `1.000` o `1.000MHz`) en formato **DIP-14** (rectangular) o **DIP-8** (cuadrado) + regulador **78L05** (TO-92, pequeñito) o **7805** (TO-220, más grande), porque la cajita funciona con 5 V y no con 9 V.
- **Patas DIP-14:** 7 = tierra, 8 = salida, 14 = +5 V (la 1 no se conecta). La esquina en punta marca la pata 1.
- **Patas DIP-8:** 4 = tierra, 5 = salida, 8 = +5 V (la 1 no se conecta).
- **Ventaja:** cero calibración y muy estable.
- **Desventaja:** saca onda **cuadrada**, no senoidal. No es grave: el filtro LC del receptor la limpia. Igual hay que reducirla con el divisor antes del CA3080, igual que con el cristal.
- [Ver oscilador](https://www.google.com/search?tbm=isch&q=oscilador+cristal+1MHz+DIP-14) · [Ver 78L05](https://www.google.com/search?tbm=isch&q=regulador+78L05)

### Opción B — Cualquier cristal común + chip divisor (sirve hasta el de 20 MHz que ya tenemos)
Un chip **74HC04** hace oscilar el cristal y un chip **74HC4040** divide la frecuencia, como una caja de cambios que baja la velocidad.
- **Qué comprar:** 74HC04 + 74HC4040 + 78L05 + resistencia de **1 MΩ** + 2 condensadores de **22 pF** + el cristal.
- **Qué cristal y de qué pata del 74HC4040 sale la señal:**

| Cristal | Divide entre | Sale por la pata | Portadora | ¿Sirve? |
| :-- | :-: | :-: | :-- | :-- |
| 4 MHz (muy común) | 4 | 7 | **1.000 MHz** | ✅ Ideal |
| 8 MHz (común) | 8 | 6 | **1.000 MHz** | ✅ Ideal |
| 16 MHz (el de Arduino) | 16 | 5 | **1.000 MHz** | ✅ Ideal |
| 20 MHz (**el que ya tenemos**) | 16 | 5 | **1.25 MHz** | ✅ Sirve (filtro LC con 100 µH → ≈ 162 pF = 150 pF + 12 pF) |

- **Ventaja:** muy estable y cualquier cristal común funciona.
- **Desventaja:** son dos chips más en la protoboard y también saca onda cuadrada.
- [Ver 74HC04](https://www.google.com/search?tbm=isch&q=74HC04+DIP-14) · [Ver 74HC4040](https://www.google.com/search?tbm=isch&q=74HC4040+DIP-16) · [Ver cristal 4 MHz](https://www.google.com/search?tbm=isch&q=cristal+4MHz+HC-49)

### Opción C — Oscilador LC sin cristal (Colpitts con el 2N2222)
En vez del cristal, la frecuencia la ponen la bobina y dos condensadores, como un columpio que oscila a su propio ritmo.
- **Qué comprar:** nada nuevo. Se usan el 2N2222, **una bobina de 100 µH** (por eso pedimos 2) y los **2 condensadores de 470 pF**.
- **Frecuencia:** ≈ 1.04 MHz. Se busca con el radio AM (ahí se oye un "silencio" cuando se encuentra) y se ajusta cambiando los condensadores.
- **Ventaja:** barato y con piezas que ya están en la lista.
- **Desventaja:** la frecuencia "se corre" un poco con la temperatura o al tocar el circuito.

### Opción D — Módulo generador AD9833 + Arduino (solo si alguien tiene Arduino)
- **Qué comprar:** módulo **AD9833**.
- **Ventaja:** saca una senoidal limpia de exactamente 1.000 MHz, programada desde el código.
- **Desventaja:** hay que programarlo y depende del Arduino.
- [Ver AD9833](https://www.google.com/search?tbm=isch&q=modulo+AD9833)

**Recomendación:** 1) cristal de 1 MHz → 2) **Opción A** → 3) **Opción B** con un cristal de 4 MHz (o el de 20 MHz que ya tenemos) → 4) **Opción C** como último recurso.