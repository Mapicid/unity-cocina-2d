# Práctica 04 — Mensaje en pantalla (UI) Correcto / Incorrecto

## Objetivo
Mostrar en pantalla un mensaje visual cuando un alimento se suelta en una zona:
- ✔ CORRECTO
- ❌ INCORRECTO

En esta práctica dejamos de depender de la Console.

---

## Conceptos que se trabajan
- Canvas (UI)
- TextMeshPro (texto en pantalla)
- Referencias desde el Inspector
- Activar / desactivar UI desde un script

---

## Preparación de la UI (Canvas + Texto)

### 1️⃣ Crear el Canvas
En Unity (menú superior):
GameObject → UI → Canvas

Se crea un objeto Canvas en la Hierarchy.

---

### 2️⃣ Crear el texto del mensaje (TextMeshPro)
Dentro del Canvas:
1. Click derecho sobre Canvas en la Hierarchy
2. UI → Text - TextMeshPro

Si Unity pregunta por importar TMP Essentials:
- Aceptar / Import

La primera vez que se usa TextMeshPro, Unity tarda en importar.
Renombrar el texto a:
Mensaje

---

### 3️⃣ Configurar el texto Mensaje
Seleccionar Mensaje y en el Inspector ajustar:
- Text: (vacío o “ ”)
- Font Size: (por ejemplo 48)
- Alignment: Center
- Posición: centrado en la pantalla (RectTransform)

Opcional (recomendado):
- Desactivar el GameObject Mensaje para que al empezar no se vea:
  En la Hierarchy, desmarcar la casilla del objeto Mensaje.

---

## Modificar el script ZonaCategoria para usar UI

### 4️⃣ Abrir el script ZonaCategoria.cs
Vamos a añadir un campo para enlazar el texto de UI y cambiar el mensaje.

Sustituir el contenido del script por este:
```csharp
using UnityEngine;
using TMPro;

public class ZonaCategoria : MonoBehaviour
{
    public string tagCorrecto;
    public TextMeshProUGUI textoMensaje;

    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag(tagCorrecto))
        {
            MostrarMensaje("✔ CORRECTO: " + other.name);
        }
        else
        {
            MostrarMensaje("❌ INCORRECTO: " + other.name);
        }
    }

    void MostrarMensaje(string msg)
    {
        if (textoMensaje == null) return;

        textoMensaje.text = msg;
        textoMensaje.gameObject.SetActive(true);
    }
}
```
---

## Enlazar el texto desde el Inspector

### 5️⃣ Asignar el Text Mensaje al script
1. Seleccionar ZonaVerduras
2. En el componente ZonaCategoria, buscar el campo:
   textoMensaje
3. Arrastrar desde la Hierarchy el objeto:
   Mensaje
   y soltarlo en ese campo

---

## ▶️ Probar el juego
1. Pulsar Play
2. Arrastrar la Zanahoria a ZonaVerduras
3. Ver el mensaje en pantalla

---

## ✅ Resultado esperado
Al soltar la zanahoria en la zona:
- Aparece un texto grande en el centro:
  ✔ CORRECTO: Zanahoria

Si fuera un objeto incorrecto:
- ❌ INCORRECTO: NombreObjeto

---

## ❌ Errores comunes
- No importar TextMeshPro Essentials
- Olvidar añadir `using TMPro;`
- No arrastrar el objeto Mensaje al campo textoMensaje
- Tener el objeto Mensaje desactivado pero no activarlo desde el script

---

## ✅ Configuración final correcta (resumen)

### 🥕 Zanahoria
- Tag: Verdura

### 🟩 ZonaVerduras
- Tag: Untagged (no se utiliza para la comprobación)
- Script: ZonaCategoria
- Campo Tag Correcto: Verdura
- Campo textoMensaje: Mensaje (TextMeshProUGUI)

---

## Siguiente mejora (opcional)
- Ocultar el mensaje después de 2 segundos
- Cambiar el color del texto (verde/rojo)
- Añadir sonido de acierto/error

