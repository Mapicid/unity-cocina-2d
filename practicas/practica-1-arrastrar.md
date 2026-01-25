# 🧪 Práctica 1 — Arrastrar un objeto con el ratón

## Objetivo
Aprender a:
- Crear y usar un script en Unity
- Entender qué es un evento de Unity
- Arrastrar un GameObject con el ratón

Al finalizar la práctica, el jugador podrá arrastrar una zanahoria por la pantalla.

---

## Conceptos que se trabajan
- GameObject
- Componentes
- Script como componente
- Eventos de Unity (OnMouseDown, OnMouseDrag)
- Collider 2D

---

## Preparación de la escena

### 1️⃣ Crear el GameObject
En la escena debe existir un GameObject llamado Zanahoria.

Debe tener:
- Transform (automático)
- Sprite Renderer (para que se vea la imagen)
- Un sprite asignado (zanahoria u otro alimento)

---

### 2️⃣ Añadir el Collider
Selecciona Zanahoria y añade el componente BoxCollider2D.

IMPORTANTE:  
Sin un BoxCollider2D, los eventos de ratón NO funcionan.

---

## Crear el script

### 3️⃣ Crear el archivo C#
En Unity:
1. Ir a la carpeta Assets/scripts
2. Click derecho → Create > C# Script
3. Nombre EXACTO del script: ArrastrarObjeto

---

### 4️⃣ Código del script
```md
Este script debe guardarse con el nombre ArrastrarObjeto.cs
Abrir ArrastrarObjeto.cs y escribir el siguiente código:
```csharp
using UnityEngine;

public class ArrastrarObjeto : MonoBehaviour
{
    private Vector3 offset;

    void OnMouseDown()
    {
        offset = transform.position - GetMouseWorldPos();
    }

    void OnMouseDrag()
    {
        transform.position = GetMouseWorldPos() + offset;
    }

    Vector3 GetMouseWorldPos()
    {
        Vector3 mousePoint = Input.mousePosition;
        mousePoint.z = 0;
        return Camera.main.ScreenToWorldPoint(mousePoint);
    }
}
```
---

## 🔗 Asignar el script al GameObject
- Arrastrar el script ArrastrarObjeto desde la carpeta scripts
- Soltarlo sobre el GameObject Zanahoria
- Comprobar que aparece como componente en el Inspector

---

## ▶️ Probar el juego
1. Pulsar Play
2. Hacer click sobre la zanahoria
3. Arrastrarla por la pantalla

---

## ✅ Resultado esperado
- La zanahoria se mueve siguiendo el ratón
- No hay errores en la consola
- El objeto responde al click y al arrastre

---

## ❌ Errores comunes
- No añadir BoxCollider2D
- No asignar el script al GameObject
- Tener errores rojos en la consola

---

## 🧠 Qué hemos aprendido
- Un script es un componente
- Los eventos de Unity son métodos especiales
- Unity ejecuta automáticamente OnMouseDown y OnMouseDrag
- El comportamiento depende de los componentes del GameObject

---

## 🚀 Siguiente práctica
En la siguiente práctica se trabajará con:
- Collider2D
- Is Trigger
- Detección de entrada en una zona

