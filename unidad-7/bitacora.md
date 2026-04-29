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

**10) Código fuente:**  

**11) Enlace al sketch:**  

**12) Capturas:**  

## Bitácora de reflexión
