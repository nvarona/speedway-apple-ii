# 🏎️ SPEEDWAY — Applesoft BASIC Game

![Platform](https://img.shields.io/badge/Platform-Apple%20IIe-green)
![Language](https://img.shields.io/badge/Language-Applesoft%20BASIC-brightgreen)
![Version](https://img.shields.io/badge/Version-3.1-blue)
![Year](https://img.shields.io/badge/Year-2026-lightgrey)

Un juego de carreras ASCII para **Apple IIe** escrito en **Applesoft BASIC**, inspirado en el clásico *Speedway* de 1988.

```
        XXX    0    XXX
        XXX         XXX
        XXX  <=>    XXX
        XXX         XXX
        XXX   ...   XXX
        XXX         XXX
        XXX    0    XXX   ← TU COCHE
        XXX         XXX
        XXX   <0>   XXX
        XXX         XXX
```

---

## 🕹️ Descripción

Eres un piloto de moto (`0`) que avanza por una carretera que hace scroll vertical de abajo hacia arriba. La carretera zigzaguea y se va estrechando con la dificultad. Debes esquivar los obstáculos que vienen hacia ti moviendo el coche horizontalmente.

---

## 🎮 Cómo Jugar

| Tecla | Acción |
|---|---|
| `←` Flecha izquierda | Mover coche a la izquierda |
| `→` Flecha derecha | Mover coche a la derecha |

- El juego **va acelerando** conforme aumenta tu puntuación
- Tienes **3 vidas**
- Si chocas con un obstáculo, pierdes una vida y vuelves al centro
- Si te quedas sin vidas, se muestra tu puntuación final

---

## ⚠️ Obstáculos

| Símbolo | Nombre | Efecto |
|---|---|---|
| `<=>` | Coche contrario | Pierdes 1 vida |
| `<0>` | Coche contrario | Pierdes 1 vida |
| `...` | Mancha de aceite | Te hace patinar (desvío aleatorio) |
| `..` | Mancha de aceite pequeña | Te hace patinar |
| `+` | Granada | Pierdes 2 vidas |

---

## 📺 Requisitos

- **Apple IIe** (o emulador compatible)
- **Applesoft BASIC** (incluido en ROM del Apple IIe)
- Memoria RAM: 32K mínimo

### Emuladores recomendados

- [AppleWin](https://github.com/AppleWin/AppleWin) — Windows
- [LinApple](https://github.com/linappleii/linapple) — Linux
- [OpenEmulator](https://openemulator.github.io/) — macOS
- [Virtual Apple II](https://www.scullinsteel.com/apple2/) — Web (navegador)

---

## 🚀 Instrucciones de Carga

### En un Apple IIe real o emulador

1. Abre el emulador y arranca con Applesoft BASIC
2. En el prompt `]` escribe `NEW` y pulsa ENTER
3. Copia y pega el código línea a línea, o usa la función de carga del emulador
4. Escribe `RUN` y pulsa ENTER

### Desde un archivo de disco (.dsk)

```
]LOAD SPEEDWAY
]RUN
```

---

## 📁 Estructura del Proyecto

```
speedway/
│
├── README.md           ← Este archivo
├── SPEEDWAY.BAS        ← Código fuente principal Applesoft BASIC
└── SCREENSHOT.png      ← Captura de pantalla del juego
```

---

## 🗺️ Estructura del Código

| Líneas | Función |
|---|---|
| 100–169 | Inicialización, variables y arrays |
| 170–229 | Dibujo de pantalla inicial |
| 230–330 | **Bucle principal del juego** |
| 500–525 | Pantalla de Game Over |
| 530–610 | Pantalla de presentación |
| 650 | Subrutina: dibujar paredes de una fila |
| 700–725 | Subrutina: lectura de teclado |
| 800–855 | Subrutina: generación de obstáculos |
| 900–998 | Subrutina: detección de colisiones |

---

## ⚙️ Variables Principales

| Variable | Descripción |
|---|---|
| `X` | Posición horizontal del coche |
| `OX` | Posición anterior del coche (para borrado) |
| `LV` | Vidas restantes |
| `SC` | Puntuación actual |
| `SK` | Desplazamiento por patinada de aceite |
| `WP(22)` | Array: posición de pared izquierda por fila |
| `RD$(22)` | Array: contenido de obstáculo por fila |
| `OC(22)` | Array: columna de obstáculo por fila |
| `WD` | Dirección del zigzag de carretera (-1, 0, 1) |
| `CW` | Ancho de la carretera (14 columnas) |
| `SP` | Velocidad del scroll (decrece con SC) |

---

## 🔧 Ajustes de Dificultad

Puedes modificar estas líneas para cambiar la dificultad:

```basic
REM Velocidad inicial y mínima del scroll:
245 SP = 600 - (SC * 3): IF SP < 150 THEN SP=150

REM Probabilidad de aparición de obstáculos (1 de cada N frames):
305 IF INT(3*RND(1))=0 THEN GOSUB 850

REM Rango del zigzag de la carretera:
299 IF WP(22) < 1 THEN WP(22)=1: WD=1
300 IF WP(22) > 8 THEN WP(22)=8: WD=-1
```

---

## 👨‍💻 Créditos

- **Diseño original:** SpeedWay borrador (1988)
- **Adaptación Apple IIe:** Natxo Varona (2026)
- **Asistencia de desarrollo:** Claude (Anthropic)

---

## 📜 Licencia

Este proyecto es una adaptación con fines educativos y nostálgicos del juego original de 1988. Libre para uso personal y no comercial.

---

## 📸 Capturas de Pantalla

*La carretera hace zigzag mientras los obstáculos suben desde abajo hacia el coche fijo en la fila 9.*

![Gameplay](screenshot.png)
![Gameplay 2](screenshot-2.png)

---

> *"Escribir juegos en BASIC para Apple IIe en 2026... porque se puede."* 🍎
