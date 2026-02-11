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
**1)** 



## Bitácora de aplicación 



## Bitácora de reflexión
