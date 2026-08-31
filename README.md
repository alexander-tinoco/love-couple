# love-couple

Dos llaveros con pantalla redonda, ojos animados y cámara, que saben el uno del otro.
Regalo de cumpleaños — **26 de septiembre de 2026**.

Inspirado en [STARBOY](https://lilguy.net/) de CREATURE / @lilguynet, pero con su propio
alcance, su propio lenguaje visual (negro mate en vez de cromo) y una idea que el original
no tiene: **son dos, y se extrañan**.

## Documentos

| Archivo | Qué es |
|---|---|
| [`docs/plan.html`](docs/plan.html) | Plan de construcción completo: lista de compra con precios de México, cableado pin a pin, arquitectura, calendario y riesgos. |
| [`docs/editor-de-ojos.html`](docs/editor-de-ojos.html) | Herramienta interactiva para diseñar los ojos y exportarlos a C++. **No necesita hardware** — ábrelo en el navegador. |
| [`referencia/starboy-referencia.jpg`](referencia/starboy-referencia.jpg) | Fotograma del video original, para comparar. |

Los dos HTML son autónomos: se abren con doble clic, sin servidor ni dependencias.

## Qué hace

- Pantalla redonda de 1.28" con ojos animados procedurales (15 estados de ánimo)
- Cámara con detección de caras — **los ojos te siguen**
- Acelerómetro: se marea si lo agitas, se duerme si lo guardas
- Micrófono: se sobresalta con ruido fuerte, se agobia con ruido sostenido
- Cuando los dos llaveros están cerca, se detectan por ESP-NOW
- Cuando están lejos, se extrañan por WiFi a través de un Worker de Cloudflare
- Contador de **cuánto llevan sin verse** y de **días juntos**
- Batería recargable por USB-C, carcasa negra impresa en 3D con cristal de reloj

## Piezas

| Pieza | Dónde | Precio | Cant. |
|---|---|---|---|
| XIAO ESP32-S3 Sense | UNIT Electronics | $325 MXN | 3 |
| IMU MPU6050 | UNIT Electronics | $80 MXN | 3 |
| LiPo 3.7 V 400 mAh `602035` | UNIT Electronics | $67 MXN | 3 |
| Pantalla GC9A01 1.28" 240×240 SPI | MercadoLibre | $93–169 MXN | 3 |
| Cristal mineral plano de reloj Ø34–36 mm | Relojería local | $30–60 MXN | 4 |
| Argollas, tornillos M2, cable AWG30, cinta | Local | ~$230 MXN | — |

**Total con repuestos: ~$2,270 MXN.** Sin repuestos: ~$1,560 MXN.

> UNIT **no** vende la pantalla redonda en ninguna variante — comprobado. Tampoco HeTPro,
> Sandorobotics ni 330ohms. Sale de MercadoLibre.
>
> No compres baterías en Amazon México: la misma LiPo de 400 mAh cuesta $255–298 ahí
> contra $67 en UNIT.

## Cableado

| Componente | Señal | Pin | GPIO |
|---|---|---|---|
| GC9A01 | SCK | `D8` | 7 |
| GC9A01 | MOSI | `D10` | 9 |
| GC9A01 | CS | `D1` | 2 |
| GC9A01 | DC | `D3` | 4 |
| GC9A01 | RST | `D6` | 43 |
| GC9A01 | BLK | `D0` | 1 |
| MPU6050 | SDA | `D4` | 5 |
| MPU6050 | SCL | `D5` | 6 |
| MPU6050 | INT | `D7` | 44 |
| Batería | B+ / B− | pads | — |

La cámara y el micrófono van por el conector interno del XIAO Sense y no ocupan pines.
No hace falta un TP4056: el XIAO ya carga la LiPo por su propio USB-C.
Libres: `D2` (GPIO3) y `D9` (GPIO8).

## Fases

| | Fechas | |
|---|---|---|
| F0 | 30 ago – 1 sep | Comprar |
| F1 | 1 – 6 sep | Encender y parpadear |
| F2 | 5 – 12 sep | Sentidos y cámara |
| F3 | 10 – 18 sep | El vínculo (ESP-NOW + WiFi) |
| F4 | 6 – 19 sep | CAD e impresión (en paralelo) |
| F5 | 19 – 22 sep | Ensamblaje |
| F6 | todo el mes | Animaciones y personalidad |
| — | 25 sep | Colchón |
| — | **26 sep** | **Entrega** |
