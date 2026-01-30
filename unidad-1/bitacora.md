# Unidad 1

## Bitácora de proceso de aprendizaje
### Actividad 01
#### Piensa y describe en una sola frase y en tus propias palabras cómo la aleatoriedad influye en el arte generativo.  
  **Respuesta:** De acuerdo al video del canal [Sotheby's](https://youtu.be/d2LC6Am9bZI?si=TccV35wFJpt09Kec), la aleatoriedad en el arte generativo hace que la obra en sí no sea un resultado fijo, sino un proceso. Esta permite generar variación y singularidad, cada ejecución es única y esa es la escencia de esta forma de creación artística.

### Actividad 02
#### ¿Qué espero que suceda?
Modifiqué los valores del choice (todos en cero), esperando que se moviera por el centro.
#### ¿Qué sucedió?
Empezó a hacer su recorrido hacia arriba y un poco hacia la derecha.   

   No funcionó. Luego de ver bien el código, me di cuenta de que funcionaba con if/else if/else, y esto es en orden. Dejé el random en 4, por lo que se escogían valores entre 0, 1, 2 y 3; si en el primer choice el valor era igual a cero, entonces se ejecutaba el if, moviéndose en x++ (derecha). Como en los otros dos choice siguientes también debían ser iguales a cero, no se ejecutaban porque el primero ya lo había hecho. Y como ninguna de las dos condiciones anteriores se cumplió, se ejecutó el else, haciendo que se moviera en y-- (arriba).

### Actividad 03
#### En tus propias palabras cuál es la diferencia entre una distribución uniforme y una no uniforme de números aleatorios.
**Respuesta:** En una distribución uniforme, todos los valores posibles tienen la misma probabilidad de salir y se ve repartido "parejo", pero también caótico. En cambio, en la no uniforme, algunos valores tienen más probabilidad que otros; en esta la información se ve mucho más en el centro y el patrón es más "natural".

### Actividad 04
### Actividad 05
### Actividad 06

## Bitácora de aplicación 
### Actividad 07 ⋆.˚🦋༘⋆
**Concepto: Garden Fairies** es una obra generativa interactiva donde el usuario crea vida dando clic. Al tocar el lienzo, nacen hadas autónomas que recorren el espacio dejando un rastro de flores, transformando el vacío en un "campo de flores" vibrante en tiempo real.

El movimiento fluido de las hadas se logra con Ruido Perlin, que permite un desplazamiento orgánico y suave en lugar de saltos caóticos. Esto imita el vuelo natural de insecto, haciendo que la trayectoria se sienta biológica y elegante.

La diversidad de las flores utiliza la lógica de Lévy Flight para gestionar la probabilidad: las flores comunes aparecen con frecuencia, mientras que una flor azul especial surge como un "evento raro". Finalmente, el brillo del hada se genera con una Distribución Uniforme, que reparte partículas de luz exactamente en su contorno mediante trigonometría, creando un "aura mágica" equilibrada.  

**Código:**
```
let grupoHadas = [];

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(140, 180, 80); 
}

function draw() {
  background(140, 180, 80, 15); 

  for (let hada of grupoHadas) {
    hada.actualizar();
    hada.mostrar();
  }
}

function mousePressed() {
  grupoHadas.push(new Hada(mouseX, mouseY));
}

class Hada {
  constructor(x, y) {
    this.origenX = x;
    this.origenY = y;
    this.pos = createVector(x, y);
    
    this.tX = random(10000);
    this.tY = random(10000, 20000);
    
    // CAPTURA DE OFFSET: Esto asegura que el primer frame sea (0,0)
    this.startNoiseX = noise(this.tX);
    this.startNoiseY = noise(this.tY);
    
    this.floresHada = [];
    this.particulasHada = [];
  }

  actualizar() {
    // Restamos el valor inicial para que el primer valor de 'offsetX' sea 0
    let currentNoiseX = noise(this.tX) - this.startNoiseX;
    let currentNoiseY = noise(this.tY) - this.startNoiseY;

    // Mapeamos el movimiento relativo (ahora sí centrado en el clic)
    let offsetX = map(currentNoiseX, -0.5, 0.5, -200, 200);
    let offsetY = map(currentNoiseY, -0.5, 0.5, -200, 200);
    
    this.pos.x = this.origenX + offsetX;
    this.pos.y = this.origenY + offsetY;
    
    this.tX += 0.005;
    this.tY += 0.005;

    // Lógica de flores (Lévy Flight)
    if (frameCount % 6 === 0) {
      let r = random(100);
      let tipo = (r < 2) ? 4 : (r < 35) ? 1 : (r < 70) ? 2 : 3;
      this.floresHada.push(new Flor(this.pos.x, this.pos.y, tipo));
    }

    // Partículas (Contorno)
    if (this.particulasHada.length < 10) {
      this.particulasHada.push(new Particula(this.pos.x, this.pos.y));
    }
    
    for (let i = this.particulasHada.length - 1; i >= 0; i--) {
      this.particulasHada[i].update();
      if (this.particulasHada[i].isDead()) this.particulasHada.splice(i, 1);
    }
  }

  mostrar() {
    for (let f of this.floresHada) f.show();
    for (let p of this.particulasHada) p.show();
    
    fill(255, 255, 100);
    noStroke();
    ellipse(this.pos.x, this.pos.y, 8, 8);
  }
}

class Flor {
  constructor(x, y, tipo) {
    this.x = x; this.y = y; this.tipo = tipo; this.size = random(6, 12);
  }
  show() {
    noStroke();
    if (this.tipo === 1) fill(255, 180, 210, 200); 
    else if (this.tipo === 2) fill(255, 200, 100, 200); 
    else if (this.tipo === 3) fill(180, 150, 255, 200); 
    
    if (this.tipo === 4) {
      fill(80, 200, 255); 
      rectMode(CENTER);
      rect(this.x, this.y, this.size * 1.2, this.size * 1.2);
    } else {
      ellipse(this.x, this.y, this.size);
    }
  }
}

class Particula {
  constructor(hx, hy) {
    let angulo = random(TWO_PI);
    let radioBorde = 5; 
    this.px = hx + cos(angulo) * radioBorde;
    this.py = hy + sin(angulo) * radioBorde;
    this.vx = cos(angulo) * random(0.3, 0.8);
    this.vy = sin(angulo) * random(0.3, 0.8);
    this.vida = 255;
  }
  update() {
    this.px += this.vx;
    this.py += this.vy;
    this.vida -= 12;
  }
  show() {
    stroke(255, 255, 180, this.vida);
    strokeWeight(2);
    point(this.px, this.py);
  }
  isDead() { return this.vida <= 0; }
}
```
**Enlace:** https://editor.p5js.org/Hannanah06/full/cOBrlvLKU  

<img width="1019" height="729" alt="Captura de pantalla 2026-01-30 003448" src="https://github.com/user-attachments/assets/75dbb72a-a43a-44fb-a745-ab820c43206c" />

## Bitácora de reflexión

