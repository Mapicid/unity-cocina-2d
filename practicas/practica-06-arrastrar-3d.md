# Práctica 06 – Arrastrar y soltar un objeto 3D

En esta práctica crearás una mini demo en Unity donde podrás **arrastrar un objeto 3D (por ejemplo un cubo)** con el ratón y **soltarlo** en la escena.

---

## Objetivo

- Seleccionar un objeto 3D con el ratón.
- Arrastrarlo por la escena (sobre un plano horizontal).
- Soltarlo al dejar de pulsar.

---

## Requisitos

- Proyecto Unity (3D).
- Un objeto 3D con **Collider** (por ejemplo, `Cube` con `BoxCollider`).
- Cámara con etiqueta **MainCamera**.

---

## Pasos

### 1) Preparar la escena
1. Crea una escena nueva llamada: `practica-06-arrastrar-3d`.
2. Añade un **Plane**: `GameObject > 3D Object > Plane`.
3. Añade un **Cube**: `GameObject > 3D Object > Cube`.
4. Coloca el cubo por encima del plano (por ejemplo `Y = 0.5`).
5. Verifica que:
   - El cubo tiene `BoxCollider` (lo trae por defecto).
   - La cámara tiene tag `MainCamera`.

---

### 2) Crear el script
1. Crea la carpeta: `Assets/Scripts/`
2. Crea el script: `DragAndDrop3D.cs`
3. Pega el código del script (incluido en esta práctica).
4. Arrastra el script al **Cube** para añadirlo como componente.

---

### 3) Probar
1. Pulsa **Play**.
2. Haz click sobre el cubo.
3. Sin soltar el click, mueve el ratón: el cubo debe seguirlo.
4. Suelta el click: el cubo se queda en su posición.

---

## Retos (opcional)
- Añade un segundo cubo y comprueba que ambos se pueden arrastrar.
- Cambia `dragPlaneY` para arrastrar a otra altura.
- Haz que el objeto cambie de color mientras se arrastra.

---

## Entrega
- Captura de pantalla o vídeo corto mostrando el arrastre.
- Explicación breve (2–3 líneas) de cómo funciona el script.

