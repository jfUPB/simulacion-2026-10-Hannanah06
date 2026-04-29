# Unidad 7

## Bitácora de proceso de aprendizaje
### Actividad 01
**1) Analiza 3 o 4 ejemplos de Ji Lee.**  
Escogí los siguientes ejemplos:
<img width="349" height="129" alt="image" src="https://github.com/user-attachments/assets/7c09bc37-5139-4175-ad05-1b13da118e18" />

<img width="421" height="235" alt="image" src="https://github.com/user-attachments/assets/8236001a-58e3-4798-8e0c-7394b3d484a0" />

<img width="411" height="110" alt="image" src="https://github.com/user-attachments/assets/c0076b6b-26e3-46ed-b398-7fa34b1c271d" />       

**2) Explica cómo la manipulación tipográfica refuerza el significado.**  
✦ **MOON:** En este diseño, la manipulación se centra en el uso de la posición y la jerarquía visual.  
- **La técnica:** La letra "O" se reduce de tamaño y se eleva para situarse en la parte superior derecha de la otra letra "O", similar a la posición de un superíndice o un exponente matemático.
- **Refuerzo del significado:** Al desplazar la "O" hacia arriba, Lee emula la posición de la luna en el cielo nocturno. Esa "O" pequeña y elevada evoca la imagen de un cuerpo celeste orbitando o suspendido en el espacio.  

✦  **DALI:** Aquí se utiliza la alteración de los trazos de las letras para crear una referencia iconográfica clara.  
- **La técnica:** Lee extiende los trazos inferiores de la letra "A" de manera curva y alargada hacia los lados, extendiéndose por debajo de la "D" y la "L".
- **Refuerzo del significado:** Esta manipulación transforma la estructura de la palabra en el rasgo físico más distintivo del artista Salvador Dalí: su icónico bigote puntiagudo y surrealista. La palabra deja de ser solo un apellido para convertirse en un retrato esquemático del personaje.  

✦ **ECLIPSE:** Este ejemplo juega con la superposición y la iluminación (contraste).
- **La técnica:** La letra "C" de la palabra se presenta como un arco delgado y brillante, mientras que el resto de las letras están en un tono gris muy oscuro, casi fundiéndose con el fondo negro.
- **Refuerzo del significado:** La manipulación visual imita exactamente el fenómeno de un eclipse solar. La "C" brillante representa el "anillo de diamante" o el último resplandor de luz solar que queda visible cuando la luna cubre el sol. El hecho de que el resto de la palabra sea apenas legible refuerza la idea de oscuridad y ocultamiento propia del evento astronómico.  

**3) Propón 2 o 3 palabras propias y esboza cómo podrían representarse visualmente.**  
<img width="1280" height="960" alt="Act01" src="https://github.com/user-attachments/assets/df115b86-a8b6-46d3-9423-6f6d7f0bf87b" />

**4) Indica cuál de esas palabras te interesa más y por qué.**  
Siento que con la palabra "Bloom" podría haber una interacción más natural, ya que las "o" serían semillas que florecen, con la ayuda del usuario.

### Actividad 02
**1) Explica con tus palabras qué hace cada uno de esos conceptos.**  

✦ **Engine (El Motor):** Es el "cerebro" o el corazón de la simulación. Su única tarea es gestionar el paso del tiempo y realizar los cálculos matemáticos necesarios para saber dónde debe estar cada objeto en el siguiente segundo. No "dibuja" nada, solo calcula las posiciones basándose en leyes físicas.  

✦ **World (El Mundo):** Si el *Engine* es el cerebro, el *World* es el escenario o el contenedor. Es el lugar donde viven todos los objetos, las fuerzas de gravedad y las restricciones. Cuando se crea un objeto, se tiene que "añadir al mundo" para que el motor sepa que debe incluirlo en sus cálculos.  

✦ **Bodies (Los Cuerpos):** Son los objetos físicos en sí mismos. Pueden ser rectángulos, círculos o polígonos personalizados. Tienen propiedades como:
- **Masa:** Qué tan pesados son.
- **Fricción:** Qué tanto se deslizan al tocar a otros.
- **Restitución:** Qué tan "rebotantes" son.
- **Static:** Si el cuerpo es estático (como un suelo que no se mueve) o dinámico (como una pelota que cae).

✦  **Constraint (La Restricción):** Establece una relación de distancia o posición entre dos puntos o dos objetos, limitando su libertad de movimiento para que actúen de forma conectada.  

✦ **MouseConstraint (Interacción con el ratón):** Es un tipo especial de restricción que permite que el usuario interactúe con el mundo físico. Básicamente, "ata" el cursor del ratón a los cuerpos físicos para que se puedan pinchar, arrastrar o lanzar dentro del escenario. Sin esto, el mundo físico ocurriría de forma autónoma sin que se pudiera tocar nada.  

## Bitácora de aplicación 
### Actividad 05 °🌸˖𓍢ִִ໋🌼*˖:･
**1) Palabra elegida.**  
La palabra que yo elegí fue "Bloom", que significa *florecer* en inglés.  

**2) Justificación conceptual.**  
Esta obra se fundamenta en la idea del crecimiento orgánico impulsado por la interacción humana. Conceptualmente, la obra explora la relación entre el cuidado y la recompensa estética. Al utilizar la metáfora de una regadera, el usuario deja de ser un espectador pasivo para convertirse en un agente vital (un "cuidador").

**3) Análisis de su significado visual y comportamental.**  

✦ **Significado Visual:**  
- **Tipografía y Vegetación:** El uso de la fuente *Fraunces* (una tipografía con serifas pronunciadas y elegantes) junto con las ramas dibujadas mediante curvas de Bézier, crea una armonía entre lo editorial y lo natural.
- **Paleta de Colores:** Se emplean colores vibrantes pero suavizados (corales, lilas, turquesas) para las flores, lo que comunica delicadeza. El rastro de partículas de agua en tonos turquesa refuerza la fluidez y la limpieza visual.
- **Composición:** La disposición central de las letras "B L M" actúa como el núcleo del jardín, donde las flores no son solo adornos, sino que completan la palabra, sugiriendo que la belleza es necesaria para la integridad del mensaje.  

✦ **Significado Conceptual:**  
- **Crecimiento por Proximidad:** El comportamiento de las flores está ligado a la cercanía de la regadera. Esto simula una "atención dirigida". Si el usuario deja de regar, el crecimiento se detiene, lo que refuerza la idea de persistencia en el cuidado.
- **Física de Partículas:** La implementación de gravedad y aceleración en las gotas de agua añade una capa de realismo físico que contrasta con la naturaleza mágica de las flores, creando un equilibrio entre lo tangible y lo fantástico.

**5) Bocetos:**  
<img width="1280" height="960" alt="Bloom" src="https://github.com/user-attachments/assets/d54efd7b-0cf2-4765-b095-b02caee52407" />  

**8) Explicación de la relación entre audio y comportamiento.**  
La integración del sonido en este proyecto no es meramente ambiental, sino reactiva y funcional:  

✦ **Feedback Sensorial:** El audio actúa como una confirmación inmediata de la interacción exitosa. Cuando el usuario riega la zona activa de la flor, el sonido de "magia misteriosa" se dispara, validando la acción de "dar vida".  

✦ **Sincronía Evolutiva:** Existe una relación directa entre el volumen y la persistencia del sonido con el estado de crecimiento. El uso de un *GainNode* para crear una rampa exponencial de volumen permite que cada "gota" sonora tenga una estela, similar a cómo el agua nutre la tierra incluso después de que cae.  

✦ **Variabilidad Orgánica:** El código altera ligeramente la velocidad de reproducción (*playbackRate*) en cada disparo. Esto evita la monotonía mecánica, haciendo que cada interacción suene única, tal como en la naturaleza nada se repite exactamente igual.

**10) Código fuente (index):**  
```js
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>BLOOM - Partículas con Física</title>
    <link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,wght@0,800;1,700&display=swap" rel="stylesheet">
    <style>
        body { margin: 0; background: #050a14; overflow: hidden; width: 100vw; height: 100vh; }
        canvas { display: block; cursor: none; }
    </style>
</head>
<body>

<canvas id="canvas"></canvas>

<script>
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');

let WIDTH, HEIGHT, T = 0, wet = false, mouse = { x: -200, y: -200 }, audioCtx = null, stars = [];
let magicSoundBuffer = null;
let waterDrops = []; // Array para las partículas de agua

async function loadMagicSound() {
    if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    try {
        const response = await fetch('Sonido de magia  misteriosa.mp3'); 
        const arrayBuffer = await response.arrayBuffer();
        magicSoundBuffer = await audioCtx.decodeAudioData(arrayBuffer);
    } catch (e) { console.error("Error audio:", e); }
}

function setupResolution() {
    const dpr = window.devicePixelRatio || 1;
    WIDTH = window.innerWidth;
    HEIGHT = window.innerHeight;
    canvas.width = WIDTH * dpr;
    canvas.height = HEIGHT * dpr;
    canvas.style.width = WIDTH + 'px';
    canvas.style.height = HEIGHT + 'px';
    ctx.scale(dpr, dpr);
    stars = Array.from({ length: 100 }, () => ({
        x: Math.random() * WIDTH, y: Math.random() * HEIGHT, 
        i: Math.random() * 10, r: Math.random() * 0.4 + 0.4
    }));
}
setupResolution();

const getBase = () => HEIGHT * 0.6; 

class Flower {
    constructor(offsetX, palette) {
        this.offsetX = offsetX;
        this.growth = 0; 
        this.palette = palette;
        this.lastNoteTime = 0;
    }
    update() {
        const x = (WIDTH / 2) + this.offsetX;
        const y = getBase() - 55;
        let dx = (mouse.x + 55) - x;
        let dy = (mouse.y + 35) - y;
        if (wet && Math.sqrt(dx*dx + dy*dy) < 100) {
            this.growth = Math.min(1, this.growth + 0.006);
            this.triggerMagicAudio();
        }
    }
    draw() {
        const x = (WIDTH / 2) + this.offsetX;
        const y = getBase() - 55;
        ctx.save();
        ctx.translate(x, y);
        let s = 0.2 + this.growth * 0.8;
        ctx.scale(s, s);
        ctx.beginPath(); ctx.arc(0,0,50,0,Math.PI*2);
        ctx.lineWidth = 18; ctx.strokeStyle = "#2c3e50";
        ctx.shadowBlur = 15; ctx.shadowColor = this.palette[0];
        ctx.stroke();
        if(this.growth > 0.01) {
            ctx.rotate(T*0.22);
            for(let i=0; i<10; i++) { ctx.rotate(Math.PI*2/10); drawPetal(25, 80*this.growth, this.palette[i%4]); }
            ctx.rotate(-T*0.8);
            for(let i=0; i<8; i++) { ctx.rotate(Math.PI*2/8); drawPetal(18, 55*this.growth, this.palette[(i+1)%4]); }
            const cG = ctx.createRadialGradient(0,0,0,0,0,15);
            cG.addColorStop(0, "gold"); cG.addColorStop(1, "#cc6600");
            ctx.fillStyle = cG; ctx.beginPath(); ctx.arc(0,0,15,0,Math.PI*2); ctx.fill();
        }
        ctx.restore();
    }
    triggerMagicAudio() {
        const now = audioCtx?.currentTime;
        if (!audioCtx || !magicSoundBuffer || now - this.lastNoteTime < 0.3) return;
        this.lastNoteTime = now;
        const source = audioCtx.createBufferSource();
        source.buffer = magicSoundBuffer;
        const g = audioCtx.createGain();
        g.gain.setValueAtTime(1.0, now);
        g.gain.exponentialRampToValueAtTime(0.001, now + 3.0);
       
        source.connect(g); g.connect(audioCtx.destination);
        source.start(0);
    }
}

const f1 = new Flower(-25, ['#ff6b6b', '#ff4d8d', '#ffb347', '#ffd93d']); 
const f2 = new Flower(115, ['#c77dff', '#e0aaff', '#7b2fff', '#48cae4']);

function drawPetal(w, l, color) {
    ctx.beginPath(); ctx.fillStyle = color;
    ctx.moveTo(0, 0);
    ctx.bezierCurveTo(w, -l*0.3, w, -l*0.7, 0, -l);
    ctx.bezierCurveTo(-w, -l*0.7, -w, -l*0.3, 0, 0);
    ctx.fill();
}

function drawSprig(x, y, angle, flip = 1) {
    ctx.save();
    ctx.translate(x, y); ctx.rotate(angle); ctx.scale(flip, 1);
    ctx.strokeStyle = "#3e623a"; ctx.lineWidth = 2.5;
    ctx.beginPath(); ctx.moveTo(0,0); ctx.lineTo(0,-30); ctx.stroke();
    for(let i=0; i<3; i++) {
        ctx.save(); ctx.translate(0, -8-i*7);
        ctx.rotate(Math.sin(T*0.7+i)*0.1);
        ctx.fillStyle = "#2c7a36";
        ctx.beginPath(); ctx.ellipse(5, 0, 7, 2.5, 0.4, 0, Math.PI*2); ctx.fill();
        ctx.restore();
    }
    ctx.restore();
}

function updateWaterParticles() {
    if (wet) {
        // Creamos 2 gotas nuevas por cada frame
        for(let i=0; i<2; i++) {
            waterDrops.push({
                x: mouse.x + 85,
                y: mouse.y + 55,
                vx: (Math.random() - 0.5) * 2, // Velocidad X aleatoria
                vy: Math.random() * 2,         // Velocidad Y inicial
                life: 1.0                      // Opacidad/Vida
            });
        }
    }
    
    // Actualizamos física de cada gota
    for (let i = waterDrops.length - 1; i >= 0; i--) {
        let p = waterDrops[i];
        p.vy += 0.2;  // Gravedad
        p.x += p.vx;
        p.y += p.vy;
        p.life -= 0.02; // Se desvanece
        if (p.life <= 0) waterDrops.splice(i, 1);
    }
}

function drawWateringCan(x, y) {
    ctx.save(); ctx.translate(x, y);
    ctx.fillStyle = "teal"; ctx.shadowBlur = 15; ctx.shadowColor = "#48cae4";
    ctx.beginPath(); ctx.roundRect(0, 0, 60, 40, 10); ctx.fill();
    ctx.strokeStyle = "teal"; ctx.lineWidth = 8;
    ctx.beginPath(); ctx.moveTo(60,30); ctx.quadraticCurveTo(80,30,90,50); ctx.stroke();
    ctx.restore();

    // Dibujamos las partículas de agua (fuera del translate de la regadera)
    waterDrops.forEach(p => {
        ctx.strokeStyle = `rgba(0, 51, 102, ${p.life})`;
        ctx.lineWidth = 2;
        ctx.beginPath();
        ctx.moveTo(p.x, p.y);
        ctx.lineTo(p.x + p.vx, p.y + p.vy);
        ctx.stroke();
    });
}

function render() {
    T += 0.016;
    const baseLine = getBase();
    const centerX = WIDTH / 2;
    const bg = ctx.createLinearGradient(0, 0, 0, HEIGHT);
    bg.addColorStop(0, '#abc4ff'); bg.addColorStop(0.5, '#d9d4f1'); bg.addColorStop(1, '#f3d1d9'); 
    ctx.fillStyle = bg; ctx.fillRect(0, 0, WIDTH, HEIGHT);

    stars.forEach(s => {
        ctx.fillStyle = `rgba(255, 255, 255, ${0.15 + Math.sin(T*0.3+s.i)*0.1})`;
        ctx.beginPath(); ctx.arc(s.x, s.y, s.r * 1.3, 0, Math.PI*2); ctx.fill();
    });

    ctx.font = "800 160px Fraunces"; ctx.textAlign = "center"; ctx.fillStyle = "#2c3e50";
    ctx.fillText("B", centerX - 280, baseLine);
    ctx.fillText("L", centerX - 165, baseLine);
    ctx.fillText("M", centerX + 270, baseLine);

    drawSprig(centerX - 280, baseLine-20, -0.4);
    drawSprig(centerX + 310, baseLine-60, 0.3, -1);

    updateWaterParticles(); // <--- Aquí corre la "física"
    f1.update(); f1.draw();
    f2.update(); f2.draw();

    drawWateringCan(mouse.x, mouse.y);
    requestAnimationFrame(render);
}

canvas.addEventListener('mousemove', e => { mouse.x = e.clientX; mouse.y = e.clientY; });
canvas.addEventListener('mousedown', () => { 
    wet = true; if(!audioCtx) loadMagicSound();
    else if (audioCtx.state === 'suspended') audioCtx.resume();
});
canvas.addEventListener('mouseup', () => wet = false);
window.addEventListener('resize', setupResolution);
render();
</script>
</body>
</html>
```

**11) Enlace al sketch:** https://editor.p5js.org/Hannanah06/full/buUki8qBG

**12) Capturas:**  
<img width="1422" height="688" alt="Captura de pantalla 2026-04-29 015537" src="https://github.com/user-attachments/assets/99d7793f-983a-43f5-9408-71378515db9f" />  
<img width="1189" height="528" alt="Captura de pantalla 2026-04-29 015556" src="https://github.com/user-attachments/assets/9c5f2dd8-8c6e-477a-b0a3-7aa2ebbc82b6" />    


<img width="1136" height="508" alt="image" src="https://github.com/user-attachments/assets/3b4b1dd0-6e22-4c9a-a839-5e18d7106d92" />  


## Bitácora de reflexión
