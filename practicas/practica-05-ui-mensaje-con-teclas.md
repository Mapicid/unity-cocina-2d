# Práctica 05 – Mostrar y ocultar mensaje con teclas

## Objetivo
Aprender a detectar la pulsación de teclas y mostrar u ocultar un mensaje en pantalla usando la interfaz de usuario (UI) de Unity.

---

## Conceptos que se trabajan
- Método `Update()`
- Entrada por teclado (`Input.GetKeyDown`)
- Activar y desactivar objetos (`SetActive`)
- Uso de UI (Canvas y Text)
- Referencias desde el Inspector

---

## Preparación de la escena

1. Crear un proyecto en Unity (2D o 3D).
2. En la jerarquía:
   - `GameObject > UI > Canvas`
   - Dentro del Canvas: `UI > Text - TextMeshPro`
3. Cambiar el texto por:
   > Pulsa M para mostrar el mensaje  
   > Pulsa N para ocultarlo
4. **Desactivar el objeto del texto** desde el Inspector.
5. Crear un **GameObject vacío** llamado `GameManager`.

---

## Script

Crear un script llamado `ControlMensaje.cs` y asignarlo al objeto `GameManager`.

```csharp
using UnityEngine;

public class ControlMensaje : MonoBehaviour
{
    public GameObject mensaje;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.M))
        {
            mensaje.SetActive(true);
        }

        if (Input.GetKeyDown(KeyCode.N))
        {
            mensaje.SetActive(false);
        }
    }
```}

