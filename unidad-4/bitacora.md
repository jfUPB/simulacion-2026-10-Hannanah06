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



### Actividad 03

### Actividad 04

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

### Actividad 09

### Actividad 10


## Bitácora de aplicación 
### Actividad 11


## Bitácora de reflexión






