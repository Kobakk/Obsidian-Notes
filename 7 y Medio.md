#javascript 
```javascript
function pedirCarta() {
  let cartas = [1, 2, 3, 4, 5, 6, 7, 0.5, 0.5, 0.5];
  let indice = Math.floor(Math.random() * cartas.length);
  return cartas[indice];
}
function numeroCartas() {
  return Math.floor(Math.random() * 3) + 2;
}
function imprimirCarta(jugador, carta, puntos) {
  addElement("p", `${jugador} - Carta: ${carta} puntos. Total: ${puntos}`);
  //document.write(`<p>${jugador} - Carta: ${carta} puntos.</p>`);
}
function partidaJugador2() {
  let cantidadCartas = numeroCartas();
  let puntos = 0;
  //document.write(`<p>J2 - Número de Cartas: ${cantidadCartas} cartas.</p>`);
  for (let index = 0; index < cantidadCartas; index++) {
    let carta = pedirCarta();
    puntos += carta;
    imprimirCarta("J2", carta, puntos);
  }
  return puntos;
}
function addElement(type, content) {
  const principal = document.getElementById("principal");
  const elementHTML = document.createElement(type);
  elementHTML.innerHTML = content;
  principal.appendChild(elementHTML);
}
function imprimirPuntuacion(jugador, puntos) {
  addElement("h2", `${jugador} - Total: ${puntos} puntos.`);
  //document.write(`<h2>Puntuación ${jugador}.</h2>`);
  if (puntos > tope) {
    //alert(`Tienes ${puntuacion}. Has perdido `);
    //document.write(`<h3>Tienes ${puntos}. Te has pasado.</h3>`);
    addElement("h3", `Tienes ${puntos}. Te has pasado.`);
  } else if (puntos === tope) {
    //alert(`Eres el mejor: ${puntuacion} puntos.`);
    //document.write(`<h3>Eres el mejor: ${puntos} puntos.</h3>`);
    addElement("h3", `Eres el mejor: ${puntos} puntos.`);
  } else {
    //alert(`Tu puntuación es: ${puntuacion} puntos.`);
    //document.write(`<h3>Tu puntuación es: ${puntos} puntos.</h3>`);
    addElement("h3", `Tu puntuación es: ${puntos} puntos.`);
  }
}
let puntuacionJugador1 = 0;
let puntuacionJugador2 = 0;
const tope = 7.5;
let carta;
let continuar = true;
let imprimir = true;
function pedirCartaJ1() {
  if (continuar) {
    carta = pedirCarta();
    puntuacionJugador1 += carta;
    imprimirCarta("J1", carta, puntuacionJugador1);
  }
  if (puntuacionJugador1 > tope) {
    continuar = false;
    resultados();
  }
}
function resultados() {
  if (imprimir) {
    puntuacionJugador2 = partidaJugador2();
    imprimirPuntuacion("J1", puntuacionJugador1);
    imprimirPuntuacion("J2", puntuacionJugador2);
    if (puntuacionJugador1 > tope && puntuacionJugador2 > tope) {
      addElement("h2", `Pierden los dos jugadores.`);
    } else if (puntuacionJugador1 <= tope && puntuacionJugador2 > tope) {
      addElement("h2", `Gana el jugador 1.`);
    } else if (puntuacionJugador1 > tope && puntuacionJugador2 <= tope) {
      addElement("h2", `Gana el jugador 2.`);
    } else {
      if (puntuacionJugador1 > puntuacionJugador2) {
        addElement("h2", `Gana el jugador 1.`);
      } else if (puntuacionJugador1 < puntuacionJugador2) {
        addElement("h2", `Gana el jugador 2.`);
      } else {
        addElement("h2", `Empate.`);
      }
    }
    imprimir = false;
  }
}
```
Parte del html:
```html
 <body>
    <h1>7 y 1/2</h1>
    <button onclick="pedirCartaJ1();">Continuar</button>
    <button onclick="continuar = false; resultados()">Terminar</button>
    <div id="principal"></div>
    <script src="./app.js"></script>
  </body>
```

### Lógica
