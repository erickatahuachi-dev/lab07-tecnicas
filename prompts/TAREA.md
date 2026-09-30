# Tarea: Mi prompt avanzado

## Tarea elegida
Diseñar y codificar un módulo de **Registro de Usuarios** en Java que incluya validaciones de seguridad para el correo electrónico y la contraseña (mínimo 8 caracteres, una mayúscula y un número).

---

## Version 1: prompt basico
Este es el intento inicial con una instrucción directa y sin contexto adicional.

```text
Haz un código en Java para registrar un usuario con correo y contraseña, y que valide los datos.
```

### Qué mejoró y análisis de la respuesta v1:
La IA entregó un código funcional básico, pero muy genérico. No definió qué tipo de validaciones exactas aplicar para la contraseña ni estructuró el código bajo un patrón de desarrollo limpio o profesional.

---

## Version 2
En esta iteración, se incorporó la técnica de **Role Prompting** y se especificaron las reglas de negocio de forma clara.

```text
Actúa como un Desarrollador Java Senior con experiencia en ciberseguridad. Escribe una clase en Java llamada 'RegistroUsuario' que maneje el registro de usuarios. Debe validar que el correo tenga un '@' y que la contraseña tenga mínimo 8 caracteres, una mayúscula y un número.
```

### Qué mejoró y análisis de la respuesta v2:
La respuesta mejoró drásticamente en calidad técnica gracias al rol asignado. El código incluyó comentarios profesionales, el uso de expresiones regulares (Regex) para el correo electrónico y condicionales específicas para la contraseña.

---

## Version 3: prompt final
En la versión final combinamos cuatro técnicas avanzadas: **Role Prompting**, **Prompt Estructurado** (usando etiquetas XML), **Chain of Thought** (para el flujo lógico) y **Few-Shot** (para determinar el formato estricto de los mensajes de error).

```text
<rol>Actúa como un Ingeniero de Software Senior y Experto en Seguridad de Aplicaciones.</rol>

<contexto>
Estamos construyendo el módulo de autenticación para una app bancaria móvil. La seguridad es crítica.
</contexto>

<instruccion>
Diseña la clase 'UserRegistration' en Java. Piensa paso a paso (Chain of Thought) en la lógica de validación antes de escribir el código: verifica primero la existencia de campos nulos, luego el formato del correo y finalmente la robustez de la contraseña (mínimo 8 caracteres, 1 mayúscula, 1 número).
</instruccion>

<ejemplos>
Formato estricto para las excepciones lanzadas en caso de fallo (Few-Shot):
- Correo inválido -> "ERROR_VALIDACION: El formato del correo electrónico no es válido."
- Contraseña débil -> "ERROR_VALIDACION: La contraseña no cumple con los requisitos mínimos de seguridad."
</ejemplos>

<formato_respuesta>
Muestra primero un breve pseudocódigo de tu razonamiento lógico paso a paso. Luego, entrega el bloque de código Java limpio, encapsulado y listo para producción.
</formato_respuesta>
```

### Qué mejoró y análisis de la respuesta v3:
El prompt final obligó a la IA a estructurar su pensamiento de manera impecable. Al incluir ejemplos del formato de error (Few-Shot), las excepciones del código adoptaron la estructura exacta requerida por la aplicación. El resultado es un código robusto y seguro para producción.

---

## Tecnicas usadas en el prompt final

| Técnica Avanzada | Parte del Prompt Final que la Utiliza |
|------------------|---------------------------------------|
| **Role Prompting** | `<rol>Actúa como un Ingeniero de Software Senior...</rol>` |
| **Prompt Estructurado** | Uso de etiquetas `<rol>`, `<contexto>`, `<instruccion>`, `<ejemplos>` y `<formato_respuesta>`. |
| **Chain of Thought** | Se le ordena explícitamente: *"Piensa paso a paso en la lógica de validación antes de escribir el código..."* |
| **Few-Shot** | Se le otorgan ejemplos de mapeo exacto para los mensajes de error: `Correo inválido -> "ERROR_VALIDACION: ..."` |

---

## Evaluacion del resultado

| Qué revisar | Cumple (Sí / No) |
|-------------|------------------|
| ¿El prompt final combina al menos tres técnicas avanzadas? | **Sí** (Combina 4 técnicas) |
| ¿Se asignó un rol específico en lugar de uno genérico o vago? | **Sí** (Ingeniero de Software Senior y Experto en Seguridad) |
| ¿La IA respetó el formato de excepciones configurado en los ejemplos? | **Sí** |
| ¿Se incluyó la explicación del razonamiento lógico (paso a paso) antes del código? | **Sí** |

---

## Por que elegi estas tecnicas
Elegí **Role Prompting** e **Inyección de Contexto** porque en tareas de seguridad de software es vital que la IA adopte una postura rigurosa y defensiva al programar. Sumé **Chain of Thought** para asegurar que la verificación de datos se realice en un orden jerárquico correcto (evitando errores en cascada como evaluar un texto nulo). Finalmente, utilicé **Few-Shot** y **Prompt Estructurado** para mantener un control absoluto sobre la arquitectura del código y el formato de salida de los errores, lo cual facilita enormemente la posterior integración del código con el resto del sistema informático.
