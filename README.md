<div align="center">

# 🔵🔴 Trivia Cuerva · San Lorenzo de Almagro

**Juego de preguntas y respuestas sobre el Ciclón: girá la ruleta, respondé y escalá de la reserva hasta ser Campeón del Mundo.**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?logo=javascript&logoColor=black)
![Web Audio API](https://img.shields.io/badge/Web_Audio_API-sonido_procedural-8A2BE2)
![Canvas API](https://img.shields.io/badge/Canvas_API-diploma_PNG-0C2C6B)
![Sin dependencias](https://img.shields.io/badge/dependencias-0-2FAA55)

[**Jugar ahora**](https://gastonpaez.github.io/Trivia_SL/) · [Reportar un problema](https://github.com/GastonPaez/Trivia_SL/issues)

</div>

---

## 📌 Descripción

**Trivia Cuerva** es un juego web de trivia dedicado al Club Atlético San Lorenzo de Almagro. El jugador ingresa su nombre, gira una ruleta que sortea la temática de cada pregunta y avanza por un escalafón de nueve niveles inspirado en la carrera de un futbolista, desde *Equipo de reserva* hasta *Campeón del Mundo*.

Todo el juego vive en **un único archivo HTML**, sin frameworks, librerías ni proceso de build. La música, los efectos de sonido, los íconos, el escudo y el diploma descargable se generan con código: no hay archivos de audio ni imágenes externas.

---

## 🎮 Cómo se juega

1. **Ingresá tu nombre de hincha** y tocá *¡A la cancha!*
2. **Girá la Ruleta del Ciclón** para sortear la temática: **Resultados**, **Jugadores** o **Historia**.
3. **Respondé la pregunta** de opción múltiple. Cada acierto te sube un nivel en el escalafón.
4. Tenés **dos vidas** (tolerancia de un error) y un **salvataje 50/50** por partida, que elimina dos opciones incorrectas.
5. Llegá a las **9 respuestas correctas** para consagrarte *Campeón del Mundo*.
6. Al terminar, **descargá tu diploma cuervo** en PNG con tu nombre, el nivel alcanzado y tus estadísticas.

### El escalafón

| Nivel | Título |
|:---:|---|
| 1 | Equipo de reserva |
| 2 | Suplente en primera |
| 3 | Titular en primera |
| 4 | Finalista de liga |
| 5 | Campeón de liga |
| 6 | Campeón Copa Argentina |
| 7 | Campeón Sudamericana |
| 8 | Campeón Libertadores |
| 9 | 🏆 Campeón del Mundo |

---

## ✨ Características

- **Ruleta animada** construida con `conic-gradient` y transiciones CSS, con un cálculo de rotación que garantiza que el puntero se detenga dentro del sector sorteado.
- **Dificultad progresiva:** el banco de preguntas está clasificado por temática y por dificultad del 1 al 9. En cada nivel se elige la pregunta cuya dificultad se acerca más al objetivo, con desempate aleatorio.
- **Sin preguntas repetidas** dentro de una partida, con estrategias de respaldo si se agota una temática.
- **Opciones mezcladas en cada pregunta** con el algoritmo Fisher-Yates, de modo que la respuesta correcta nunca está en la misma posición.
- **Banda sonora de tango y murga generada en tiempo real** con la Web Audio API: progresión de acordes en La menor, bajo y bombo sintetizados, con botón para silenciarla.
- **Efectos de sonido** para aciertos, errores, giro de ruleta, subida de nivel, victoria y derrota.
- **Diploma descargable** dibujado con la Canvas API y exportado como imagen PNG.
- **Identidad visual azulgrana** con tipografías de inspiración porteña, textura que evoca el fileteado, escudo e íconos en SVG inline, animación de subida de nivel y confeti al ganar.
- **Diseño responsive** con `clamp()` y unidades relativas, pensado para celular y escritorio.

---

## 🧠 Habilidades

**JavaScript sin frameworks.** Arquitectura de una aplicación de varias pantallas (inicio, ruleta, pregunta y resultado) con un objeto de estado central, encapsulada en una IIFE con `"use strict"` para no contaminar el ámbito global.

**Lógica de juego y algoritmos.** Selección adaptativa de preguntas por cercanía de dificultad, mezcla aleatoria con Fisher-Yates, control de vidas y comodines, y cálculo trigonométrico para ubicar los íconos de la ruleta y alinear el giro con el sector sorteado.

**Audio procedural.** Uso de osciladores, envolventes de ganancia, filtros pasa-bajos y un *scheduler* con anticipación para mantener el tempo estable, respetando la política de los navegadores que exige una interacción del usuario antes de reproducir sonido.

**Gráficos en el navegador.** Generación de imágenes con Canvas 2D (degradados, texturas, marcos y texto) y exportación a PNG sin servidor.

**Diseño de interfaz.** CSS moderno con variables personalizadas, `conic-gradient`, pseudo-elementos, animaciones con `keyframes` y `cubic-bezier`, y tipografía fluida.

**Contenido y diseño de juego.** Banco de 27 preguntas balanceado en tres temáticas y nueve niveles de dificultad, con una narrativa de progresión ligada a la identidad del club.

---

## 🛠️ Stack tecnológico

| Área | Tecnología |
|---|---|
| Estructura | HTML5 semántico, SVG inline |
| Estilos | CSS3 (variables, `conic-gradient`, animaciones), Google Fonts (Yeseva One, Bebas Neue, Oswald, Pacifico) |
| Lógica | JavaScript ES6+ vanilla |
| Sonido | Web Audio API |
| Gráficos | Canvas API |
| Hosting | GitHub Pages |

---

## 📂 Estructura del proyecto

```
Trivia_SL/
├── index.html   # Juego completo: estilos, lógica, preguntas, audio y diploma
├── A.html       # Variante anterior con paleta dorada
└── README.md
```

---

> La música arranca con el primer clic en la página, porque los navegadores bloquean el audio automático hasta que el usuario interactúa.

---

## ➕ Agregar preguntas

Las preguntas se definen en el arreglo `BANK` dentro de `index.html`. Cada una indica la temática (`t`), la dificultad del 1 al 9 (`d`), el enunciado (`q`) y las opciones (`o`). **La primera opción siempre es la correcta**; el juego las mezcla al mostrarlas.

```js
{ t: "HIS", d: 1, q: "¿En qué año fue fundado San Lorenzo de Almagro?",
  o: ["1908", "1901", "1910", "1912"] }
```

Temáticas disponibles: `RES` (Resultados), `JUG` (Jugadores) e `HIS` (Historia). Para mantener el balance, conviene que cada temática tenga al menos una pregunta por nivel de dificultad.

---

## 👤 Autor

**Gastón Páez**

[![GitHub](https://img.shields.io/badge/GitHub-GastonPaez-181717?logo=github)](https://github.com/GastonPaez)

<div align="center">
💙❤️
</div>
