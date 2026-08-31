# love-couple

Two keychains with round displays, animated eyes and cameras, that know about each other.
A birthday gift — **26 September 2026**.

Inspired by [STARBOY](https://lilguy.net/) by CREATURE / @lilguynet, but with its own scope,
its own visual language (matte black instead of chrome) and one idea the original doesn't
have: **there are two of them, and they miss each other**.

## Documents

| File | What it is |
|---|---|
| [`docs/build-plan.html`](docs/build-plan.html) | The full build plan: bill of materials with Mexican prices, pin-by-pin wiring, architecture, schedule and risks. |
| [`docs/eye-editor.html`](docs/eye-editor.html) | Interactive tool to design the eyes and export them to C++. **No hardware required** — open it in a browser. |
| [`docs/hardware.html`](docs/hardware.html) | Pinouts, voltage map, every wire, battery runtime, how it fits in the star, WiFi setup once sealed, and safety. Read before ordering. |
| [`reference/`](reference/) | Reference shots of the real device: `starboy-reference.jpg` plus `starboy-01..07.png`. |

Both HTML files are self-contained: open them with a double click, no server, no dependencies.

## What it does

- 1.28" round display with procedural animated eyes (15 moods)
- Camera with face detection — **the eyes follow you**
- Accelerometer: gets dizzy if you shake it, falls asleep when pocketed
- Microphone: startles at sudden noise, gets overwhelmed by sustained noise
- When the two keychains are close, they find each other over ESP-NOW
- When they're apart, they miss each other over WiFi via a Cloudflare Worker
- Counters for **how long since they last met** and **days together**
- USB-C rechargeable battery, black 3D-printed enclosure with a watch crystal

## Parts

| Part | Where | Price | Qty |
|---|---|---|---|
| XIAO ESP32-S3 Sense | UNIT Electronics | $325 MXN | 3 |
| Accelerometer, 3.3 V native | see `docs/hardware.html` | ~$80 MXN | 3 |
| LiPo 3.7 V ~350 mAh `402535` | MercadoLibre | ~$70 MXN | 3 |
| GC9A01 1.28" 240×240 SPI display | MercadoLibre | $93–169 MXN | 3 |
| Flat mineral watch crystal Ø34–36 mm | Local watch-repair shop | $30–60 MXN | 4 |
| Split rings, M2 screws, AWG30 wire, tape | Local | ~$230 MXN | — |

**Total with spares: ~$2,270 MXN.** Without spares: ~$1,560 MXN.

> UNIT does **not** stock the round display in any variant — verified. Neither do HeTPro,
> Sandorobotics or 330ohms. It has to come from MercadoLibre.
>
> Don't buy batteries on Amazon Mexico: the same LiPo costs $255–298 there against
> around $70 elsewhere.
>
> Two parts changed after the hardware review: a **4 mm** cell instead of 6 mm (two
> millimetres off a 20 mm object for 50 mAh), and the accelerometer needs checking —
> the common GY-521 breakout's regulator wants more than 3.3 V and there is no 5 V
> rail on battery. Both are explained in `docs/hardware.html`.

## Wiring

| Component | Signal | Pin | GPIO |
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
| Battery | B+ / B− | pads | — |

The camera and microphone go through the XIAO Sense's internal connector and use no pins.
No TP4056 needed: the XIAO already charges the LiPo over its own USB-C.
Free: `D2` (GPIO3) and `D9` (GPIO8).

## Phases

| | Dates | |
|---|---|---|
| P0 | 30 Aug – 1 Sep | Order parts |
| P1 | 1 – 6 Sep | Light up and blink |
| P2 | 5 – 12 Sep | Senses and camera |
| P3 | 10 – 18 Sep | The link (ESP-NOW + WiFi) |
| P4 | 6 – 19 Sep | CAD and printing (in parallel) |
| P5 | 19 – 22 Sep | Assembly |
| P6 | all month | Animations and personality |
| — | 25 Sep | Buffer |
| — | **26 Sep** | **Delivery** |
