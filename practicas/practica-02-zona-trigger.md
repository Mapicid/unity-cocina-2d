# Práctica 02 — Zonas + Is Trigger (detectar entrada)

## Objetivo
Crear una zona (por ejemplo Verduras) que detecte cuando un alimento entra en ella
usando Collider2D y la opción Is Trigger.

Al finalizar la práctica, al meter la Zanahoria en la zona, se mostrará un mensaje en la Console.

---

## Conceptos que se trabajan
- BoxCollider2D
- Is Trigger
- Eventos 2D (OnTriggerEnter2D)
- Separación de roles: objeto arrastrable vs zona

---

## Preparación de la escena

### 1️⃣ Crear la zona Verduras
En la ventana Hierarchy:
1. Click derecho
2. 2D Object → Sprite → Square
3. Renombrar el objeto a: ZonaVerduras
4. Cambiar su tamaño desde Transform → Scale  
   (por ejemplo Scale X = 4, Y = 2, Z=1, Position X=5, Y=3, Z=0) para que sea una zona grande

---

### 2️⃣ Añadir Collider a la zona y activar Trigger
Selecciona el GameObject ZonaVerduras y añade:
- BoxCollider2D

En el componente BoxCollider2D:
- Activar la opción Is Trigger (✔)

---

### 3️⃣ Comprobar el objeto Zanahoria
Selecciona Zanahoria y comprueba que tiene:
- BoxCollider2D
- Script ArrastrarObjeto

---

## Crear el script de detección

### 4️⃣ Crear el archivo C#
En Unity:
1. Ir a Assets/scripts
2. Click derecho → Create → C# Script (MonoBehaviour Script)
3. Nombre del script: DetectarEntrada

---

### 5️⃣ Código del script
Abrir DetectarEntrada.cs y escribir el siguiente código:

```csharp
using UnityEngine;

public class DetectarEntrada : MonoBehaviour
{
    void OnTriggerEnter2D(Collider2D other)
    {
        Debug.Log("Ha entrado: " + other.name);
    }
}
```

## 🔗 Asignar el script a la zona

### 6️⃣ Asignar el script a la zona
- Arrastrar DetectarEntrada.cs sobre el GameObject ZonaVerduras
- Comprobar que aparece como componente en el Inspector

---

## ▶️ Probar el juego
1. Pulsar Play
2. Arrastrar Zanahoria dentro de ZonaVerduras

---

## ✅ Resultado esperado
- En la Console aparece un mensaje tipo:
  Ha entrado: Zanahoria

---

## ❌ Errores comunes
---

Para que el evento `OnTriggerEnter2D` funcione correctamente, **no basta solo con Colliders**.

⚠️ **Es obligatorio que al menos uno de los dos objetos tenga un Rigidbody2D**.

En este proyecto se recomienda añadirlo al objeto **Zanahoria**.

Pasos:
1. Seleccionar el GameObject Zanahoria
2. Add Component → Rigidbody2D
3. Configurar:
   - Body Type: Kinematic
   - Gravity Scale: 0

Sin Rigidbody2D, el método `OnTriggerEnter2D` **no se ejecuta** y no aparece ningún mensaje en la consola,
aunque los colliders y el trigger estén bien configurados.

---

