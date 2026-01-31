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
   - Si Unity solicita importar TextMeshPro (Essentials o Extras), aceptar todas las opciones para continuar.


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

### 8. Crear el script en Assets
1. En la ventana **Project** (Assets):
   - (Opcional) Crear una carpeta llamada `Scripts`
   - Entrar en `Assets/Scripts`

2. Crear el script:
- Situarse en la ventana **Project (Assets)**
- Menú: **Assets > Create > MonoBehaviour Script**
  (Si no funciona el botón derecho, usar el menú superior)
- Nombre del script: `ControlMensaje`


> Importante: el nombre del archivo y el nombre de la clase deben coincidir.

### 9. Pegar el código
Abrir `ControlMensaje.cs` y reemplazar el contenido por:

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
## Enlazar el script y probar el funcionamiento

### 1. Asignar el script al GameManager
- En la ventana **Hierarchy**, seleccionar el objeto `GameManager`.
- Arrastrar el script `ControlMensaje` desde la ventana **Project (Assets)** al **Inspector** del `GameManager`.
- Comprobar que el componente `ControlMensaje` aparece en el Inspector.

### 2. Enlazar el objeto del mensaje
- Con el objeto `GameManager` seleccionado:
  - En el Inspector, localizar el campo **Mensaje** del script `ControlMensaje`.
  - Arrastrar el objeto **Text (TextMeshPro)** desde la jerarquía hasta el campo **Mensaje**.

> Este paso es obligatorio para que el script funcione correctamente.
>
## 📐 Ajuste de posición y tamaño del texto (muy importante)

Para que el mensaje se vea correctamente en pantalla y no quede fuera del área visible, configurar el **Rect Transform** del objeto **Text (TextMeshPro)** con los siguientes valores:

1. Seleccionar el objeto **Text (TextMeshPro)** dentro del `Canvas`.

2. En el componente **Rect Transform**:
   - **Anchors**: Centro (Middle Center)  
     *(Seleccionar el preset central; opcionalmente usar Alt + Shift al hacer clic)*
   - **Pos X**: `0`
   - **Pos Y**: `0`
   - **Width**: `500`
   - **Height**: `120`

3. En el componente **TextMeshPro – Text (UI)**:
   - **Alignment**: Center / Center

Con esta configuración, el texto aparecerá **centrado en pantalla** y se verá correctamente en cualquier resolución.

> ⚠️ Nota:  
> Si el texto existe pero no se ve correctamente en pantalla, revisa primero el **Rect Transform** (posición y anchors) antes de modificar el script.


### 3. Probar la práctica
- Pulsar el botón **Play**.
- Hacer clic dentro de la ventana **Game** para que Unity detecte el teclado.
- Pulsar las siguientes teclas:
  - **M** → el mensaje aparece en pantalla.
  - **N** → el mensaje desaparece.

### 4. Comprobaciones finales
- Al iniciar el juego, el mensaje no debe verse.
- No deben aparecer errores en la consola.

