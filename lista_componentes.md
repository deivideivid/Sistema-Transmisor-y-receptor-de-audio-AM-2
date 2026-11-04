# Lista de Componentes — Sistema Transmisor y Receptor AM

**Estado:** ✅ Lo tenemos · 🛒 Falta comprar · ⚠️ No sirve / sobra · 🤝 Lo tiene el compañero

Cada componente tiene un link a Google Imágenes para ver cómo es físicamente.

---

## 1. Lo que ya tenemos y sí sirve

| # | Componente | Referencia | Cant. | Estado | Para qué se usa | Imagen |
| :-- | :-- | :-- | :-: | :-: | :-- | :-- |
| 1 | Protoboard | MB-102, 830 puntos | 1 | ✅ | Montar todo el sistema | [Ver](https://www.google.com/search?tbm=isch&q=protoboard+MB-102+830+puntos) |
| 2 | Micrófono | Electret con cables | 1 | ✅ | Captar la voz | [Ver](https://www.google.com/search?tbm=isch&q=microfono+electret+con+cables) |
| 3 | Amplificador operacional | LM358P (8 pines) | 2 | ✅ | Uno de preamplificador en el TX y otro de buffer en el RX | [Ver](https://www.google.com/search?tbm=isch&q=LM358P+DIP-8) |
| 4 | Modulador | CA3080E (8 pines) | 1 | ✅ | Hacer la modulación AM | [Ver](https://www.google.com/search?tbm=isch&q=CA3080E+DIP-8) |
| 5 | Amplificador de audio | LM386N-1 (8 pines) | 1 | ✅ | Darle fuerza a la voz para el parlante | [Ver](https://www.google.com/search?tbm=isch&q=LM386N-1+DIP-8) |
| 6 | Parlante | 8 Ω (Stetron LS19C050) | 1 | ✅ | Salida de sonido | [Ver](https://www.google.com/search?tbm=isch&q=parlante+8+ohm+pequeño) |
| 7 | Transistor | 2N2222A | 2 | ✅ | Oscilador de la portadora | [Ver](https://www.google.com/search?tbm=isch&q=transistor+2N2222A) |
| 8 | Diodo de silicio | 1N4148 | 2 | ✅ | Detector de envolvente (plan A, funciona bien porque la señal llega por cable) | [Ver](https://www.google.com/search?tbm=isch&q=diodo+1N4148) |
| 9 | Diodo detector | 1N34A (germanio) o 1N5819 (Schottky) | 1 | 🤝 | Detector de envolvente (para comparar con el 1N4148) | [Ver](https://www.google.com/search?tbm=isch&q=diodo+1N34A+germanio) |
| 10 | Potenciómetro | B10K (10 kΩ) | 1 | ✅ | Resistencia del filtro RC del detector | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B10K) |
| 11 | Potenciómetro | B100K (100 kΩ) | 1 | ✅ | Ajustar el índice de modulación en el CA3080 | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B100K) |
| 12 | Condensadores electrolíticos | 1 µF, 10 µF, 100 µF | 1 c/u | ✅ | Pasar audio entre etapas (no alcanzan, ver compras) | [Ver](https://www.google.com/search?tbm=isch&q=condensador+electrolitico+10uF) |
| 13 | Baterías + broches | 9 V | 2 | 🤝 | Fuente de +9 V / 0 V / −9 V | [Ver](https://www.google.com/search?tbm=isch&q=bateria+9V+con+broche) |

## 2. Lo que no sirve o sobra

| Componente | Por qué |
| :-- | :-- |
| ⚠️ Cristal de 20 MHz | El CA3080 no alcanza esa velocidad, la protoboard mete mucha interferencia a 20 MHz y no se puede probar con un radio AM. Se cambia por uno de **1 MHz**. Solo se podría reusar con la opción C de la sección 4. |

---

## 3. 🛒 Lista de compras

| # | Componente | Referencia / Código | Cant. | Prioridad | Para qué se usa | Imagen |
| :-- | :-- | :-- | :-: | :-: | :-- | :-- |
| 1 | **Cristal de cuarzo** | **1 MHz** (HC-49) | 1 | 🔴 Urgente | Portadora del transmisor | [Ver](https://www.google.com/search?tbm=isch&q=cristal+cuarzo+1MHz+HC-49) |
| 2 | **Bobina / inductor** | **100 µH** axial (parece una resistencia) | 2 | 🔴 Urgente | Filtro LC del receptor | [Ver](https://www.google.com/search?tbm=isch&q=inductor+axial+100uH) |
| 3 | Condensadores cerámicos (pF) | 22 pF (22), 100 pF (101), 220 pF (221), 470 pF (471) | 2 c/u | 🔴 Urgente | Oscilador de cristal y filtro LC | [Ver](https://www.google.com/search?tbm=isch&q=condensador+ceramico+220pF+221) |
| 4 | Condensadores cerámicos | 100 nF (104) | 8 | 🔴 Urgente | Desacople: uno pegado a la alimentación de cada chip | [Ver](https://www.google.com/search?tbm=isch&q=condensador+ceramico+104+100nF) |
| 5 | Condensadores cerámicos | 1 nF (102), 2.2 nF (222), 4.7 nF (472), 10 nF (103), 47 nF (473) | 2 c/u | 🟠 Necesario | Detector RC (2.2 nF es el principal) y red Zobel del LM386 (47 nF) | [Ver](https://www.google.com/search?tbm=isch&q=condensador+ceramico+222+2.2nF) |
| 6 | Condensadores electrolíticos | 10 µF ×4, 100 µF ×2, 220 µF ×1 | 7 | 🟠 Necesario | Paso de audio entre etapas, filtro de la fuente, salida al parlante (220 µF) | [Ver](https://www.google.com/search?tbm=isch&q=condensador+electrolitico+220uF+16V) |
| 7 | **Kit surtido de resistencias** | 1/4 W (que traiga 10 Ω, 100 Ω, 1 k, 2.2 k, 4.7 k, 10 k, 47 k, 100 k) | 1 kit | 🟠 Necesario | Todas las etapas | [Ver](https://www.google.com/search?tbm=isch&q=kit+surtido+resistencias+1%2F4W) |
| 8 | Potenciómetro | B10K | 1 | 🟠 Necesario | Volumen del LM386 | [Ver](https://www.google.com/search?tbm=isch&q=potenciometro+B10K) |
| 9 | Cables | Jumpers macho-macho o 1 m de UTP sólido | 1 set | 🟠 Necesario | Conexiones en la protoboard | [Ver](https://www.google.com/search?tbm=isch&q=cables+jumper+macho+macho+protoboard) |
| 10 | Interruptor | Switch deslizante pequeño | 1 | 🟢 Opcional | Apagar las baterías sin desconectarlas | [Ver](https://www.google.com/search?tbm=isch&q=switch+deslizante+protoboard) |

> **Tip:** si venden **kit surtido de condensadores cerámicos**, sale más barato y trae casi todos los de las filas 3, 4 y 5.

---

## 4. Alternativas si no conseguimos el cristal de 1 MHz

| Opción | Qué se compra | Dificultad | Ventajas | Desventajas |
| :-- | :-- | :-: | :-- | :-- |
| **A. Oscilador de cristal en cajita** | Oscilador de 1 MHz encapsulado (4 pines, DIP-8 o DIP-14) + regulador **7805** para sacar 5 V de la batería de 9 V | Fácil | Ya trae todo adentro, solo se alimenta y saca la onda | Saca onda cuadrada (hay que suavizarla con el filtro LC) y necesita el 7805 · [Ver](https://www.google.com/search?tbm=isch&q=oscilador+cristal+1MHz+DIP) |
| **B. Oscilador LC (Colpitts)** | Nada extra: se usan el 2N2222, una bobina de 100 µH y condensadores de pF | Media | No necesita cristal y se puede sintonizar en cualquier punto de la banda AM | Es menos estable, la frecuencia "se corre" un poquito con la temperatura |
| **C. Reusar el cristal de 20 MHz con un divisor** | Chip **74HC04** (para el oscilador) + chip **74HC4040** (divide entre 16) + regulador **7805** | Difícil | 20 MHz ÷ 16 = **1.25 MHz**, dentro de la banda AM y muy estable | Son dos chips más y ocupan espacio en la protoboard |
| **D. Generador de señales del laboratorio** | Nada | Muy fácil | Perfecto para las primeras pruebas | No es parte del circuito final |

**Recomendación:** buscar primero el cristal de 1 MHz. Si no hay, la **opción A**. Mientras tanto, se prueba con la **opción D**.
