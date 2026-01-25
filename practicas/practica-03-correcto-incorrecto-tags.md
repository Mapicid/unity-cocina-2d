# Práctica 03 — Correcto / Incorrecto con Tags

## Objetivo
Usar **Tags** para comprobar si un alimento se ha colocado en la zona correcta.

Al finalizar la práctica:
- Si la Zanahoria entra en ZonaVerduras → mensaje **Correcto**
- Si entra un alimento incorrecto → mensaje **Incorrecto**

---

## Conceptos que se trabajan
- Tags
- Comparación de etiquetas
- OnTriggerEnter2D
- Lógica condicional (if / else)
- Separación de responsabilidades

---

## Preparación de Tags

### 1️⃣ Crear los Tags necesarios
En Unity:
1. Seleccionar cualquier GameObject
2. En el Inspector, arriba donde pone **Tag**
3. Click en **Add Tag…**
4. Crear los siguientes Tags:
   - Añado el tag verdura. Respeta mayúsculas/minúsculas.
  
---

### 2️⃣ Asignar Tag al alimento
Seleccionar **Zanahoria**:
- En el Inspector → Tag
- Asignar el tag: `Verdura`

---

## Preparar la zona

### 3️⃣ Definir qué tipo de alimento acepta la zona
Seleccionar **ZonaVerduras** y comprobar que tiene:
- BoxCollider2D (Is Trigger activado)
- Script DetectarEntrada (o crear uno nuevo llamado ZonaCategoria)

---

## Crear el script de validación

### 4️⃣ Crear el archivo C#
En Unity:
1. Ir a Assets/scripts
2. Click derecho → Create → MonoBehaviour Script
3. Nombre del script: ZonaCategoria

---

### 5️⃣ Código del script
Abrir `ZonaCategoria.cs` y escribir:

```csharp
using UnityEngine;

public class ZonaCategoria : MonoBehaviour
{
    public string tagCorrecto;

    void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag(tagCorrecto))
        {
            Debug.Log("✔ Correcto: " + other.name);
        }
        else
        {
            Debug.Log("❌ Incorrecto: " + other.name);
        }
    }
}
```

## Configuración de la zona desde el Inspector

### 6️⃣ Configurar la zona desde el Inspector
Seleccionar el GameObject **ZonaVerduras** y comprobar:

- Tiene BoxCollider2D
- Tiene activada la opción Is Trigger
- Tiene añadido el script ZonaCategoria. En esta práctica, el script DetectarEntrada de la práctica anterior ya no se utiliza

En el Inspector, dentro del componente ZonaCategoria:
- En el campo **Tag Correcto**, escribir exactamente: Verdura

---

## ▶️ Probar el juego
1. Pulsar el botón Play
2. Arrastrar la Zanahoria dentro de ZonaVerduras

---

## ✅ Resultado esperado
Si la Zanahoria entra en la zona correcta, en la Console aparece:

✔ Correcto: Zanahoria

Si entra un objeto con un tag incorrecto, en la Console aparece:

❌ Incorrecto: NombreObjeto

---

## ❌ Errores comunes
- No crear el Tag antes de usarlo
- Escribir mal el nombre del tag (mayúsculas y minúsculas importan)
- No asignar el script ZonaCategoria a la zona
- No rellenar el campo Tag Correcto en el Inspector
- No tener activado Is Trigger en el collider de la zona

---

## 🧠 Qué hemos aprendido
- Los Tags permiten identificar objetos como Zanahoria
- La zona decide si el resultado es Correcto o Incorrecto
- CompareTag es la forma correcta de comparar etiquetas
- El comportamiento se configura desde el Inspector sin modificar el código

---

## 🚀 Siguiente paso
En la siguiente práctica se trabajará con:
- Interfaz de usuario (UI)
- Mostrar mensajes en pantalla
- Feedback visual para el jugador
