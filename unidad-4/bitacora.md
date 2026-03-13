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

### Actividad 06

### Actividad 07

### Actividad 08

### Actividad 09

### Actividad 10


## Bitácora de aplicación 
### Actividad 11


## Bitácora de reflexión


