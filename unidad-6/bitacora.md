# Unidad 6

## Bitácora de proceso de aprendizaje
### Actividad 01
Las piezas que me llamaron la atención fueron *Fidenza* y *Flow interpretation*.

#### Fidenza:
<img width="573" height="688" alt="image" src="https://github.com/user-attachments/assets/9b9755cd-8ffe-414e-a9a7-c40cf862f726" />  

✦ **Decisiones visuales:** Se basa en una composición que alterna saturación y vacíos. El ritmo lo dan bloques de distintos grosores que siguen curvas fluidas, creando una densidad orgánica que evita colisiones.

✦ **Potencia:** Logra que formas geométricas rígidas (rectángulos) se comporten como fluidos, transmitiendo una sensación de orden natural y complejidad estructural.

✦ **Hipótesis del sistema:** Un campo de flujo (Flow Field) basado en Ruido de Perlin, integrado con un algoritmo de empaquetamiento que impide que los bloques se solapen, ajustando su ancho según el espacio disponible.  

#### Flow Interpretation:
<img width="565" height="712" alt="image" src="https://github.com/user-attachments/assets/a43a0cbb-d362-4bd0-ab64-c0be55d08ec9" />  

✦ **Decisiones visuales:** Destaca la repetición de trazos finos y una dirección de movimiento muy marcada. La variación es sutil en cada línea, emulando la textura de un pincel seco o fibras naturales.

✦ **Potencia:** Su fuerza radica en la gestualidad. A pesar de ser código, se siente humano y táctil debido a la acumulación de miles de líneas con opacidad baja.

✦ **Hipótesis del sistema:** Uso de partículas mensajeras que dejan un rastro (trail) al recorrer un campo vectorial. El sistema aplica pequeñas perturbaciones aleatorias en cada paso para romper la perfección matemática y generar esa textura fibrosa.

### Actividad 02
**1) Explica con tus propias palabras qué es un agente autónomo.**   
Un agente autónomo es una entidad digital que toma sus propias decisiones basándose en su entorno y en un conjunto de reglas internas. A diferencia de un objeto que solo "reacciona" (como una pelota rebotando), el agente tiene intencionalidad: observa dónde está, hacia dónde quiere ir y calcula cómo llegar ahí por sí mismo.  

**2) Explica qué es una *steering force*.**  
Es una fuerza de dirección o de "maniobra". No es una fuerza que empuja al objeto bruscamente, sino una fuerza que lo orienta suavemente hacia un objetivo. Básicamente, es el ajuste que el agente hace para corregir su trayectoria actual y alcanzar su velocidad deseada.

**3) Compara una *steering force* con una fuerza externa como la gravedad.**  
La gravedad es una fuerza externa y universal; es una imposición del entorno que empuja a todos los objetos por igual, generando una aceleración constante y predecible (como una caída libre).

En cambio, la steering force es una fuerza interna y deliberada. Representa la "voluntad" del agente para corregir su rumbo según su objetivo, lo que genera trayectorias curvas y fluidas en lugar de movimientos mecánicos. Mientras la gravedad es una reacción física, el steering es una decisión de diseño.

**4) Describe por qué estas ideas son útiles para diseñar comportamiento visual y no solo para simular movimiento.**  
Estas ideas son potentes porque permiten diseñar narrativa y personalidad, no solo física:  

✦ **Dejan de ser puntos y pasan a ser personajes:** Un agente que "duda" antes de moverse o que "persigue" con agresividad comunica una emoción al espectador.

✦ **Emergencia:** Al poner muchos agentes con reglas simples de steering (como en las obras de Tyler Hobbs), surgen patrones complejos y texturas visuales que parecen vivas, algo imposible de lograr con fuerzas externas rígidas.

✦ **Interactividad:** Permiten que el sistema responda al usuario de forma orgánica (por ejemplo, que las partículas "sientan" curiosidad por el cursor en lugar de solo ser empujadas por él).

### Actividad 03
**1) ¿Cómo está construido el campo de flujo?**  
Se construye dividiendo el lienzo en una rejilla de celdas. A cada celda se le asigna un ángulo o dirección, generalmente utilizando *Perlin Noise* para asegurar que los cambios de dirección entre celdas vecinas sean suaves y coherentes, en lugar de aleatorios.

**2) ¿Qué representa cada celda o vector del campo?**  
Cada celda contiene un vector unitario (una dirección). Representa la "fuerza" o el "deseo" del entorno en ese punto específico: le indica a cualquier agente que pase por ahí hacia dónde debería dirigirse.

**3) ¿Cómo usa un agente su posición para consultar el campo?**  
El agente toma su posición (*x*, *y*) actual y la mapea para encontrar a qué columna y fila de la rejilla corresponde. Es como buscar su ubicación en un mapa para leer la señal de tránsito que hay justo en ese punto.

**4) ¿Cómo se convierte el vector consultado en una decisión de movimiento?**  
Una vez que el agente obtiene el vector de la celda, ese vector se convierte en su "velocidad deseada". El agente aplica la fórmula de steering: calcula la diferencia entre esa dirección deseada y su velocidad actual, generando una fuerza que lo empuja gradualmente hacia el flujo.

**5) Identifica parámetros importantes del sistema.**  
✦ **Resolución:** El tamaño de las celdas. Una resolución alta (celdas pequeñas) crea flujos detallados; una baja crea movimientos más toscos.

✦ ***MaxSpeed*:** Qué tan rápido puede ir el agente.

✦ ***MaxForce*:** La capacidad de maniobra. Si es baja, el agente tarda en girar (curvas amplias); si es alta, reacciona instantáneamente (giros cerrados).

✦ **Cantidad de agentes:** Define la densidad visual y qué tan evidente es el campo invisible

**6) Realiza al menos una modificación y analiza el efecto visual que produce.**  
**Modificación:** Aumentar la resolución de la rejilla y reducir drásticamente la MaxForce.

**Efecto visual:** Los agentes parecen tener "pereza" o inercia. No pueden seguir los giros cerrados del campo, lo que genera trazos que se cruzan y suavizan el ruido del fondo, creando una estética más etérea y menos geométrica.  

✦ **¿Qué tipo de movimiento produce este algoritmo?:** Es un movimiento emergente y coreografiado. No hay un líder, pero todos parecen seguir una voluntad común. Es fluido, continuo y no lineal.

✦ **¿Qué sensaciones visuales te sugiere?:** Sugiere naturalidad, corrientes de aire, magnetismo o el movimiento de cardúmenes y fluidos. Se siente como algo vivo pero gobernado por leyes invisibles.

✦ **¿En qué tipo de pieza musical imaginas que podría funcionar bien?:** Encajaría con el Minimalismo (como Philip Glass) o Ambient. Música que se construye mediante la repetición de patrones pequeños que, al sumarse, crean una atmósfera compleja y envolvente.

### Actividad 04
**1) Explica con tus palabras las tres reglas básicas: separación, alineación, cohesión.**  
✦ **Separación:** Es la regla de seguridad. El agente evita chocar con sus vecinos cercanos para mantener su espacio personal. Si se acerca demasiado a alguien, aplica una fuerza en sentido opuesto.

✦ **Alineación:** Es la regla de imitación. El agente observa hacia dónde se dirigen sus vecinos y ajusta su propia velocidad para moverse en la misma dirección que el grupo.

✦ **Cohesión:** Es la regla social. El agente intenta dirigirse hacia el centro de masa de sus vecinos para no quedarse solo y mantener al grupo unido.

**2) Identifica qué parámetros controlan estas reglas.**  
El sistema se controla principalmente mediante:

✦ **Pesos (Weights):** Multiplicadores que definen qué regla es más importante (ej. "más separación que cohesión").

✦ **Radio de visión (Neighbor Distance):** Qué tan lejos puede "ver" un agente para considerar a otros como parte de su grupo.

✦ **Límites físicos:** *maxSpeed* (velocidad límite) y *maxForce* (capacidad de giro).

**3) Modifica uno o más pesos del sistema y describe el efecto visual y colectivo.**  
**Modificación:** Aumentar al máximo el peso de la Separación y reducir a cero la Cohesión.

**Efecto visual:** El grupo se desintegra inmediatamente. Los agentes actúan de forma paranoica, huyendo unos de otros apenas se cruzan, llenando todo el lienzo de manera uniforme pero caótica, perdiendo cualquier sentido de "comunidad".

**4) Describe el comportamiento emergente observado.**  
El *flocking* estándar produce un movimiento fluido y estable. Es fascinante porque no hay un líder; el orden surge de abajo hacia arriba. A veces parece nervioso cuando encuentran un obstáculo, pero rápidamente recuperan una danza colectiva que parece un solo organismo vivo.  

✦ **¿Qué atmósfera visual produce el flocking?:** Produce una sensación de vida biológica y sincronía. Evoca la naturaleza (aves, peces, insectos) y transmite una mezcla de calma (por el flujo) y vigilancia (por la reacción constante).  

✦ **¿En qué tipo de relación con una canción podría funcionar mejor este algoritmo?:** Funcionaría muy bien con música que tenga capas que se suman progresivamente o polirritmias. Imagino una canción donde cada instrumento es un agente: a veces se separan en solos y luego todos se alinean en un coro potente. Es ideal para visualizar la armonía y la tensión entre el individuo y el colectivo.

### Actividad 05
#### Comparativa: *Flow Fields* vs. *Flocking*
✦ **Movimiento y Control:** En los *Flow Fields*, el movimiento es coreografiado por una estructura invisible; el diseñador tiene un control alto al "dibujar" el camino. En el *Flocking*, el movimiento es autónomo e impredecible; el control es indirecto ya que depende de la interacción constante entre agentes.

✦ **Emergencia y Atmósfera:** El *Flow Field* tiene una emergencia baja/moderada y transmite orden, serenidad y magnetismo. El *Flocking* es puramente emergente; se siente "vivo" y biológico, transmitiendo sincronía y dinamismo social.

✦ **Música y Técnica:** El *Flow Field* es como el Ambient: una estructura base guía todo; es muy eficiente para mover miles de partículas. El *Flocking* es como una improvisación de Jazz: cada elemento reacciona al otro; es visualmente rico pero más costoso computacionalmente.  

#### Si quisieras diseñar visuales para una canción contemplativa, agresiva, melancólica o eufórica, ¿Cuál algoritmo usarías en cada caso y por qué?
✦ **Contemplativa:** *Flow Field*. Su avance constante y sin conflictos refuerza la paz y el enfoque meditativo.

✦ **Agresiva:** *Flocking*. Con separación extrema y fuerza alta, genera movimientos bruscos, violentos y caóticos.

✦ **Melancólica:** *Flow Field*. Con rastros largos y velocidad mínima, evoca la sensación de dejarse llevar por una corriente sin oponer resistencia.

✦ **Eufórica:** *Flocking*. Con alta cohesión y velocidad, crea un clímax visual de masa coordinada que se mueve con energía y triunfo.

## Bitácora de aplicación 
### Actividad 06
#### Concepto: 
La obra se llama "idk". Visualmente, representa el mito de Ícaro no como una caída, sino como una transformación. Se centra en un núcleo solar pulsante, rodeado de un sistema de partículas que actúan como "cenizas de oro" y geometrías fractales que simbolizan la ascensión y la divinidad.

#### Relación entre la visual y la canción:
La canción *Icarus* de ARTMS tiene una estructura que transita entre la vulnerabilidad y la explosión de poder (especialmente en el estribillo y el puente). La visual emula esto mediante el uso del color: tonos pálidos y movimientos erráticos durante los versos, que se transforman en un brillo dorado intenso y la aparición de "alas" de ruido Perlin cuando la música alcanza su punto máximo, reflejando la letra "reborn like a phoenix wing".

#### Mapa de decisiones:
✦ **Fondo Negro:** Para representar el vacío del espacio y dar jerarquía absoluta a la luz.

✦ **Partículas con Gravedad Inversa:** Las partículas no caen; son atraídas por el sol o expulsadas por el bajo (fuerzas centrífugas).

✦ **Geometría Triangular:** Uso de polígonos de tres lados en el mandala para evocar agresividad y ascensión.

✦ **Textura de Ruido (CRT):** Decisión estética para darle un acabado de "metraje encontrado" o visión mística, alejándose de lo digital plano.

#### Mapa de interpretación:
✦ **El Sol:** Representa la meta, el deseo y la fuente de energía.

✦ **Las Partículas:** Simbolizan las plumas y las cenizas del cuerpo de Ícaro que, al quemarse, se convierten en luz pura.

✦ **El Zoom Reactivo:** Interpreta la "sofocación" y la intensidad del acercamiento al sol; la cámara parece vibrar por el calor y la presión del sonido.

#### Justificación del algoritmo elegido:
Se seleccionó un sistema de Agentes Autónomos y Ruido de Perlin.

✦ **Ruido de Perlin:** Utilizado para las "Alas de Fénix" y la corona solar, ya que permite un movimiento fluido y orgánico que imita el fuego, imposible de lograr con aleatoriedad simple (*random*).

✦ **Lévy Flight (implícito en explosiones):** Para que las partículas tengan cambios de ritmo bruscos durante el drop, simulando una desintegración física real.

#### Explicación de la relación audio-visual:
La relación es Directa y Paramétrica:

✦ **Frecuencias Bajas (Bass):** Controlan el tamaño del sol y la fuerza de explosión de las partículas.

✦ **Frecuencias Altas (Treble):** Modulan el brillo de las alas y la velocidad de rotación del mandala.

✦ **Amplitud (Volumen):** Determina el nivel de zoom y el grosor de las líneas, creando una sinestesia donde el espectador "ve" la presión sonora de la producción de ARTMS.  

#### Código:
**Index:**
```js
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>ICARUS — The Solar Rebirth</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.4/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.4/addons/p5.sound.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Space+Mono&display=swap');
        body { margin: 0; background: #000; overflow: hidden; font-family: 'Space Mono', monospace; }
        #ui { position: fixed; width: 100%; height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; z-index: 100; background: #000; transition: 1s; }
        #ui.hidden { opacity: 0; pointer-events: none; }
        .title { font-family: 'Cinzel', serif; color: white; font-size: 2.5rem; letter-spacing: 12px; text-shadow: 0 0 15px #ffcc00; text-align: center; margin-bottom: 40px; text-transform: uppercase; }
        #playBtn { padding: 15px 40px; background: none; border: 1px solid rgba(255,204,0,0.5); color: #ffcc00; cursor: pointer; letter-spacing: 3px; transition: 0.3s; text-transform: uppercase; font-weight: bold; }
        #playBtn:hover { background: #ffcc00; color: #000; border-color: #ffcc00; box-shadow: 0 0 20px #ff9900; }
    </style>
</head>
<body>

<div id="ui">
    <h1 class="title">ICARUS</h1>
    <input type="file" id="fileInput" accept="audio/*" style="display:none">
    <button id="playBtn">SUBIR AUDIO Y RENACER</button>
</div>

<script>
let song, fft, amp;
let particles = [];
let noiseGfx;
let tOffset = 0;
let smoothZoom = 1.0;

// Estados de interacción
let modoFuego = true;

// Colores
let colSunCore, colSunMid, colSunOut, colRebirth;

function setup() {
    createCanvas(windowWidth, windowHeight);
    fft = new p5.FFT(0.85, 512);
    amp = new p5.Amplitude();
    
    actualizarPaleta();

    for (let i = 0; i < 1000; i++) {
        particles.push(new Particle());
    }

    noiseGfx = createGraphics(width, height);
    noiseGfx.loadPixels();
    for (let i = 0; i < noiseGfx.pixels.length; i += 4) {
        let n = random(15);
        noiseGfx.pixels[i] = noiseGfx.pixels[i+1] = noiseGfx.pixels[i+2] = 255;
        noiseGfx.pixels[i+3] = n;
    }
    noiseGfx.updatePixels();
}

function actualizarPaleta() {
    colorMode(HSB, 360, 100, 100, 100);
    if (modoFuego) {
        colSunCore = color(50, 20, 100, 80);  
        colSunMid = color(40, 90, 100, 50);   
        colSunOut = color(15, 100, 100, 20);  
        colRebirth = color(45, 100, 100, 100); 
    } else {
        colSunCore = color(190, 30, 100, 80); // Cyan pálido
        colSunMid = color(210, 80, 100, 50);  // Azul eléctrico
        colSunOut = color(260, 90, 80, 20);   // Violeta profundo
        colRebirth = color(180, 100, 100, 100); // Turquesa neón
    }
    colorMode(RGB, 255, 255, 255, 255);
}

function mousePressed() {
    modoFuego = !modoFuego;
    actualizarPaleta();
}

function draw() {
    if (!song || !song.isPlaying()) {
        background(0);
        return;
    }

    fft.analyze();
    let bass = fft.getEnergy("bass") / 255;
    let mid = fft.getEnergy("mid") / 255;
    let high = fft.getEnergy("treble") / 255; 
    let vol = amp.getLevel();

    background(0, 2, 8); 

    let zoomIntensity = map(bass, 0.7, 1, vol * 0.4, vol * 1.2, true);
    smoothZoom = lerp(smoothZoom, 1.0 + zoomIntensity, 0.1);

    push();
    translate(width/2, height/2);
    
    let isDrop = bass > 0.83;
    
    for (let p of particles) {
        if (isDrop) p.explode(bass);
        p.update();
        p.show(bass, isDrop);
    }

    scale(smoothZoom);
    drawMandala(bass, mid, isDrop);
    drawSolarCorona(bass, vol);

    if (isDrop || vol > 0.3) {
        drawPhoenixWings(bass, vol, high);
    }

    pop();

    image(noiseGfx, 0, 0);
    drawScanlines();
    tOffset += 0.005 + (bass * 0.02);
}

class Particle {
    constructor() {
        this.reset();
    }
    reset() {
        this.pos = p5.Vector.random2D().mult(random(0, 60));
        this.vel = p5.Vector.random2D().mult(random(0.2, 1.5));
        this.acc = createVector(0, 0);
        this.alpha = random(50, 180);
        this.size = random(1, 2.5);
    }
    explode(intensity) {
        let force = this.pos.copy().normalize();
        force.mult(intensity * 18);
        this.acc.add(force);
    }
    update() {
        let gravity = this.pos.copy().mult(-0.0008);
        this.acc.add(gravity);
        this.vel.add(this.acc);
        this.vel.limit(7);
        this.pos.add(this.vel);
        this.acc.mult(0);
        if (this.pos.mag() > width * 0.9) this.reset();
    }
    show(bass, isDrop) {
        if (isDrop) {
            stroke(colRebirth.levels[0], colRebirth.levels[1], colRebirth.levels[2], this.alpha);
            strokeWeight(this.size + bass * 3);
        } else {
            stroke(255, this.alpha * (0.5 + bass)); 
            strokeWeight(this.size);
        }
        point(this.pos.x, this.pos.y);
    }
}

function drawMandala(bass, mid, isDrop) {
    noFill();
    strokeWeight(1.3);
    let layers = 8;
    for (let i = 0; i < layers; i++) {
        push();
        let speedMult = map(i, 0, layers, 2.0, 0.3);
        rotate(tOffset * speedMult + (i * 0.3));
        let size = 180 + (i * 35) + (mid * 130);
        let alpha = map(i, 0, layers, 180, 20);
        
        if (isDrop) {
            stroke(colRebirth.levels[0], colRebirth.levels[1], colRebirth.levels[2], alpha);
        } else {
            stroke(255, alpha * (0.3 + bass));
        }
        
        beginShape();
        for (let a = 0; a < TWO_PI; a += TWO_PI / 3) {
            vertex(cos(a) * size, sin(a) * size);
        }
        endShape(CLOSE);
        pop();
    }
}

function drawSolarCorona(bass, vol) {
    push();
    let rBase = 150 + (bass * 50); 
    for (let j = 0; j < 6; j++) {
        let alpha = map(j, 0, 6, 150, 10);
        let inter = map(j, 0, 6, 0, 1);
        let col = lerpColor(lerpColor(colSunCore, colSunMid, inter), colSunOut, inter * 0.5);
        fill(col.levels[0], col.levels[1], col.levels[2], alpha * (0.4 + bass));
        noStroke();
        beginShape();
        for (let a = 0; a < TWO_PI; a += 0.15) {
            let xoff = map(cos(a + tOffset), -1, 1, 0, 1.8);
            let yoff = map(sin(a + tOffset), -1, 1, 0, 1.8);
            let n = noise(xoff + j * 0.2, yoff + j * 0.2, tOffset * 1.2);
            let r = rBase + map(n, 0, 1, -60, 60) * (1 + vol * 5);
            vertex(r * cos(a), r * sin(a) * 0.96);
        }
        endShape(CLOSE);
    }
    pop();
}

function drawPhoenixWings(bass, vol, high) {
    push();
    stroke(colRebirth.levels[0], colRebirth.levels[1], colRebirth.levels[2], 180 * (0.2 + bass));
    noFill();
    strokeWeight(1.5 + bass * 3);
    let wingSpan = 250 + (bass * 150) + (vol * 100);
    let wingHeight = 400 + (bass * 200);

    // Ala Derecha
    beginShape();
    for (let a = -PI/2; a < PI/2; a += 0.1) {
        let xoff = map(cos(a + tOffset * 0.5), -1, 1, 0, 2);
        let yoff = map(sin(a + tOffset * 0.5), -1, 1, 0, 2);
        let n = noise(xoff, yoff, tOffset);
        let r = wingSpan * random(0.8, 1.2);
        let x = r * cos(a) * n;
        let y = wingHeight * sin(a);
        curveVertex(x, y);
    }
    endShape();

    // Ala Izquierda
    beginShape();
    for (let a = PI/2; a < 3*PI/2; a += 0.1) {
        let xoff = map(cos(a - tOffset * 0.5), -1, 1, 0, 2);
        let yoff = map(sin(a - tOffset * 0.5), -1, 1, 0, 2);
        let n = noise(xoff, yoff, tOffset + 10);
        let r = wingSpan * random(0.8, 1.2);
        let x = r * cos(a) * n;
        let y = wingHeight * sin(a);
        curveVertex(x, y);
    }
    endShape();
    pop();
}

function drawScanlines() {
    stroke(0, 45); 
    for (let i = 0; i < height; i += 5) line(0, i, width, i);
}

document.getElementById('playBtn').addEventListener('click', () => {
    document.getElementById('fileInput').click();
});

document.getElementById('fileInput').addEventListener('change', (e) => {
    let file = e.target.files[0];
    if (file) {
        let url = URL.createObjectURL(file);
        if (song) song.stop();
        song = loadSound(url, () => {
            userStartAudio();
            document.getElementById('ui').classList.add('hidden');
            song.play();
        });
    }
});

function windowResized() { resizeCanvas(windowWidth, windowHeight); }
</script>
</body>
</html>
```
#### Enlace: 
https://editor.p5js.org/Hannanah06/full/SKMcQPxlQ

<img width="1865" height="988" alt="image" src="https://github.com/user-attachments/assets/edb96b52-5edb-405c-b570-05def0cb2f77" />

<img width="1917" height="1011" alt="Captura de pantalla 2026-04-17 035758" src="https://github.com/user-attachments/assets/52784b93-e8d4-4de6-b602-d54f48aa37b4" />


## Bitácora de reflexión
