# PRACTICA - Flor con Python en Blender

## Introducción

En esta práctica se utiliza Python y la API bpy de Blender para generar una figura compuesta por varios círculos distribuidos alrededor de un punto central.

Se emplea una estructura while y funciones trigonométricas para calcular matemáticamente la posición de cada círculo en el plano XY.

---

## Código en Python

```python
import bpy
import math

# Configuración del entorno
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete(use_global=False)

# Definición de variables
radio = 2
angulo_actual = 0

# Paso 1: Círculo central
bpy.ops.mesh.primitive_circle_add(
    radius=radio,
    location=(0, 0, 0)
)

# Estructura while
while angulo_actual < 360:
    theta = math.radians(angulo_actual)
    x = radio * math.cos(theta)
    y = radio * math.sin(theta)

    bpy.ops.mesh.primitive_circle_add(
        radius=radio,
        location=(x, y, 0)
    )

    angulo_actual += 60
```

---

## Resultado en Blender

![Flor en Blender](flor_blender.png)

---

## Explicación

Se utiliza la fórmula matemática:

x = r cos(θ)  
y = r sen(θ)

El ángulo aumenta de 60 en 60 grados hasta completar 360°, generando seis círculos distribuidos uniformemente alrededor del círculo central.
