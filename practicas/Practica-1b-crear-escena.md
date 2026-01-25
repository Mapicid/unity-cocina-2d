# Práctica 1B — Crear la escena y probar el arrastre

## Objetivo
Crear los GameObjects necesarios en la escena y probar el script
ArrastrarObjeto creado en la práctica anterior.

Al finalizar la práctica, el jugador podrá arrastrar un objeto con el ratón.

---

## Preparación de la escena

### 1️⃣ Abrir la escena
En la ventana Project:
- Ir a Assets / Scenes
- Hacer doble clic sobre la escena (por ejemplo Cocina Scene)

La escena debe mostrarse en el editor y en la Hierarchy debe aparecer:
- Main Camera

---

### 2️⃣ Crear el GameObject Zanahoria
En la ventana Hierarchy:
1. Click derecho
2. 2D Object → Sprite → Square
3. Renombrar el objeto a Zanahoria

Debe verse un cuadrado blanco en la escena.

---

### 3️⃣ Añadir componentes a Zanahoria
Seleccionar el GameObject Zanahoria y comprobar en el Inspector que tiene:

- Transform (automático)
- Sprite Renderer

Añadir además:
- BoxCollider2D

---

### 4️⃣ Asignar el script ArrastrarObjeto
Desde la ventana Project:
- Arrastrar ArrastrarObjeto.cs
- Soltarlo sobre el GameObject Zanahoria

El Inspector debe mostrar:
- ArrastrarObjeto como componente

---

### Configuración del sistema de Input (IMPORTANTE)

Para que el arrastre con el ratón funcione correctamente, Unity debe tener
activado el sistema de entrada antiguo y el nuevo.

En Unity:

1. Ir a `Edit → Project Settings…`
2. Seleccionar `Player`
3. Abrir `Other Settings`
4. Buscar `Active Input Handling`
5. Seleccionar:
   - **Both**  
     (Input Manager (Old) + Input System Package)

Unity pedirá reiniciar el editor.
Aceptar **Restart**.

⚠️ Si no se realiza este paso, el objeto no se moverá aunque el script esté bien.

## ▶️ Probar el juego

1. Pulsar el botón Play
2. Hacer click sobre el objeto Zanahoria
3. Arrastrarlo con el ratón

---

## ✅ Resultado esperado
- El objeto se mueve siguiendo el ratón
- No aparecen errores en la consola
- El script funciona correctamente

---

## ❌ Errores comunes
- No abrir la escena correcta
- No añadir BoxCollider2D
- No asignar el script al GameObject
- Tener errores en la consola

---

## Qué hemos aprendido
- Los scripts no funcionan solos
- Un script debe asignarse a un GameObject
- El comportamiento depende de los componentes del objeto

