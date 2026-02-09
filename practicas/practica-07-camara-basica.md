# Práctica 07 – Cámara básica en Unity 3D

## 🎯 Objetivo
Conocer las principales opciones de la cámara en Unity y entender cómo afectan a lo que se ve en pantalla.

---

## 🛠️ Preparación del proyecto
1. Crear un proyecto **3D** en Unity.
2. Crear una escena llamada `CamaraBasica`.
3. Guardar la escena en la carpeta `Scenes`.

---

## 📦 Escena base
1. Añade un **Plane** como suelo.
2. Añade varios objetos 3D (Cube, Sphere, Capsule).
3. Coloca los objetos a distintas distancias:
   - Uno muy cerca de la cámara
   - Otros a media distancia
   - Alguno bastante lejos

---

## 📷 Trabajo con la cámara

### 1️⃣ Posición y rotación
1. Selecciona la **Main Camera**.
2. Muévela y rótala hasta que se vea bien la escena.
3. Observa cómo cambia lo que se ve al:
   - Subir la cámara
   - Bajarla
   - Girarla

👉 **Qué debe pasar:**  
La cámara decide desde dónde se ve la escena y qué entra en pantalla.

---

### 2️⃣ Projection
1. En la cámara, cambia **Projection** a:
   - `Perspective`
   - `Orthographic`
2. Observa la diferencia entre ambas.

👉 **Qué debe pasar:**  
- En *Perspective*, los objetos lejanos se ven más pequeños.  
- En *Orthographic*, el tamaño no depende de la distancia.

---

### 3️⃣ Field of View (solo en Perspective)
1. Asegúrate de estar en **Perspective**.
2. Cambia el **Field of View** a:
   - 40
   - 60
   - 90

👉 **Qué debe pasar:**  
- Valores bajos hacen efecto “zoom”.
- Valores altos hacen efecto “gran angular”.

---

### 4️⃣ Clipping Planes
1. Modifica el **Near Clip Plane**:
   - Prueba valores bajos (0.1 – 0.3)
   - Prueba valores más altos (1 o más)
2. Modifica el **Far Clip Plane**:
   - Prueba 50
   - Prueba 500

👉 **Qué debe pasar:**  
- Algunos objetos pueden desaparecer si están demasiado cerca o demasiado lejos.
- La cámara solo renderiza lo que está entre el Near y el Far.

---

### 5️⃣ Clear Flags
1. Cambia **Clear Flags** a:
   - Skybox
   - Solid Color
2. Si usas Solid Color, cambia el color de fondo.

👉 **Qué debe pasar:**  
La cámara limpia la pantalla antes de dibujar la escena.

---

## ✅ Idea clave
La cámara **no es el jugador**, es el punto de vista.  
Cambiar sus valores puede hacer que el mismo escenario se vea completamente distinto.

