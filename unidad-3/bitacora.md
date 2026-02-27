# Unidad 3

## Bitácora de proceso de aprendizaje
### Actividad 01
Aunque no pude ver el video completo, leyendo acerca de su trabajo y charlas anteriores entendí varias cosas que me inspiran:  

✿ Su enfoque mezcla lo científico y lo artístico: él habla de fuerzas invisibles como magnetismo y gravedad, no como temas científicos fríos, sino como herramientas para dar vida a imágenes que “sienten”.

✿ Su método creativo surge de la experimentación y la iteración, no de una idea fija. En otras entrevistas ha comentado que empezó experimentando con herramientas como *Flash* o *Processing*, y que muchas de sus decisiones creativas vinieron de probar y volver a probar cosas hasta que algo interesante ocurría.

✿ Me identifico mucho con la idea de que la disciplina no es solo técnica, sino un hábito de curiosidad (explorar, fallar, observar y seguir). En una de sus charlas comenta cómo ve estos sistemas en todas partes ٠࣪⭑*en árboles, en el movimiento de personas, incluso cuando intenta dormir*٠࣪⭑ lo que muestra cuán profundamente vive su trabajo.  

Me impresiona cómo algo que comienza con código, fórmulas y matemáticas puede parecer tan orgánico y estéticamente sugerente. Me recuerda que, en el arte digital, no hay una sola forma de crear; la forma y el contenido pueden surgir de reglas que el artista define, pero que la obra misma descubre al ejecutarse.

### Actividad 02
En esta unidad sentí que el movimiento dejó de ser “porque sí” y empezó a tener una razón. Antes la aceleración era casi un invento creativo, pero ahora entiendo que puede salir de algo más lógico: fuerzas que se suman. Cuando vi que todo se conecta con *F = m·a*, como que se abrió mi mente, esto ya no es solo mover cosas en pantalla, es construir mini reglas del universo.

Me gustó darme cuenta de que no estoy animando directamente el movimiento, sino diseñando condiciones para que ocurra. Eso me parece muy poderoso. También me deja pensando en hasta qué punto quiero que mis simulaciones sean físicas y cuándo romper esas reglas puede ser más interesante. Esta unidad me hizo sentir que estoy uniendo lo técnico con lo creativo, y eso me gusta mucho:

### Actividad 03


## Bitácora de aplicación
### Actividad 04 ⌯ᯓ🪁🍃༄.°
**Concepto:** Mi obra, **Fine Line**, trata sobre la fragilidad de las conexiones. Al poner al espectador en primera persona sosteniendo una cometa, no solo quiero que vea una animación, sino que sienta la responsabilidad de mantener algo a flote. Es una metáfora sobre esos momentos de la vida donde todo está en calma y es fácil sostener lo que queremos, frente a los momentos de "tormenta" donde el entorno intenta arrebatárnoslo.  

Para que esta historia se sienta real, la aceleración no es fija, sino que nace de una lucha constante de fuerzas:  

☁︎ **El equilibrio:** En las tormentas, el usuario debe aplicar una fuerza de tensión (hacer clic) que contrarreste exactamente la fuerza del viento. Si no hay una reacción proporcional, la aceleración descontrolada hace que el hilo se rompa.

☁︎ **La masa y el peso:** Le di a la cometa una masa alta para que se sienta pesada y valiosa. No es un objeto ligero que vuela sin rumbo; es algo que opone resistencia, lo que obliga al espectador a ser más cuidadoso con sus movimientos.

☁︎ **La pérdida:** La regla de ruptura es el final de la historia. Cuando la distancia entre la mano y la cometa supera un límite, el sistema deja de calcular la tensión y la cometa escapa. Es el momento donde la física nos dice que el control se ha perdido definitivamente.  

Al final, como si fuéramos niños otra vez, lloramos a nuestra madre por la pérdida de nuestra preciada cometa.

**Código:**
```js
let kite;
let windState = "CALMADO";
let timer = 0;
let breezeLines = [];
let broken = false;
let handImg; 

let colSkyTop = [44, 62, 110];    // Azul oscuro/noche
let colSkyBottom = [190, 210, 245]; // Azul claro/lavanda
let colKite = [235, 130, 140];    // Rosa/Rojizo suave
let colSkin = [245, 210, 180];    // Crema/Piel
let colGrass = [60, 85, 130];     // Azul verdoso para el suelo (estético)
let colDirt = [40, 50, 80];       // Tierra muy oscura y reducida
let colLetras = [255,255,255]

function preload() {
  handImg = loadImage('mano.png'); 
}
function setup() {
  createCanvas(1000, 500);
  // Masa 
  kite = new Kite(4.0, 600, height - 250);
  
  for (let i = 0; i < 20; i++) {
    breezeLines.push(new Breeze());
  }
}

function draw() {
  drawSkyGradient();
 
  // El ancla de la mano en la esquina inferior izquierda
  let handAnchor = createVector(60, height - 60);

  if (!broken) {
    // CONTROLAR LA FRECUENCIAAA
    if (millis() > timer) {
      windState = random() > 0.5 ? "TORMENTOSO" : "CALMADO";
      timer = millis() + random(5000, 8000);
    }

    // --- CÁLCULO DE FUERZAS ---
    let lift = createVector(0, -0.07); // Sustentación constante
    let wind;
    
    if (windState === "TORMENTOSO") {
      wind = createVector(0.45, random(-0.05, 0.05)); // Viento fuerte horizontal
    } else {
      wind = createVector(0.08, -0.02); // Brisa ligera
    }

    let tension = createVector(0, 0);
    let distance = p5.Vector.dist(kite.position, handAnchor);
    let isTense = false;

    // Límite de ruptura
    if (distance > 750) broken = true;

    // Resistencia en tormenta: Mantiene la cometa en el sitio
    if (windState === "TORMENTOSO" && mouseIsPressed) {
      tension = p5.Vector.sub(handAnchor, kite.position);
      // Magnitud calculada para equilibrar el viento de 0.45
      tension.setMag(0.4); 
      isTense = true;
    }

    // Aplicar Fuerzas al objeto
    kite.applyForce(lift);
    kite.applyForce(wind);
    kite.applyForce(tension);
    
    // Rozamiento (Drag) aumentado para suavidad extrema
    let drag = kite.velocity.copy();
    drag.mult(-0.1); 
    kite.applyForce(drag);

    kite.update();
    kite.checkGround(); 
    kite.display(handAnchor, isTense);

  } else {
    // Escena de pérdida
    kite.applyForce(createVector(0.2, -0.08));
    kite.update();
    kite.display(null, false);
    
    push();
    fill(colLetras);
    noStroke();
    textAlign(CENTER);
    textSize(22);
    text("MAAA!!, MI COMETAAAA :( ...", width/2, height/2);
    pop();
  }
 
  for (let b of breezeLines) {
    b.update(windState);
    b.display();
  }
  
  drawFirstPersonHand(handAnchor);
  drawInterface();
}

function mousePressed() {
  if (windState === "CALMADO" && !broken) {
    let handAnchor = createVector(60, height - 60);
    let pull = p5.Vector.sub(handAnchor, kite.position);
    // PARA JALAR LA COMETA
    pull.setMag(6); 
    kite.applyForce(pull);
  }
}

// --- CLASES Y DIBUJO ---
class Kite {
  constructor(m, x, y) {
    this.mass = m;
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }

  applyForce(f) {
    let force = p5.Vector.div(f, this.mass);
    this.acceleration.add(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.velocity.limit(1.8); 
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  checkGround() {
    let groundLimit = height - 55;
    if (this.position.y > groundLimit) {
      this.position.y = groundLimit;
      this.velocity.y *= -0.1;
    }
  }

  display(hand, isTense) {
    if (hand && !broken) {
      stroke(isTense ? [235, 100, 110] : [255, 200]);
      strokeWeight(isTense ? 3 : 1);
      line(this.position.x, this.position.y, hand.x, hand.y);
    }

    push();
    translate(this.position.x, this.position.y);
    rotate(this.velocity.heading() + PI/2);
    
    fill(colKite);
    stroke(255, 50);
    strokeWeight(1.5);
    beginShape();
    vertex(0, -20); vertex(15, 0); vertex(0, 30); vertex(-15, 0);
    endShape(CLOSE);
    
    // Cola de la cometa
    noFill();
    stroke(colKite);
    beginShape();
    for (let i = 0; i < 40; i += 5) {
      vertex(sin(i * 0.2 + frameCount * 0.1) * 5, 30 + i);
    }
    endShape();
    pop();
  }
}

class Breeze {
  constructor() {
    this.x = random(width);
    this.y = random(height - 60);
    this.speed = random(0.2, 0.7);
    this.offset = random(100);
  }

  update(state) {
    let s = (state === "TORMENTOSO") ? this.speed * 5 : this.speed;
    this.x += s;
    if (this.x > width) this.x = -50;
  }

  display() {
    stroke(255, 80);
    noFill();
    beginShape();
    for (let i = 0; i < 40; i += 8) {
      let dy = sin((this.x + i) * 0.04 + this.offset) * 3;
      vertex(this.x + i, this.y + dy);
    }
    endShape();
  }
}

function drawSkyGradient() {
  for (let i = 0; i < height; i++) {
    let inter = map(i, 0, height, 0, 1);
    let c = lerpColor(color(colSkyTop), color(colSkyBottom), inter);
    stroke(c);
    line(0, i, width, i);
  }
}

function drawMinimalGround() {
  noStroke();
  fill(colDirt);
  rect(0, height - 20, width, 20);
  fill(colGrass);
  rect(0, height - 50, width, 30); 
}

function drawFirstPersonHand(anchor) {
  push();
  // 1. Llevamos el centro de dibujo al ancla
  translate(anchor.x, anchor.y); 
  
  // 2. ROTACIÓN: Modifica el número (0.1) para girar la mano
  // rotate(radians(15)); // Puedes usar grados para que sea más fácil
  rotate(0.6); 

  imageMode(CENTER);
  
  let wobbleX = 0;
  let wobbleY = 0;
  if (windState === "TORMENTOSO" && mouseIsPressed) {
    wobbleX = random(-1.5, 1.5);
    wobbleY = random(-1.5, 1.5);
  }

  if (handImg) {
    // 3. POSICIÓN: Los valores (-20 y +40) mueven la imagen respecto al ancla
    // 4. TAMAÑO: (200, 200) controla la escala
    image(handImg, -20 + wobbleX, 70 + wobbleY, 200, 200); 
  }
  pop();
}

function drawInterface() {
  noStroke();
  fill(255, 150);
  textSize(20);
  textAlign(LEFT);
}
```

## Bitácora de reflexión






