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

1. Crear un proyecto nuevo en Unity (2D o 3D).
   - Nombre recomendado del proyecto: `Unity_UI_Mensajes`

2. Nada más abrir el proyecto, guardar la escena:
   - Menú: **File > Save As...**
   - Carpeta: **Scenes**
   - Nombre de la escena: `EscenaPrincipal`
   - Guardar.

3. En la jerarquía, crear el Canvas:
   - Menú: **GameObject > UI > Canvas**
   - Unity creará automáticamente un objeto `Canvas` y un `EventSystem`.

4. Dentro del Canvas, crear el texto del mensaje:
   - Seleccionar el objeto **Canvas**
   - Menú: **GameObject > UI > Text - TextMeshPro**
   - Aceptar la importación de TextMeshPro si Unity lo solicita.

5. Cambiar el texto del objeto TextMeshPro por:
   > Pulsa M para mostrar el mensaje  
   > Pulsa N para ocultarlo
      
6. Desactivar el objeto del texto:
- Seleccionar el objeto **Text (TextMeshPro)** en la jerarquía
- En el Inspector, desmarcar el checkbox de la parte superior

7. Crear un GameObject vacío para el script:
- Menú: **GameObject > Create Empty**
- Cambiar el nombre a: `GameManager`

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
}
```

