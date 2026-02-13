# Unidad 2

## Bitácora de proceso de aprendizaje
### Actividad 01
El trabajo que más me gustó fue "Crab People" de **Raven Kwok**

### Actividad 02
#### 1) ¿Cómo funciona la suma dos vectores en p5.js?
**Respuesta:** La suma de vectores en p5.js se realiza mediante el uso de la clase especializada **p5.Vector**, ya que la biblioteca no permite el uso de operadores matemáticos convencionales entre objetos. Para ejecutar esta operación, se utiliza habitualmente el método **add()**, el cual suma internamente las componentes $x$, $y$ (y $z$ si aplica) de un vector a las del otro. Se puede aplicar directamente sobre un vector existente para modificarlo, como en **v1.add(v2)**, o de forma estática para generar un tercer vector resultante sin alterar los originales.

#### 2) ¿Por qué esta línea position = position + velocity; no funciona?
**Respuesta:** No funciona debido a que **JavaScript** no soporta la sobrecarga de operadores para objetos. Dado que tanto position como velocity son instancias de vectores y no simples números, el intérprete de JavaScript no sabe cómo sumar sus estructuras internas mediante el símbolo +. Al intentar hacerlo, el lenguaje suele convertir ambos objetos a cadenas de texto, resultando en un error de ejecución o en un dato inválido en lugar de realizar la suma matemática de sus coordenadas.

### Actividad 03

### Actividad 04

### Actividad 05

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


## Bitácora de aplicación 
### Actividad 09


## Bitácora de reflexión


