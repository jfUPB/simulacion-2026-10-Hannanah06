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

## Bitácora de reflexión
