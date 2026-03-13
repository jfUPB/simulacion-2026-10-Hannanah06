# Unidad 4

## Bitácora de proceso de aprendizaje
### Actividad 01
Lo que más me atrapó de “*The Awesome Machinery Of Nature: We are all connected*” fue cómo Memo Akten transforma reglas matemáticas en algo que se siente totalmente vivo.  
**-Formas y Colores:** Me encantó cómo los patrones visuales crean una red donde todo parece estar conectado. No se siente como código rígido, sino como un sistema orgánico y fluido.  
**-Sonido:** La sincronía entre el movimiento y el audio hace que la simulación deje de ser algo que solo "ves" para convertirse en una experiencia que "sientes".

### Actividad 02
#### Análisis: Manejo de Ángulos
✿ **¿Qué está pasando en esta simulación? ¿Cuál es la interacción?**  
Lo que veo en el canvas es una figura que gira sobre su centro, de forma contínua. El código usa la posición del cursor (*mouseX*) para controlar qué tanto aumenta el ángulo en cada frame, haciendo que la animación reaccione a lo que yo hago.  

✿ **Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto?**  
Sé que p5.js pone el punto (0,0) en la esquina de arriba a la izquierda. Si intentara rotar algo ahí, la figura giraría "anclada" a esa esquina y se saldría de la pantalla.  

✿ **Cuál es la relación entre el sistema de coordenadas y la función *rotate()***  
Algo clave que aprendí es que *rotate()* no hace girar al objeto, sino a todo el sistema de coordenadas. Es como si el "papel" donde estoy dibujando fuera el que da la vuelta. Por eso el orden importa muchísimo:

Primero muevo el papel al centro (*translate*). Luego giro el papel con el ángulo que quiero (*rotate*). Al final, dibujo la figura en (0,0). Como el papel ya está movido y girado, la figura aparece en el centro y con la inclinación correcta.  

✿ **Observa que al dibujar los elementos gráficos parece que se está dibujando en la posición (0, 0) del sistema de coordenadas. ¿Por qué crees que se hace esto?**  
Me di cuenta de que dibujar alrededor del (0,0) facilita muchísimo el diseño. Al poner los círculos en (50, 0) y (-50, 0), se crea una figura simétrica que tiene su centro justo en el origen. Dibujar en el origen permite olvidar la posición global y concentrarse solo en la forma del objeto.  

✿ **¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan?**  
Aunque el código de *circle(50, 0, 16)* nunca cambia, lo que sí cambia en cada frame es el estado del lienzo antes de dibujar. Es como si se tuviera un sello con la forma de la línea y los círculos:

En cada frame, el programa primero mueve y gira el papel un poquito más que en el anterior (gracias a que la variable del ángulo aumenta). Luego, simplemente se pone el "sello" siempre en el mismo lugar: el (0,0). Como el papel está cada vez más inclinado cuando pongo el sello, al final se ve la animación de rotación.  

#### Análisis: Orientación según el Movimiento (Motion 101)
✿ **Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?**
El marco Motion 101 se encarga de que el objeto se mueva con física real, y nosotros simplemente usamos la dirección de ese movimiento para inclinar el "papel" antes de dibujar la figura. Así parece que el objeto realmente sabe hacia dónde se dirige. Lo que hace, en este caso, es: calcular el ángulo con *velocity.heading()*, rotación dinámica con *rotate(angle)* y dibujar en el origen (0,0).

✿ **Observa detenidamente este fragmento de código de la simulación. ¿Qué hace la función heading()?**
El *heading()* es como una brújula para los vectores. Toma el vector de velocidad (que tiene un componente en $x$ y otro en $y$) y calcula el ángulo exacto hacia el que está apuntando, por lo que no se hace trigonometría manual; la función devuelve el ángulo en radianes para que p5.js sepa exactamente hacia dónde se está "lanzando" el objeto.  

✿ **¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.**  
Tras experimentar un poco, me di cuenta de que son como un botón de "guardar" y "volver".

*push()*: Guarda el estado actual del lienzo (su posición, rotación y estilos).  
*pop()*: Restaura el estado que se guardó antes.  

✿ **¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.**  
p5.js dibuja los rectángulos desde la esquina superior izquierda.  
**Mi experimento:** Si dejo el modo por defecto, al rotar el rectángulo, este parece "cojear" porque gira alrededor de su esquina. Al activar *rectMode(CENTER)*, el punto (0,0) queda justo en el centro del rectángulo. Así, cuando el código dice rect(0, 0, 30, 10), el objeto queda perfectamente balanceado sobre su eje.  

✿ **¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad?**  
**El Vector:** La velocidad es una flecha que va desde la posición actual hacia donde se mueve el objeto. El ángulo que forma esa flecha con el eje horizontal es lo que nos da *heading()*.

**Traslación:** Primero "llevamos" todo nuestro sistema de coordenadas a *this.position.x* y *this.position.y*. Ahora nuestro (0,0) es el centro del objeto.

**Rotación:** Giramos el plano según el ángulo de la velocidad.

**Resultado:** Como el papel ya está en el lugar correcto y con la inclinación de la velocidad, al dibujar el *rect(0, 0)*, este queda automáticamente apuntando hacia donde se está moviendo.

### Actividad 05
#### Análisis: Coordenadas polares
✿ **Observa de nuevo esta parte del código ¿Cuál es la relación entre r y theta con las posiciones x y y?**  
Aprendí que las coordenadas polares son una forma distinta de ver el espacio: en lugar de "ancho y alto", usamos distancia ($r$) y dirección ($\theta$).  
- $r$ (el radio) define qué tan lejos del centro está el círculo.  
- $\theta$ (el ángulo) define en qué parte de la "vuelta" se encuentra.

✿ **Modifica la función draw() ¿Qué ocurre? ¿Por qué?**
El círculo deja de describir un círculo grande y se queda pegado al origen (el centro del lienzo). Casi no se percibe el movimiento, aunque el código sigue corriendo. La clave está en cómo funciona *p5.Vector.fromAngle(theta)*:  

**-Vectores Unitarios:** La función *fromAngle()* crea un vector con una longitud (magnitud) de exactamente 1.  
**-Falta el Radio ($r$):** En el código anterior, multiplicábamos el coseno y el seno por un radio. Aquí, al usar solo *v.x* y *v.y*, el círculo se está dibujando a solo 1 píxel de distancia del centro. Como el círculo mide 48 píxeles de ancho, parece que no se mueve porque el pequeño giro de 1 píxel ocurre "dentro" de su propio dibujo.  
**-La línea se pierde:** Como la línea todavía usa las variables *x* e *y* (que ya no se están actualizando con el nuevo *theta*), la línea se queda quieta apuntando a un valor viejo o da error si esas variables no están definidas.

✿ **Ahora realiza esta modificación ¿Qué ocurre aquí? ¿Por qué?**  
La simulación vuelve a funcionar perfectamente. El círculo describe de nuevo su trayectoria circular grande alrededor del centro, y la línea lo sigue correctamente, conectando el origen con el centro del círculo. La clave está en cómo estamos usando ahora la función *p5.Vector.fromAngle()*:  
- **El segundo parámetro:** A diferencia del intento anterior, ahora le pasamos dos datos a la función: *fromAngle(theta, r)*.  
- **Ángulo + Magnitud:** El primer valor (*theta*) le dice al vector hacia dónde apuntar, y el segundo valor (*r*) le dice qué tan largo debe ser.  
- **Trigonometría automática:** Internamente, p5.js hace el trabajo de calcular $x = r \cdot \cos(\theta)$ y $y = r \cdot \sin(\theta)$ por nosotros.  
- **Coherencia visual:** Al usar *v.x* y *v.y* tanto para la línea como para el círculo, garantizamos que ambos elementos estén perfectamente alineados en cada frame.

### Actividad 06
#### Reflexiones sobre la Sinusoide
- **Matemática en Movimiento:** Aprendí que el seno no es solo un gráfico en papel, sino un motor de animación. Gracias a su oscilación entre -1 y 1, permite crear ciclos naturales (latidos, ondas, vaivenes).

- **El Poder de los Parámetros:** -Amplitud: Define el tamaño del movimiento.
-Frecuencia/Fase: Controlan el ritmo. Entendí que desplazar la fase en el tiempo es lo que crea la ilusión de que una onda se mueve.

- **De lo Estático a lo Vivo:** La clave fue pasar del *setup()* al *draw()*. Al vincular el ángulo con una variable que aumenta siempre (*startAngle* o *frameCount*), la estructura matemática se convierte en un comportamiento orgánico.

- **Uso en la Naturaleza:** Entender la sinusoide es fundamental para mis actividades anteriores (hadas y cometas), ya que casi todo lo natural (viento, vuelo, agua) sigue patrones oscilatorios.

### Actividad 07
El objetivo de esta actividad era transformar un sistema de oscilación simple en una estructura orgánica que responda a estímulos externos (fuerzas) y presente variaciones naturales (ruido). Lo hice de la siguiente manera:  
- **Matemática (Sinusoide Radial):** Utilicé las funciones *sin()* y *cos()* para convertir la oscilación lineal en un movimiento circular. Al usar *translate(width/2, height/2)*, todos los puntos nacen de un centro común, creando una estructura de "péndulos radiales".

- **Unidad 1 - Aleatoriedad (Perlin Noise):** Sustituí el valor estático del largo de los brazos por *noise()*. Esto permite que la amplitud de cada brazo cambie de forma fluida y orgánica, haciendo que la figura "respire" en lugar de ser rígida.

- **Unidad 3 - Fuerzas (Interacción):** Implementé el *mouseX* como una fuerza motriz. Al mover el ratón, el usuario altera la velocidad angular del sistema, simulando una fuerza externa que acelera o frena la rotación de los péndulos.

### Actividad 08
Para que la onda deje de ser una imagen fija y se mueva como una "ola", trasladé el código del *setup()* (que solo corre una vez) al *draw()* (que se ejecuta en bucle).  
- **Limpieza:** Agregué *background(255)* al inicio del draw para borrar el rastro de los círculos anteriores.
- **Nueva Variable *startAngle:*** Introduje esta variable para controlar el inicio de la fase en cada fotograma.
- **Lógica de Animación:** En cada frame, igualo el ángulo de dibujo a *startAngle*.  
-Al final de cada frame, incremento *startAngle* += 0.05.  
-Esto hace que la onda comience en un punto ligeramente distinto cada vez, creando la ilusión de desplazamiento.

## Bitácora de aplicación 
### Actividad 11 𓏲๋࣭࣪˖🪼.ᐟ
**Concepto: Deep Sea Breathing** es una obra bastante personal. Busco construir una atmósfera de introspección y calma, basándome en el lugar donde nací y lo que me gusta. La narrativa se basa en un "Móvil de Cuna Abisal": un objeto diseñado para serenar la mente, trasladando la simplicidad de un móvil infantil a las profundidades del océano. Las reglas del sistema (fricción, inercia y brillo) están diseñadas para que cada interacción se sienta como un retorno a ese estado de asombro primitivo, donde el movimiento suave y el sonido cristalino eran suficientes para generar paz.  

Se aplicó Movimiento Armónico Simple para el nado vertical de las criaturas y la ondulación de los tentáculos y colas. El uso de funciones trigonométricas ($\sin$ y $\cos$) permite que el sistema no sea rígido, sino que tenga un ritmo orgánico que imita la respiración y el vaivén del agua. De las unidades anteriores apliqué Física (Fuerzas y Vectores) y Sistemas de Partículas  
- Física: Implementé conceptos de torque y fricción angular para que el giro del móvil responda a la fuerza del aire.
- Sistemas de Partículas: Los "destellos de alegría" y las burbujas funcionan bajo reglas de aceleración y desvanecimiento (fade-out), creando una respuesta visual efímera que premia la interacción del usuario.

La obra utiliza el micrófono como un sensor de energía vital. El usuario debe respirar profundo y exhalar hacia el sistema; esta entrada de audio se traduce en una fuerza de rotación que rompe la inercia del móvil.

**Código:**
```js
let mic;
let started = false; //Controla si la simulación ya inició (tras el clic)
let instructionsAlpha = 255; //Para el desvanecimiento del mensaje inicial

// Física
let angleMóvil = 0; //Posición angular actual
let angleVel = 0; //Velocidad de rotación
let friction = 0.985; //Resistencia que detiene el móvil poco a poco
let waveAngle = 0;

// Sonido (CAJA DE MÚSICA CRISTALINA)
let osc, env;
let notas = [523.25, 587.33, 659.25, 698.46, 783.99, 880.00, 987.77, 1046.50]; //escala c4 a c5, registro medio 
let glimmers = []; 
let bubbles = [];

function setup() {
  createCanvas(windowWidth, windowHeight);
  
  env = new p5.Envelope();
  env.setADSR(0.02, 0.1, 0.1, 0.8); //Para que se más elongaod el sonido
  env.setRange(0.3, 0); //Volumen máximo y mínimo
  
  osc = new p5.Oscillator('sine'); //Genera una onda pura (suave)
  osc.amp(env); //Conecta el oscilador a la envolvente
}

function draw() {
  background(5, 10, 25);

  if (!started) {
    drawStartScreen();
    return;
  }

  // 1. CAPTURA DE ENERGÍA
  let vol = mic.getLevel();
  //Convertimos el volumen en una fuerza de giro (torque)
  let torque = map(vol, 0, 0.5, 0, 0.15); 
  angleVel += torque; //La fuerza acelera la rotación
  angleVel *= friction; //Aplicamos la fricción para que no gire por siempre
  angleMóvil += angleVel; //Actualizamos la posición según la velocidad

  // 2. LÓGICA DE DESTELLOS Y SONIDO
  if (angleVel > 0.002) {
    if (random(1) < angleVel * 1.5) { 
      glimmers.push(new Glimmer(random(width), random(height), false));
    }
    if (random(1) < angleVel * 0.7) {
      playChime(); //Elige nota al azar y la toca
      for(let i=0; i<3; i++) {
        glimmers.push(new Glimmer(random(width), random(height), true));
      }
    }
    if (frameCount % 10 == 0) bubbles.push(new Bubble(width/2, height * 0.85));
  }

  // Partículas
  actualizarParticulas();

  // 3. MÓVIL Y HÉLICE
  dibujarEscena();

  // 4. MENSAJE DE RESPIRACIÓN (Aparece tras el clic y se desvanece)
  if (instructionsAlpha > 0) {
    drawInstructions();
    instructionsAlpha -= 1.5; // Velocidad del desvanecimiento
  }

  waveAngle += 0.05;
}

function drawInstructions() {
  push();
  textAlign(CENTER, CENTER);
  fill(200, 240, 255, instructionsAlpha);
  textSize(20);
  textFont('Georgia'); // Un estilo más elegante/clásico
  text("respira profundo y exhala...", width / 2, height / 1.4);
  pop();
}

// --- FUNCIONES DE SOPORTE (Limpieza de código) ---

function actualizarParticulas() {
  for (let i = glimmers.length - 1; i >= 0; i--) {
    glimmers[i].update();
    glimmers[i].show();
    if (glimmers[i].finished()) glimmers.splice(i, 1);
  }
  for (let i = bubbles.length - 1; i >= 0; i--) {
    bubbles[i].update(angleVel);
    bubbles[i].show();
    if (bubbles[i].finished()) bubbles.splice(i, 1);
  }
}

function dibujarEscena() {
  push();
  translate(width / 2, height / 5);
  drawCribCarousel(angleMóvil, angleVel);
  pop();

  push();
  translate(width / 2, height * 0.85);
  drawGenerator(angleMóvil);
  pop();
}

function drawCribCarousel(angle, speed) {
  noFill();
  stroke(100, 220, 255, 80);
  strokeWeight(2);
  ellipse(0, 0, 320, 50);
  let numCriaturas = 5;
  let radio = 140;
  for (let i = 0; i < numCriaturas; i++) {
    let theta = angle + (TWO_PI / numCriaturas) * i;
    let xBase = radio * cos(theta);
    let yBase = (radio * 0.15) * sin(theta);
    let oscY = sin(waveAngle + i) * (20 + speed * 450);
    let h = 230 + oscY;
    let lag = speed * 180;
    let xCtrl = xBase - (lag * cos(theta + HALF_PI));
    stroke(200, 240, 255, 60);
    strokeWeight(1.2);
    bezier(xBase, yBase, xCtrl, yBase + h*0.5, xBase - lag, yBase + h*0.8, xBase, yBase + h);
    drawImprovedCreature(xBase, yBase + h, i, speed);
  }
}

function drawImprovedCreature(x, y, i, speed) {
  push();
  translate(x, y);
  let b = map(speed, 0, 0.1, 130, 255);
  noStroke();
  if (i % 3 == 0) { // Mantarraya
    fill(100, 230, 255, b);
    beginShape();
    curveVertex(-35, 0); curveVertex(-35, 0);
    curveVertex(0, -12); curveVertex(35, 0);
    curveVertex(0, 16); curveVertex(-35, 0); curveVertex(-35, 0);
    endShape();
    stroke(100, 230, 255, b/1.8);
    strokeWeight(1.5);
    noFill();
    let tailWave = sin(frameCount * 0.1 + i) * (5 + speed * 30); //Oscilación de la cola
    let tailLag = speed * 80; //La cola se retrasa según la velocidad (Inercia)
    // Los puntos de control se mueven con tailWave para crear el efecto flexible
    bezier(0, 16, tailWave, 30, -tailLag + tailWave, 40, tailWave * 0.5, 55);
  } 
  else if (i % 3 == 1) { // Tiburón Ballena
    fill(70, 130, 240, b);
    ellipse(0, 0, 55, 25);
    triangle(-25, 0, -40, -12, -40, 12);
    fill(255, b-50);
    for(let m=0; m<7; m++) circle(-12 + m*6, -6 + m%2*14, 2);
  } 
  else { // Medusa
    fill(240, 130, 255, b);
    arc(0, 0, 40, 35, PI, TWO_PI);
    stroke(240, 130, 255, b/2.5);
    for(let j=-12; j<=12; j+=6) {
      let ty = 22 + sin(frameCount * 0.1 + j) * 7;
      line(j, 0, j + sin(frameCount * 0.05) * 4, ty);
    }
  }
  pop();
}

function drawGenerator(angle) {
  rotate(angle * 5);
  for (let i = 0; i < 4; i++) {
    rotate(HALF_PI);
    fill(0, 255, 255, 100);
    stroke(255, 180);
    bezier(0, 0, 20, -30, 55, -30, 55, 0);
    bezier(55, 0, 55, 30, 20, 30, 0, 0);
  }
  fill(255); circle(0,0, 15);
}

function playChime() {
  osc.freq(random(notas));
  env.play();
}

class Glimmer {
  constructor(x, y, isJoyful) {
    this.x = x; this.y = y;
    this.alpha = 255;
    this.joyful = isJoyful;
    this.size = isJoyful ? random(6, 12) : random(1, 4);
    let colors = [color(180, 255, 255), color(255), color(220, 180, 255)];
    this.c = random(colors);
  }
  update() { this.alpha -= this.joyful ? 5 : 10; }
  show() {
    push();
    if (this.joyful) { drawingContext.shadowBlur = 12; drawingContext.shadowColor = this.c; }
    fill(red(this.c), green(this.c), blue(this.c), this.alpha);
    noStroke(); circle(this.x, this.y, this.size);
    pop();
  }
  finished() { return this.alpha < 0; }
}

class Bubble {
  constructor(x, y) {
    this.x = x + random(-70, 70);
    this.y = y;
    this.alpha = 180;
  }
  update(s) { this.y -= (1.5 + s*12); this.alpha -= 3; }
  show() {
    stroke(255, this.alpha); noFill();
    circle(this.x, this.y, random(2, 8));
  }
  finished() { return this.alpha < 0; }
}

function drawStartScreen() {
  fill(255);
  textAlign(CENTER, CENTER);
  textSize(24);
  text("DEEP SEA BREATHING", width / 2, height / 2 - 20);
  textSize(14);
  fill(100, 200, 255);
  text("HAZ CLIC PARA INICIAR", width / 2, height / 2 + 25);
}

function mousePressed() {
  if (!started) {
    userStartAudio(); 
    mic = new p5.AudioIn();
    mic.start();
    osc.start();
    started = true;
  }
}
```

**Enlace:** https://editor.p5js.org/Hannanah06/full/z_98blgrL



## Bitácora de reflexión
### Actividad 12
#### Diagrama:

https://excalidraw.com/#json=pT0VWoVL8m-Pl5gIJvVcb,A7jIBRwphtMx-mELK7NWQA







