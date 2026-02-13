# Unidad 2

## Bitácora de proceso de aprendizaje
### Actividad 01
El trabajo que más me gustó fue "Crab People" de **Raven Kwok**. Lo que más me gusta de esta obra es cómo logra que esas formas geométricas se muevan con una fluidez que parece biológica. Me parece increíble como, con código, el movimiento de las "patas" imite el comportamiento de crustáceos.

### Actividad 02
#### 1) ¿Cómo funciona la suma dos vectores en p5.js?
**Respuesta:** La suma de vectores en p5.js se realiza mediante el uso de la clase especializada **p5.Vector**, ya que la biblioteca no permite el uso de operadores matemáticos convencionales entre objetos. Para ejecutar esta operación, se utiliza habitualmente el método **add()**, el cual suma internamente las componentes $x$, $y$ (y $z$ si aplica) de un vector a las del otro. Se puede aplicar directamente sobre un vector existente para modificarlo, como en **v1.add(v2)**, o de forma estática para generar un tercer vector resultante sin alterar los originales.

#### 2) ¿Por qué esta línea position = position + velocity; no funciona?
**Respuesta:** No funciona debido a que **JavaScript** no soporta la sobrecarga de operadores para objetos. Dado que tanto position como velocity son instancias de vectores y no simples números, el intérprete de JavaScript no sabe cómo sumar sus estructuras internas mediante el símbolo +. Al intentar hacerlo, el lenguaje suele convertir ambos objetos a cadenas de texto, resultando en un error de ejecución o en un dato inválido en lugar de realizar la suma matemática de sus coordenadas.

### Actividad 03

### Actividad 04
#### 1) ¿Qué resultado esperas obtener en el programa anterior?
**Respuesta:** Esperaba que el vector *position* mantuviera sus valores originales (6, 9) después de ejecutar la función, asumiendo que v es solo una copia temporal.

#### 2) ¿Qué resultado obtuviste?
**Respuesta:** el resultado obtenido en la consola será primero p5.Vector Object [6, 9, 0] y luego p5.Vector Object [20, 30, 0]. Esto demuestra que los cambios realizados dentro de la función playingVector afectaron directamente a la variable global.

#### 3) Recuerda los conceptos de paso por valor y paso por referencia en programación. ☑

#### 4) ¿Qué tipo de paso se está realizando en el código?
**Respuesta:** En este código se está realizando un **paso por referencia**. En JavaScript, cuando se pasa un objeto (como un vector de p5.js) a una función, no se está enviando una copia de sus datos, sino una "dirección" o referencia a su ubicación en la memoria. Por lo tanto, tanto el nombre *position* fuera de la función como el nombre v dentro de ella apuntan exactamente al mismo objeto físico; cualquier modificación en los atributos .x o .y de uno se reflejará instantáneamente en el otro.

#### 5) ¿Qué aprendiste?
**Respuesta:** Aprendí que los vectores en p5.js son objetos mutables y que debemos ser cuidadosos al manipularlos dentro de funciones. Si la intención es modificar un vector sin alterar el original, primero se debería crear una copia usando el método copy(). Esta distinción es fundamental para evitar "efectos secundarios" o errores lógicos donde la posición o velocidad de un elemento cambia de forma inesperada en otras partes del programa.

### Actividad 05
#### 1) ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?
**Respuesta:** Este método se utiliza para calcular la longitud o magnitud real de un vector, aplicando el teorema de Pitágoras ($\sqrt{x^2 + y^2}$). Por otro lado, **magSq()** calcula la magnitud al cuadrado ($x^2 + y^2$), omitiendo el paso de la raíz cuadrada. La diferencia clave es que **magSq()** es significativamente más eficiente para el procesador, ya que la operación de raíz cuadrada es costosa en términos de cómputo; por ello, se prefiere su uso cuando solo se necesita comparar distancias o fuerzas sin requerir el valor exacto de la longitud.

#### 2) ¿Para qué sirve el método normalize()?
**Respuesta:** Este sirve para convertir un vector en un "vector unitario", lo que significa que ajusta su magnitud a exactamente 1 manteniendo su dirección original. Esto es fundamental en programación de gráficos para definir direcciones puras, como la trayectoria de una bala o la incidencia de la luz, facilitando cálculos posteriores al eliminar la influencia de la escala del vector. 

#### 3) Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?
**Respuesta:** Le diría que es una herramienta que nos dice qué tan alineados están dos vectores, permitiéndonos saber si apuntan en la misma dirección, en direcciones opuestas o si son perpendiculares.

#### 4) El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?
**Respuesta:** La diferencia entre su versión estática y la de instancia radica en el manejo de los datos: la versión de instancia, **v1.dot(v2)**, calcula el producto escalar de v1 con respecto a v2, mientras que la versión estática, **p5.Vector.dot(v1, v2)**, es una función de utilidad que recibe ambos vectores como argumentos, lo cual es útil para mantener el código más limpio o funcional sin depender de un objeto específico.

#### 5) Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.?
**Respuesta:** El resultado de este es un nuevo vector que es perpendicular al plano formado por los dos vectores originales. Su orientación sigue la "regla de la mano derecha", indicando hacia "arriba" o "abajo" de dicho plano, mientras que su magnitud es igual al área del paralelogramo que ambos vectores definen; así, cuanto más perpendiculares y largos sean los vectores originales, mayor será la magnitud del vector resultante.

#### 6) ¿Para que te puede servir el método dist()?
**Respuesta:** Esta es una función de conveniencia que sirve para calcular la distancia euclidiana entre dos puntos en el espacio, representados por vectores. Es extremadamente útil en el desarrollo de videojuegos y simulaciones interactivas para gestionar la detección de proximidad.

#### 7) ¿Para qué sirven los métodos normalize() y limit()?
**Respuesta:** Estos se utilizan para el control del movimiento: mientras que el primero fija la intensidad a uno para trabajar solo con la dirección, el segundo restringe la magnitud máxima de un vector a un valor específico, lo cual es esencial para evitar que un personaje o proyectil acelere infinitamente y se salga de control en la simulación.

### Actividad 06
#### 1) Código
```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  let v0 = createVector(50, 50); // Define el punto de origen (la "base" de todas las flechas).
  let v1 = createVector(300, 0); // Crea el vector rojo: apunta 300px a la derecha.
  let v2 = createVector(0, 300); // Crea el vector azul: apunta 300px hacia abajo.

  let amt = map(sin(frameCount * 0.02), -1, 1, 0, 1);

  let v3 = p5.Vector.lerp(v1, v2, amt); //Vector que se mueve (Morado/Mixto)

  // Cálculo del Vector Verde (el camino)
  let vVerde = p5.Vector.sub(v2, v1); // p5.Vector.sub(v2, v1) es para obtener el vector que va de la punta de v1 a v2

  // Colores
  let colorRojo = color(255, 0, 0);
  let colorAzul = color(0, 0, 255);
  let colorDinamico = lerpColor(colorRojo, colorAzul, amt);
  let colorVerde = color(0, 150, 0);

  // DIBUJO
  // Dibujamos las flechas base
  drawArrow(v0, v1, colorRojo);
  drawArrow(v0, v2, colorAzul);
  
  // Dibujamos el vector verde (su BASE es la PUNTA de v1)
  // Sumamos v0 + v1 para encontrar la ubicación exacta en el lienzo
  let baseVerde = p5.Vector.add(v0, v1);
  drawArrow(baseVerde, vVerde, colorVerde);
  
  // Dibujamos la flecha que se desplaza
  drawArrow(v0, v3, colorDinamico);
}

function drawArrow(base, vec, myColor) {
  push();
  stroke(myColor);
  strokeWeight(3);
  fill(myColor);
  translate(base.x, base.y);
  line(0, 0, vec.x, vec.y);
  rotate(vec.heading());
  let arrowSize = 7;
  translate(vec.mag() - arrowSize, 0);
  triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
  pop();
}
```
#### 2) ¿Cómo funciona lerp() y lerpColor()?
**Respuesta:** La interpolación lineal (lerp), es un concepto matemático que permite encontrar un valor intermedio entre dos puntos conocidos basándose en un porcentaje de progreso. Cuando se aplica **p5.Vector.lerp()**, el programa calcula una nueva posición que se desliza sobre la línea imaginaria (en este caso, el vector verde) que une los extremos de los vectores rojo y azul.  

Por otro lado, **lerpColor()** realiza exactamente la misma operación pero en el espacio de color; en lugar de calcular coordenadas $x$ e $y$, calcula la mezcla de los componentes Rojo, Verde y Azul (RGB). Si el porcentaje de progreso es 0.5, ambas funciones nos entregan el "punto medio": una posición situada justo a la mitad del camino y un color morado, que es la mezcla equitativa de los dos colores originales.

#### 3) ¿Cómo se dibuja una flecha usando drawArrow()?
**Respuesta:** Para dibujar una flecha, la función **drawArrow()** utiliza transformaciones de coordenadas en lugar de cálculos manuales complejos. Primero, usa **translate()** para mover el punto de origen del dibujo a la base donde debe nacer la flecha, lo que simplifica todo el proceso posterior al establecer un nuevo "punto cero". Después, dibuja una línea simple que representa el cuerpo de la flecha hasta la punta del vector. Lo más curioso ocurre con **rotate()** y **vec.heading()**: el lienzo entero gira para alinearse con la dirección del vector, permitiendo que el triángulo de la punta se dibuje siempre con las mismas coordenadas locales, sin importar si la flecha apunta hacia arriba, abajo o en diagonal. Finalmente, se usa **pop()** para "limpiar" estas transformaciones y asegurar que el siguiente dibujo no aparezca rotado o desplazado por error.

### Actividad 08


## Bitácora de aplicación 
### Actividad 09 ⋆⭒˚.⋆🔭
**Concepto: Wishing Shower** es una pieza de arte generativo que transforma un fenómeno físico ゛una lluvia de meteoros ˎˊ˗ en una experiencia interactiva sobre la esperanza y la intención. La pieza no busca solo representar la caída de cuerpos celestes, sino invitar al espectador a participar en un cielo "vivo". Evoca esa sensación infantil de mirar al cielo y sentir que, entre miles de luces, hay una que brilla específicamente para nosotros.  

El uso de Lila como base evoca tranquilidad y misterio, mientras que el Rosa vibrante al acelerar y el Amarillo al frenar sirven como indicadores visuales de la energía cinética. El Turquesa de los deseos fue elegido por su brillo etéreo, separándose cromáticamente de la paleta cálida para resaltar su importancia.

La base del movimiento es una aceleración constante por gravedad, aplicada como un vector inclinado hacia la esquina inferior derecha. Esto genera un flujo natural y rítmico, donde cada estrella aumenta su velocidad de forma progresiva desde que nace, simulando la caída libre de un meteoro en la atmósfera. 

Para la interacción, utilicé aceleración tangencial manual vinculada a las teclas. Al presionar la derecha, aplico una fuerza a favor del movimiento actual que aumenta la magnitud de la velocidad, permitiendo que las estrellas alcancen un color rosa vibrante. Al presionar la izquierda, aplico una fuerza de oposición que reduce la velocidad gradualmente, activando un tono amarillo que evoca calma y resistencia.  

Finalmente, implementé una aceleración de evento crítico para la función del deseo (tecla W). Al activarse, una estrella seleccionada recibe un impulso masivo que ignora las reglas de fricción normales. Esta aceleración extrema dispara la velocidad de la partícula hasta que abandona el lienzo, simbolizando visualmente un anhelo que cobra fuerza propia y trasciende el entorno común.  

**Código:**
```js
let stars = [];
let maxStars = 150; 
let interactionState = 0; 

function setup() {
  createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
  for (let i = 0; i < maxStars; i++) {
    stars.push(new Star());
  }
}

function draw() {
  background(10, 15, 45, 45); 

  if (random(1) < 0.2) {
    let inactiveStar = stars.find(s => !s.active);
    if (inactiveStar) inactiveStar.activate();
  }

  for (let star of stars) {
    if (star.active) {
      star.update();
      star.checkEdges();
      star.show();
    }
  }
}

function keyPressed() {
  if (keyCode === RIGHT_ARROW) interactionState = 1; 
  if (keyCode === LEFT_ARROW) interactionState = -1; 
  
  if (key === 'w' || key === 'W') {
    let currentVisible = stars.filter(s => s.active && !s.isWish);
    if (currentVisible.length > 0) {
      let chosen = random(currentVisible);
      chosen.isWish = true; 
    }
  }
}

function keyReleased() {
  if (keyCode === RIGHT_ARROW || keyCode === LEFT_ARROW) {
    interactionState = 0;
  }
}

class Star {
  constructor() {
    this.active = false;
    this.isWish = false;
    this.pos = createVector(0, 0);
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    this.currentColor = color(180, 140, 255);
  }

  activate() {
    this.active = true;
    this.isWish = false;
    this.pos = createVector(random(-100, width * 0.4), random(-100, height * 0.1));
    this.vel = createVector(random(1, 2.5), random(1, 2.5));
    this.acc = createVector(0, 0);
    this.size = random(5, 10);
    this.baseMaxSpeed = random(3, 6); 
    this.maxSpeed = this.baseMaxSpeed;
    this.angle = random(TWO_PI);
    this.currentColor = color(180, 140, 255);
  }

  update() {
    let gravity = createVector(0.015, 0.03);
    this.acc.add(gravity);

    if (this.isWish) {
      let boost = this.vel.copy().normalize().mult(1.2); 
      this.acc.add(boost);
      this.maxSpeed = 30; 
    } else {
      if (interactionState === 1) {
        // --- ACELERACIÓN POTENTE ---
        let push = this.vel.copy().normalize().mult(0.3);
        this.acc.add(push);
        this.maxSpeed = 20; // Permite ir más rápido mientras aceleras
      } else if (interactionState === -1) {
        // Frenado suave
        let brake = this.vel.copy().normalize().mult(-0.08);
        this.acc.add(brake);
        this.maxSpeed = this.baseMaxSpeed;
      } else {
        this.maxSpeed = this.baseMaxSpeed;
      }
    }

    this.vel.add(this.acc);
    this.vel.limit(this.maxSpeed);
    this.pos.add(this.vel);
    this.acc.mult(0); 
    
    this.angle += this.vel.mag() * 0.04;
  }

  checkEdges() {
    if (this.pos.x > width + 100 || this.pos.y > height + 100) {
      this.active = false;
      this.isWish = false;
    }
  }

  show() {
    let lila = color(180, 140, 255);
    let rosa = color(255, 80, 180);
    let amarillo = color(255, 255, 100);
    let turquesa = color(0, 255, 240);

    let target = lila;
    if (this.isWish) target = turquesa;
    else if (interactionState === 1) target = rosa;
    else if (interactionState === -1) target = amarillo;

    this.currentColor = lerpColor(this.currentColor, target, 0.1);

    push();
    translate(this.pos.x, this.pos.y);
    
    stroke(this.currentColor);
    // La estela crece con la velocidad
    strokeWeight(this.isWish ? this.size * 0.7 : this.size * 0.4);
    let tailLen = this.isWish ? -20 : -5;
    let t = this.vel.copy().normalize().mult(tailLen * (this.vel.mag() * 0.3));
    line(0, 0, t.x, t.y);

    rotate(this.angle);
    noStroke();
    fill(this.currentColor);
    let s = this.isWish ? this.size * 1.6 : this.size;
    rect(0, 0, s, s);
    
    fill(255, 250);
    rect(0, 0, s * 0.4, s * 0.4);
    pop();
  }
}
```

**Enlace:** https://editor.p5js.org/Hannanah06/full/Gd10TKHsi  

<img width="1175" height="783" alt="Captura de pantalla 2026-02-13 023945" src="https://github.com/user-attachments/assets/c2983afe-b3fe-4331-a925-3c8cc02335df" />



## Bitácora de reflexión
### Actividad 10 ⋆.🔬⌬ ˚ 🦠⋆
**Concepto:** Esta pieza llamada **Synthetic Affinities** presenta un ecosistema digital de partículas divididas en tres "especies" de colores. Cada una posee una carga de afinidad —atracción o repulsión— hacia las demás, dictada por una matriz de ADN digital. Este sistema no busca la animación predecible, sino la emergencia: la aparición espontánea de estructuras orgánicas, colonias y patrones de persecución que imitan la danza de microorganismos bajo un microscopio.  

La estética de la obra está inspirada en los estudios de vida artificial de *Jeffrey Ventrella* y rinde homenaje a la visión de *Jared Tarbell*, donde el tiempo se vuelve un pincel. En lugar de limpiar el lienzo en cada cuadro, las partículas dejan rastros sutiles de su trayectoria, construyendo una red de filamentos que evocan tejidos biológicos

La interacción humana es el motor que altera la física de este universo. El usuario actúa como una fuerza de la naturaleza: al presionar la barra espaciadora, se produce una mutación instantánea en las leyes de afinidad, forzando a las partículas a reconfigurar sus jerarquías sociales. 
Al mover el cursor, el espectador manipula la temporalidad del sistema: el movimiento hacia la derecha ralentiza la existencia, permitiendo una contemplación analítica de las uniones químicas, mientras que el movimiento hacia la izquierda acelera el ritmo vital, provocando colisiones dinámicas.  

Finalmente, el click representa un evento de convergencia masiva, un punto de gravedad absoluta que obliga a todas las especies a colapsar en un núcleo denso y vibrante. Al liberar la presión, el sistema se "desenreda" de nuevo, revelando cómo las fuerzas de amor y odio matemático vuelven a separar la materia en nuevas agrupaciones.  

**Código:**
```js
let particles = [];
let numParticles = 200;
let matrix = [];
let speedMultiplier = 1; // Factor de velocidad global

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(10, 15, 30);
  randomizeRules();
  for (let i = 0; i < numParticles; i++) {
    particles.push(new Particle(random(width), random(height), i % 3));
  }
}

function randomizeRules() {
  for (let i = 0; i < 3; i++) {
    matrix[i] = [];
    for (let j = 0; j < 3; j++) {
      let force = random(0.4, 1.2); // Fuerzas siempre notables
      if (random() > 0.5) force *= -1; 
      matrix[i][j] = force;
    }
  }
}

function draw() {
  background(10, 15, 30, 30); 

  // LÓGICA DE DIRECCIÓN DEL MOUSE
  // Si la posición actual es mayor a la anterior, va a la derecha
  if (mouseX > pmouseX) {
    speedMultiplier = lerp(speedMultiplier, 0.4, 0.1); // Lento
  } else if (mouseX < pmouseX) {
    speedMultiplier = lerp(speedMultiplier, 2.5, 0.1); // Rápido
  }

  for (let p of particles) {
    p.applySocialPhysics(particles);
    p.interact(); 
    p.update();
    p.display();
  }
}

function keyPressed() {
  if (key === ' ') {
    background(10, 15, 30); 
    randomizeRules();
  }
}

class Particle {
  constructor(x, y, type) {
    this.pos = createVector(x, y);
    this.vel = createVector(random(-1, 1), random(-1, 1));
    this.acc = createVector(0, 0);
    this.type = type;
    this.maxSpeed = 4;
  }

  applySocialPhysics(others) {
    let steer = createVector(0, 0);
    let count = 0;
    for (let other of others) {
      if (other !== this) {
        let dx = other.pos.x - this.pos.x;
        let dy = other.pos.y - this.pos.y;
        let d2 = dx * dx + dy * dy;

        if (d2 > 0 && d2 < 7000 && count < 20) {
          let d = sqrt(d2);
          let force = createVector(dx / d, dy / d);
          
          if (d < 12) { // Repulsión mínima para que no se peguen literal
            force.mult(-1.5);
          } else {
            force.mult(matrix[this.type][other.type]);
          }
          steer.add(force);
          count++;
        }
      }
    }
    this.acc.add(steer);
  }

  interact() {
    if (mouseIsPressed) {
      // CLICK: ATRACCIÓN MASIVA
      let attraction = createVector(mouseX - this.pos.x, mouseY - this.pos.y);
      attraction.setMag(2.5); // Fuerza de imán potente
      this.acc.add(attraction);
      this.vel.mult(0.85); // Frena la inercia para que se queden en el centro
    }
  }

  update() {
    this.vel.add(this.acc);
    
    // Aplicamos el multiplicador de velocidad según la dirección del mouse
    let finalMaxSpeed = this.maxSpeed * speedMultiplier;
    this.vel.limit(finalMaxSpeed);
    
    this.pos.add(this.vel);
    this.vel.mult(0.94); 
    this.acc.mult(0);
    
    if (this.pos.x > width) this.pos.x = 0;
    if (this.pos.x < 0) this.pos.x = width;
    if (this.pos.y > height) this.pos.y = 0;
    if (this.pos.y < 0) this.pos.y = height;
  }

  display() {
    let colors = [color(0, 255, 255), color(255, 50, 150), color(255, 255, 100)];
    stroke(colors[this.type]);
    strokeWeight(3);
    point(this.pos.x, this.pos.y);
  }
}
```

**Enlace:** https://editor.p5js.org/Hannanah06/full/gB5_dqaWw  

<img width="1435" height="860" alt="Captura de pantalla 2026-02-13 145310" src="https://github.com/user-attachments/assets/beeab94b-252a-4d73-a593-188f46eac7e7" />








