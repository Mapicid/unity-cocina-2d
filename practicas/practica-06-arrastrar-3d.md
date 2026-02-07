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
## Script: Arrastrar y soltar en 3D

Crea un script llamado **`DragAndDrop3D.cs`** dentro de la carpeta  
`Assets/Scripts/` y copia el siguiente código:

```csharp
using UnityEngine;

/// <summary>
/// Script para arrastrar y soltar un objeto 3D con el ratón.
/// El objeto se mueve sobre un plano horizontal.
/// </summary>
public class DragAndDrop3D : MonoBehaviour
{
    // ---------- VARIABLES EDITABLES DESDE EL INSPECTOR ----------

    [Header("Ajustes del arrastre")]

    // Altura (eje Y) del plano imaginario sobre el que se mueve el objeto
    // Normalmente será 0 (el suelo)
    public float dragPlaneY = 0f;

    // Si está activado, el objeto mantiene su altura Y al arrastrarlo
    public bool keepObjectY = true;

    // ---------- VARIABLES INTERNAS ----------

    private Camera cam;        // Referencia a la cámara principal
    private bool dragging;     // Indica si el objeto se está arrastrando
    private Vector3 offset;    // Distancia entre el punto del ratón y el centro del objeto
    private Plane dragPlane;   // Plano sobre el que se moverá el objeto

    // Se ejecuta al iniciar el objeto
    private void Awake()
    {
        // Obtenemos la cámara principal de la escena
        cam = Camera.main;

        // Si no hay cámara principal, mostramos un error
        if (cam == null)
        {
            Debug.LogError("No hay una cámara con la etiqueta MainCamera.");
        }
    }

    private void Start()
    {
        // Creamos un plano horizontal en la altura indicada (dragPlaneY)
        // Vector3.up indica que el plano es horizontal
        dragPlane = new Plane(Vector3.up, new Vector3(0f, dragPlaneY, 0f));
    }

    // Se ejecuta cuando hacemos clic sobre el objeto
    private void OnMouseDown()
    {
        dragging = true;

        // Creamos un rayo desde la cámara hasta la posición del ratón
        Ray ray = cam.ScreenPointToRay(Input.mousePosition);

        // Comprobamos dónde el rayo corta el plano
        if (dragPlane.Raycast(ray, out float enter))
        {
            // Calculamos el punto de impacto en el plano
            Vector3 hitPoint = ray.GetPoint(enter);

            // Guardamos la diferencia entre el objeto y el punto del ratón
            // para que no "salte" al centro
            offset = transform.position - hitPoint;
        }
    }

    // Se ejecuta mientras mantenemos pulsado el botón del ratón
    private void OnMouseDrag()
    {
        if (!dragging) return;

        // Rayo desde la cámara al ratón
        Ray ray = cam.ScreenPointToRay(Input.mousePosition);

        // Calculamos la nueva posición sobre el plano
        if (dragPlane.Raycast(ray, out float enter))
        {
            Vector3 hitPoint = ray.GetPoint(enter);

            // Nueva posición del objeto
            Vector3 targetPosition = hitPoint + offset;

            // Si queremos mantener la altura, fijamos el eje Y
            if (keepObjectY)
            {
                targetPosition.y = transform.position.y;
            }

            // Movemos el objeto
            transform.position = targetPosition;
        }
    }

    // Se ejecuta al soltar el botón del ratón
    private void OnMouseUp()
    {
        dragging = false;
    }
}

```

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
### Nota sobre la cámara

- **Perspective** → juegos 3D reales, profundidad, cambio visual de tamaño  
- **Orthographic** → vista plana, tamaño constante, más simple
