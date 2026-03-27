# Unidad 5
## Bitácora de proceso de aprendizaje
### Actividad 01
#### Capa de comportamiento
**1. ¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?**  
En este ejemplo, cada partícula es un objeto con vectores que controlan su comportamiento:  

 ✦ **Estado Físico:** Son las variables de movimiento.        
󠀠󠀠    󠀠󠁝⋆ *position*: Ubicación en el lienzo.  
󠀠󠀠    󠀠󠁝⋆ *velocity*: Velocidad y dirección actual.  
󠀠󠀠    󠀠󠁝⋆ *acceleration*: Cambio de velocidad (fuerza aplicada).   

✦ **Estado Vital (*lifespan*):** Un valor numérico (normalmente empieza en 255) que actúa como "salud" o temporizador de visibilidad.  

**2. ¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?**  
Una partícula "muere" cuando su lifespan es menor o igual a 0.0. El sistema usa la función *isDead()* para verificar esto y eliminarla del arreglo. En cada frame se resta un valor pequeño al lifespan, lo que visualmente se traduce en un desvanecimiento (fade out) antes de desaparecer por completo.

**3. ¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.**  
El método *update()* sigue rigurosamente el modelo Motion 101 (el algoritmo básico de física en programación):  

✦ **Velocidad:** Se le suma la aceleración (*velocity.add(acceleration)*).  
✦ **Posición:** Se le suma la velocidad (*position.add(velocity)*).  
✦ **Vida:** Se reduce el lifespan (*lifespan* -= 2.0).

#### Capa de estructura
**4. ¿Quién crea las partículas? ¿En qué momento?**  
La clase *ParticleSystem* las crea, ella actúa como el administrador de la lista. En cada ejecución del ciclo *draw()*, el sistema llama a un método (usualmente *addParticle()*) que inserta una nueva instancia de *Particle* en el arreglo.  

**5. ¿Quién decide cuándo eliminar una partícula del array?**  
El *ParticleSystem*, como administrador, las elimina mediante un iterador o un ciclo *for*. Este consulta constantemente el estado de cada partícula usando la función *isDead()*.

**6. ¿Por qué se recorre el array en orden inverso para eliminar? ¿Qué pasaría si no se hiciera así?**  
Se recorre inverso porque al eliminar un elemento de un arreglo, los índices de los elementos restantes se desplazan hacia la izquierda.  
Si se elimina el elemento en el índice *i*, el que estaba en *i+1* ahora ocupa la posición *i*. El ciclo saltaría ese elemento sin revisarlo, provocando errores en el renderizado o dejando partículas "muertas" flotando.

**7. Si no eliminaras nunca las partículas, ¿Qué pasaría con la memoria y el rendimiento? Haz el experimento: comenta la línea que elimina y observa el frame rate.**  
Al comentar la línea de eliminación (*particles.remove(i)*), ocurre lo siguiente:  

✦ **Memoria:** El consumo de RAM sube linealmente de forma infinita. Cada objeto *Particle* ocupa un espacio; al no liberarlo, el programa eventualmente se queda sin memoria (Memory Leak).   

✦ **Rendimiento (Frame Rate):** Los FPS empiezan a caer drásticamente.  

La computadora tiene que procesar miles de cálculos de física (*update*) y dibujo (*display*) para partículas que ya ni siquiera son visibles. El procesador se satura y la animación se vuelve lenta o se traba.

#### Capa de visualización
**8. ¿Qué elementos visuales usa para representar una partícula?**  
**Forma y Color**. La partícula se representa mediante un círculo simple (*ellipse*). Su relleno (*fill*) y su contorno (*stroke*) utilizan un tono de gris fijo, pero el componente crítico es el cuarto parámetro del color: el canal alfa o transparencia.  

**9. ¿Cómo se conecta el “tiempo de vida” con la apariencia visual?**  
El valor de *lifespan* (que baja de 255 a 0) se asigna directamente a la transparencia. Esto hace que la partícula se vea sólida al "nacer" y se desvanezca gradualmente hasta volverse invisible justo antes de ser eliminada del arreglo.

**10. Si quisieras cambiar la representación visual (por ejemplo, usar líneas en vez de círculos), ¿Qué cambiarías y qué NO cambiarías?**  
✦ **Cambiaría:** Únicamente el código dentro del método *display()*. Reemplazaría *ellipse*(*position.x*, *position.y*, 8, 8) por algo como *line*(*position.x*, *position.y*, *position.x* + *velocity.x*, *position.y* + *velocity.y*).  

✦ **NO Cambiaría:** Toda la lógica de física y control. El patrón Motion 101 (aceleración, velocidad, posición), el cálculo del *lifespan* y el sistema de eliminación en el *ParticleSystem* seguirían siendo exactamente iguales, ya que la "vida" de la partícula es independiente de cómo se dibuja.

### Actividad 02
#### Comparación con Example 4.2
**1. ¿Qué responsabilidades que antes estaban en *draw()* ahora están dentro de la clase *Emitter*?**  
Antes (en 4.2), el *draw()* principal tenía que ocuparse de crear cada partícula individual, guardarla en un arreglo y llamar a sus métodos de actualización uno por uno. Ahora (en 4.4), el *draw()* solo le dice al **Emitter** (o *ParticleSystem*) "actualízate". La responsabilidad de crear nuevas partículas, decidir su posición de origen y gestionar su ciclo de vida interno ahora recae totalmente dentro de la clase *Emitter*.

**2. ¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?**  
La organización y reutilización. Al separar la lógica, el código principal queda mucho más limpio. Además, esto permite tener múltiples fuentes de partículas en diferentes lugares de la pantalla sin tener que escribir código repetido; cada "emisor" es independiente y autónomo.

**3. En este ejemplo hay un array de emitters. ¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?**  
✦ **Emitters:** Son creados por el sketch principal (usualmente en el *setup()* o al hacer clic con el mouse). Se guardan en un arreglo global de sistemas.  

✦ **Partículas:** Son creadas por cada instancia de Emitter. Cada emisor tiene su propio arreglo interno de partículas que gestiona de forma privada.

**4. Dibuja un diagrama que muestre la jerarquía: sketch → [emitters] → [partículas]. ¿Cuántos niveles de “colección” hay?**  
**Nivel 0: El Sketch (p5.js)**  
Es el contenedor global que corre el programa.  
↓  
**Nivel 1 de Colección: Array de Emitters**  
El Sketch guarda una lista (ej. *ArrayList*<*ParticleSystem*>) que contiene varios emisores.  
↓  
**Nivel 2 de Colección: Array de Partículas (dentro de cada Emitter)**  
Cada emisor, a su vez, guarda su propia lista privada de objetos *Particle*.  
↓  
**Objetos Finales: Partículas individuales**  
Son los elementos que finalmente vemos moverse y desvanecerse en la pantalla.  

#### Transferencia conceptual
**5. Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.**  
✦ **El Emisor como Entidad:** Es una entidad de control que gestiona una colección de objetos menores. Su función es crear cada unidad, definir su estado inicial (posición y movimiento) y monitorear su ciclo de vida.  

✦ **Dinámica de la Unidad:** Cada elemento dentro de la colección altera su estado bajo la influencia de una fuerza constante. A medida que avanza su ciclo de vida, la unidad se degrada hasta ser removida del sistema.  

✦ **Jerarquía Global:** El modelo es una colección de emisores independientes. Cada uno procesa su propio grupo de unidades sin interferir con el estado o la fuerza que afecta a los demás.

### Actividad 03
**1. ¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?**  
Lo que tienen en común es que todas heredan de la clase base *Particle*. Comparten el mismo estado físico (posición, velocidad, aceleración) y el mismo ciclo de vida (*lifespan* e *isDead()*).  
Lo que tienen de diferente es su apariencia visual y su comportamiento específico. Mientras una se dibuja como un círculo simple, la otra (la subclase) puede tener una rotación propia o una forma distinta (como un cuadrado).

**2. ¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando? Explica esto con tus propias palabras.**  
Es importante porque permite que el Emitter sea genérico y eficiente. El emisor solo sabe que tiene una "colección de partículas"; no le importa si son círculos, cuadrados o estrellas. Esto significa que el emisor puede dar una orden única (como "dibújense") y cada partícula sabrá cómo hacerlo a su manera. Sin esto, tendrías que escribir un código diferente para cada tipo de objeto, lo cual sería un caos.

**3. Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?**  
✦ **¿Qué tendría que crear?:** Una nueva subclase (ej. *StarParticle*) que extienda de *Particle* y que solo defina su propio método *display()*.  

✦ **¿Qué NO tendría que modificar:** No tocaría para nada la clase *Particle* original, ni la lógica interna del *Emitter*, ni el sistema de física. El sistema ya está preparado para aceptar cualquier cosa que sea una "partícula".

**4. Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?**  
La lógica del Emitter no cambió; el emisor sigue añadiendo, actualizando y eliminando objetos de la misma forma. La lógica de muerte tampoco cambió, ya que el chequeo de *lifespan* <= 0 sigue siendo idéntico para todos.  
La capa de gestión (Emitter) y la de física (Motion 101) permanecieron intactas. La única capa que se modificó fue la de definición de objetos, permitiendo que una sola lista contenga múltiples formas gracias a la herencia.

### Actividad 04
#### Fuerzas globales vs. locales
**1. En Example 4.6, ¿Dónde se define la gravedad? ¿Quién la aplica a las partículas? ¿Es una fuerza global o local?**  
✦ **Definición:** La gravedad se define como un objeto *PVector* dentro del sketch principal (*draw()*).  

✦ **Aplicación:** El sketch principal recorre el sistema de partículas y le pasa la fuerza a través de una función (como *applyForce()*).  

✦ **Alcance:** Es una fuerza global, ya que afecta por igual a todas las partículas del sistema sin importar su posición.  

**2. En Example 4.7, ¿Qué diferencia hay entre la gravedad y la fuerza del repeller? ¿Dónde “vive” cada una?**  
La diferencia es que la gravedad es constante y uniforme (siempre empuja igual hacia abajo). El repeller es una fuerza variable que depende de la posición; empuja más fuerte si la partícula está cerca y nada si está lejos.  
La gravedad "vive" en el sketch principal como una variable suelta. El repeller "vive" como un objeto independiente (clase *Repeller*) con su propia posición y fuerza.  

**3. La fuerza del repeller depende de la distancia entre la partícula y el repeller. ¿Qué principio físico se está modelando?**  
Se está modelando la Ley de la Inversa del Cuadrado (similar a la fuerza eléctrica o gravitacional real). El principio dicta que la magnitud de la fuerza disminuye rápidamente a medida que aumenta la distancia entre los dos cuerpos. En el código, esto se calcula normalizando el vector de distancia y dividiéndolo por la magnitud al cuadrado.

**4. ¿Cambió la clase Particle entre Example 4.6 y 4.7? ¿Qué implica esto sobre la separación entre comportamiento de la partícula y fuerzas externas?**  
La clase *Particle* no cambió. Esto demuestra una separación total entre el objeto y su entorno. La partícula es un receptor pasivo: ella solo sabe cómo "recibir" una fuerza y sumarla a su aceleración, pero no necesita saber de dónde viene esa fuerza (si es gravedad, viento o un repeller). Esto permite añadir cientos de fuerzas externas sin tener que reescribir el código de la partícula cada vez.

## Bitácora de aplicación 
### Actividad 05 𓇢𓆸🐐⋆.🌱ೃ࿔🦁*:･
**1. Concepto:** Al leer que la entrega era sobre el ciclo de la vida, lo primero que vino a mi mente fue la película "El rey león", de Disney. En una escena en particular, Mufasa le muestra a Simba el reino y comienza a hablarle sobre lo que es ser rey, diciéndole que "Todos estamos conectados en el ciclo de la vida", haciendo referencia a que todos somos necesarios en el ecosistema para seguir viviendo y debemos respetar ese balance natural.

Representaré el ciclo del que habla Mufasa en la película, en el que un ser alimenta la tierra al morir (el león) para que otros animales se alimenten con sus nutrientes (antílopes) y así estos también puedan servir de alimento (para los leones nuevamente). Lo escogí porque esa idea de que "todos cumplimos un papel" me hace sentir valiosa y quiero que los demás también lo sientan.

**2. Bocetos:**
<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/babbce4e-0b1c-4d9b-8fb7-3f135e61b788" />
<img width="1920" height="1080" alt="2" src="https://github.com/user-attachments/assets/44df68ef-76b1-47a6-9bd4-435aadacc6f9" />
<img width="1920" height="1080" alt="3" src="https://github.com/user-attachments/assets/3e7a85c6-7109-436a-afa1-6bdc411775d0" />


**3. Mapa de decisiones**


**Código:**  
**-Sketch**
```js
let manager;
let iniciado = false;

function setup() {
  createCanvas(windowWidth, windowHeight);
  textFont('Georgia');
  manager = new SceneManager();
}

function draw() {
  if (!iniciado) {
    pantallaInicio();
    return;
  }
  manager.update();
  manager.draw();
}

// ── Pantalla de inicio ────────────────────────────────────

function pantallaInicio() {
  background(8, 12, 8);

  // Título
  fill(255); noStroke();
  textAlign(CENTER, CENTER);
  textSize(32); textStyle(BOLD);
  text('El Ciclo de la Vida', width/2, height/2 - 70);

  // Botón
  let bx = width/2 - 85, by = height/2 + 44, bw = 170, bh = 44;
  let hover = mouseX > bx && mouseX < bx+bw && mouseY > by && mouseY < by+bh;
  noStroke();
  fill(hover ? color(58,120,58) : color(42,96,42));
  rect(bx, by, bw, bh, 4);
  fill(hover ? 255 : color(180,240,180));
  textSize(15); textStyle(NORMAL);
  text('Comenzar', width/2, by + bh/2 + 1);
}

// ── Eventos de mouse ──────────────────────────────────────

function mousePressed() {
  if (!iniciado) {
    let bx = width/2 - 85, by = height/2 + 44, bw = 170, bh = 44;
    if (mouseX > bx && mouseX < bx+bw && mouseY > by && mouseY < by+bh) {
      iniciado = true;
      manager.iniciarEscena1();
    }
    return;
  }
  manager.mousePressed(mouseX, mouseY);
}

function mouseDragged() {
  if (iniciado) manager.mouseDragged(mouseX, mouseY);
}

function mouseReleased() {
  if (iniciado) manager.mouseReleased();
}

// ── Responsive ────────────────────────────────────────────

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

**Resto de códigos:** https://editor.p5js.org/Hannanah06/sketches/Dq2axlnea

**Enlace:** https://editor.p5js.org/Hannanah06/full/Dq2axlnea


<img width="1224" height="709" alt="Captura de pantalla 2026-03-27 032110" src="https://github.com/user-attachments/assets/3f985341-82ec-4fa7-8b78-23fcc2ebd4ab" />
<img width="1072" height="673" alt="Captura de pantalla 2026-03-27 032130" src="https://github.com/user-attachments/assets/30ab0a52-e7c7-4333-b37d-5f222f386aea" />
<img width="790" height="654" alt="image" src="https://github.com/user-attachments/assets/b311faa4-5622-46fb-9b2b-ed7d7d520fca" />

## Bitácora de reflexión
