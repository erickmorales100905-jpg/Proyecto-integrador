# Proyecto-integrador

Realiza un repositorio para explicar el proyecto integrador de la unidad 1.
El proyecto esta basado en la tarea Escenario Procedural agregando la animación de la cámara a través del camino. 
Como entrega, debes adjuntar el url del repositorio.

INTRODUCCIÓN

Este código es un script en Python para Blender que crea automáticamente un escenario 3D con forma de pasillo recto que luego se curva, le añade materiales, luces, una cámara animada 
y un pequeño movimiento de vibración (shake) a la cámara.
Sirve para automatizar una escena sin tener que construirla manualmente objeto por objeto.


Este script sirve para:

Generar un escenario 3D procedural (hecho por código).
Crear paredes rectas y curvas automáticamente.
Asignar materiales a las paredes.
Añadir luces para iluminar la escena.
Colocar una cámara y animarla recorriendo el pasillo.
Simular un movimiento de cámara tipo “handheld” con vibración.
Preparar una escena lista para renderizar o hacer una animación.


Es útil para:
Prácticas de programación en Blender.
Escenas tipo túnel o pasillo.
Animaciones automáticas.
Proyectos de simulación o visualización.

¿CÓMO FUNCIONA?
1. Importación de librerías
   
//import bpy
//import math

bpy controla Blender.
math se usa para senos, cosenos y ángulos de la parte curva.

2. Función crear_material
def crear_material(nombre, color_rgb):

Esta función crea un material nuevo.
Usa nodos.
Busca el shader Principled BSDF.
Cambia el color y la rugosidad.
Sirve para reutilizar materiales sin repetir código.

3. Función generar_escenario

Primero borra todo:

//bpy.ops.object.select_all(action='SELECT')
//bpy.ops.object.delete()

Luego crea dos materiales:
Uno oscuro.
Uno de color rojo.

Define medidas:

largo_pasillo = 10
ancho_pasillo = 4
radio_curva = 12

4. Tramo recto
for i in range(largo_pasillo):

Crea cubos a la izquierda y derecha formando paredes.
Algunas paredes:
Cambian de color.
Algunas son más altas (escala Z).

5. Tramo curvo

Aquí usa trigonometría:

//math.cos()
//math.sin()

para colocar cubos en forma de arco, creando una curva de 90 grados.

6. Suelo
bpy.ops.mesh.primitive_plane_add()
Crea un plano grande como piso y lo escala.

7. Luces

Agrega:
Una luz tipo Sol.
Dos luces tipo Point.
Les asigna energía para iluminar la escena.

8. Cámara
Crea una cámara:
Al inicio del pasillo.
Apunta hacia adelante.
Define duración de la animación (250 frames).
Inserta keyframes:
En el tramo recto.
En la curva.
Así la cámara se mueve siguiendo el pasillo.

9. Movimiento de vibración (shake)

Función:
def agregar_shake(obj):

Busca las curvas de animación (location y rotation)
y les añade un modificador NOISE, que provoca vibración leve.

10. Ejecución
generar_escenario()

Esto ejecuta todo el script y construye la escena completa.

Codigo fuente

<img width="836" height="983" alt="image" src="https://github.com/user-attachments/assets/5cb23400-70b5-4614-b3a0-5bc05c3880ab" />
<img width="900" height="973" alt="image" src="https://github.com/user-attachments/assets/a93d8a9c-57e8-497c-8373-e5aef90eade4" />
<img width="788" height="331" alt="image" src="https://github.com/user-attachments/assets/6cfb466f-d258-4541-9635-4322a57285d2" />

Vista de la curva 

<img width="1152" height="796" alt="image" src="https://github.com/user-attachments/assets/f7f37a1b-59a5-47a6-b5f7-2dcf082fedce" />

<img width="1156" height="805" alt="image" src="https://github.com/user-attachments/assets/7b1e51b1-5b2b-4e94-857d-ee7e4f3b412e" />

