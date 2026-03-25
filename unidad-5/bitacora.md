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

### Actividad 03

### Actividad 04

## Bitácora de aplicación 


## Bitácora de reflexión
