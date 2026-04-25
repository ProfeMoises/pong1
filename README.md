# PONG ARCADE 🏓・El clásico de la era dorada

Bienvenido a **PONG ARCADE**, una recreación moderna y fiel del primer videojuego de competición que cautivó al mundo en los años 70. Este juego ha sido desarrollado íntegramente con HTML5 Canvas, CSS y JavaScript puro, sin librerías externas. Revive la emoción del tenis de mesa virtual contra una inteligencia artificial (IA) fluida y desafiante.

![Pong Canvas Demo](https://via.placeholder.com/800x400?text=PONG+ARCADE+EN+ACCION)  
*(La imagen es ilustrativa; el juego se ejecuta directamente en tu navegador)*

---

## 📜 Historia de Pong

**Pong** fue creado por **Allan Alcorn** como un ejercicio de entrenamiento para **Atari** en 1972. Nolan Bushnell, cofundador de Atari, pidió a Alcorn que desarrollara un juego sencillo que pudiera instalarse en máquinas recreativas. Inspirado en el tenis de mesa, el resultado fue un éxito inmediato: la primera máquina arcade de Pong instalada en un bar de Sunnyvale (California) dejó de funcionar al poco tiempo… ¡porque se había llenado de monedas!

Pong popularizó el concepto de los videojuegos como entretenimiento masivo y sentó las bases de la industria. Su mecánica minimalista (dos paletas, una pelota y un marcador) es hoy un icono atemporal.

Esta versión rinde homenaje a ese espíritu, añadiendo detalles visuales retro-futuristas y un modo para un jugador con paleta controlada por el mouse.

---

## 🎮 Cómo jugar – Instrucciones completas

### Objetivo del juego
Gana puntos haciendo que la pelota toque el borde derecho de la pantalla (zona de la IA) mientras evitas que toque tu borde izquierdo. El primero en acumular la mayor cantidad de puntos… ¡el juego no tiene límite! Juega hasta que quieras reiniciar.

### Controles
- **Paleta izquierda (Jugador):** se controla con el **movimiento del mouse** dentro del área del canvas. Mueve el cursor hacia arriba o abajo y la paleta seguirá tu posición.
- **Paleta derecha (IA):** se controla automáticamente mediante una inteligencia artificial que persigue la pelota con suavidad y precisión ajustable.

> ⚠️ **Nota:** El cursor del mouse se oculta automáticamente cuando está sobre el canvas para no molestar la visión del juego.

### Mecánicas y reglas
1. **Servicio**: después de cada punto, la pelota se pausa brevemente y se lanza hacia el lado contrario al último anotador (si anotó el jugador, la siguiente bola va hacia la IA, y viceversa). El saque inicial es aleatorio.
2. **Rebote con efecto angular**: cuando la pelota golpea la paleta, el ángulo de rebote depende de **dónde impacte**:
   - Si golpea cerca del centro → rebote casi recto.
   - Si golpea cerca del borde superior/inferior → la pelota sale con un ángulo más pronunciado.
3. **Incremento de velocidad**: cada vez que la pelota impacta contra una paleta, su velocidad **aumenta un 2%** (hasta un máximo de 9.5 píxeles/frame). ¡El ritmo se acelera y la emoción crece!
4. **Puntuación**:
   - **Jugador anota** → la IA no logra devolver la bola y esta cruza el borde derecho.
   - **IA anota** → el jugador falla la devolución y la bola cruza el borde izquierdo.
5. **Límites superior e inferior**: la pelota rebota en los bordes superior e inferior de la pantalla con la misma física angular.

### ¿Qué significa "esperando saque"?
Tras cada punto, la pelota se congela en el centro, aparece un mensaje **"SERVIDOR"** y tras menos de un segundo se lanza el nuevo servicio. Es la pausa natural del juego.

### Botón de reinicio
El botón **⟳ REINICIAR** resetea completamente el marcador (jugador 0 - IA 0), recoloca las paletas en el centro y lanza una nueva pelota en movimiento.

---

## 🧠 Información técnica y detalles interesantes

### Tecnologías utilizadas
- **HTML5 Canvas**: renderizado de gráficos 2D.
- **CSS3**: diseño neón, bordes brillantes y sombras.
- **JavaScript (ES6+)**: lógica del juego, físicas, IA, detección de colisiones y bucle de animación con `requestAnimationFrame`.

### Características especiales de esta versión
| Característica | Descripción |
|----------------|-------------|
| **IA adaptativa** | La paleta derecha se mueve con velocidad limitada, evitando que sea perfecta (para que el jugador tenga oportunidades). Su velocidad es de 5.4 píxeles/frame, similar a la del jugador. |
| **Efecto angular realista** | El factor de impacto se calcula en función de la diferencia entre el centro de la paleta y el punto de colisión, produciendo tiros cruzados. |
| **Aceleración progresiva** | La pelota aumenta su velocidad gradualmente, alargando la emoción y premiando los rallies largos. |
| **Estética retro-futurista** | Fondo oscuro con rejilla tenue, línea central discontinua, círculo central, sombras neón y una paleta con doble acabado brillante. |
| **Marcadores integrados** | Tanto en el panel superior como dentro del canvas (con semitransparencias) para seguir la partida fácilmente. |
| **Sin dependencias externas** | Todo el código está autocontenido – funciona sin conexión a internet una vez cargado. |

### Física del movimiento
La velocidad de la bola se normaliza tras cada colisión para mantener la coherencia. El ángulo de rebote se calcula así:
