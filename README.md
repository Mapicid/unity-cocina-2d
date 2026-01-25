# Unity Cocina 2D – Proyecto Drag & Drop

Proyecto educativo para aprender los conceptos básicos de Unity 2D mediante un juego
de cocina en el que hay que arrastrar alimentos a su categoría correcta.

Ejemplo:
- Arrastrar una 🥕 zanahoria
- Soltarla en la zona **Verduras**
- El juego indica si es correcto o incorrecto

---

## Conceptos IMPORTANTES de Unity (imprescindibles)

### 1️⃣ Scene (Escena)
Es la **pantalla del juego**.  
Todo lo que se ve y ocurre está dentro de una escena.

Ejemplo: `CocinaScene`

---

### 2️⃣ GameObject
Cualquier elemento del juego es un **GameObject**:
- Un alimento
- Una zona (Verduras, Carnes…)
- Un texto en pantalla

En Unity **todo es un GameObject**.

---

### 3️⃣ Componentes
Los GameObjects no hacen nada solos.  
Su comportamiento depende de los **componentes** que tengan.

Ejemplos de componentes:
- `Transform` → Define posición, rotación y escala. No se puede borrar
- `Sprite Renderer` → muestra una imagen
- `BoxCollider2D` → detecta colisiones
- `Script` → lógica del juego
  
Todos los GameObjects tienen Transform. Los demás componentes se añaden solo si el objeto los necesita. 

---

### 4️⃣ Sprite
Un **sprite** es una imagen 2D dentro de Unity.

Ejemplos:
- Zanahoria
- Carne
- Caja de verduras

Los sprites se muestran con el componente `Sprite Renderer`.

---

### 5️⃣ Scripts (C#)
Los scripts controlan el comportamiento del juego.

En este proyecto:
- Arrastrar un alimento
- Comprobar si está en la zona correcta
- Mostrar mensajes

Ejemplo de scripts:
- `ArrastrarObjeto.cs`
- `ZonaCategoria.cs`

---

### 6️⃣ Collider 2D
Permite detectar cuándo dos objetos se tocan.

Tipos usados:
- `BoxCollider2D`

Uso:
- Alimentos → collider normal
- Zonas → collider con **Is Trigger activado**

---

### 7️⃣ Is Trigger
Cuando un collider es **Trigger**:
- No bloquea
- Solo detecta que algo entra o sale

Se usa para:
- Zonas de Verduras
- Zonas de Carnes

---

### 8️⃣ Tags (Etiquetas)
Los **tags** sirven para identificar objetos.

Ejemplos:
- `Verdura`
- `Carne`

Se usan para comprobar si un alimento es correcto o no.

---
### 9️⃣ Eventos en Unity
Unity usa métodos especiales que se ejecutan automáticamente cuando ocurre algo.

Ejemplos:
- `OnMouseDown()` → click sobre un objeto
- `OnMouseDrag()` → arrastrar con el ratón
- `OnTriggerEnter2D()` → entrar en una zona

Estos métodos se escriben dentro de un script.
Unity los llama automáticamente.

### 🔍 Inspector
Es la ventana de Unity donde se:
- Añaden componentes a los GameObjects
- Configuran sus valores
- Asignan scripts, tags y referencias

El Inspector muestra los componentes de un GameObject.

## Lógica del juego (resumen)

1. El jugador arrastra un alimento
2. El alimento entra en una zona
3. El juego comprueba:
   - ¿El tag del alimento coincide con la zona?
4. Resultado:
   - ✔ Correcto
   - ❌ Incorrecto

---
