# Bitacora de tecnicas avanzadas 
Laboratorio 07: Tecnicas Avanzadas de Prompting. 
Herramienta de IA usada: (escribe aqui cual usaste) 
## Ejercicio 2: Zero-shot, one-shot y few-shot 


| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot | 5 | Texto libre con explicaciones | No |
| One-shot | 5 | Lista numerada con etiquetas | Sí |
| Few-shot | 5 | Solo "comentario -> etiqueta" | Sí |

## Ejercicio 3: Chain of Thought 

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|------------------|
| Directo | 318.60 | No | Sí |
| Paso a paso | 318.60 | Sí | Sí |

Es útil ver el razonamiento porque nos permite auditar y verificar cada cálculo intermedio. Si la IA llega a cometer un error en una operación matemática compleja, podemos identificar exactamente en qué paso falló en lugar de solo recibir un número incorrecto sin explicación.

## Ejercicio 4: Role prompting 

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|-------------------------------|-----------------------|----------------------|
| A. Sin rol | General / Estándar | Ejemplos básicos de texto | A cualquier principiante curioso |
| B. Rol docente | Muy sencillo y amigable | Analogías de la vida real (cajas) | A estudiantes que recién empiezan desde cero |
| C. Rol senior | Avanzado y técnico | Código estructurado en Java | A programadores o desarrolladores profesionales |

## Ejercicio 5: Descomposicion 
- **Paso 1:** La IA me entregó una lista con los 5 requisitos del sistema (como registrar productos, actualizar stock, etc.).
- **Paso 2:** Diseñó las clases necesarias (`Producto`, `Inventario`) detallando sus atributos y tipos de datos.
- **Paso 3:** Generó el código Java completo y ordenado para la clase `Producto`.
- **Paso 4:** Realizó una revisión del código y propuso 3 mejoras (como validación de datos, encapsulamiento o métodos adicionales).

*Comparación:* El pedido de una sola vez generó un resultado demasiado genérico y difícil de revisar de golpe. Al dividirlo por pasos (descomposición), se obtuvo un diseño mucho más estructurado, coherente y con código de mejor calidad.

## Ejercicio 6: Prompt estructurado y autocritica
### Evaluación de la tabla final

| Qué revisar | Cumple (Sí / No) |
|-------------|------------------|
| ¿Tiene las 4 columnas pedidas? | Sí |
| ¿Incluye el bloqueo después de 3 intentos? | Sí |
| ¿Incluye casos con campos vacíos? | Sí |
| ¿Indica qué casos agregó en la autocrítica? | Sí |
| ¿Hay algún caso repetido o que no tenga sentido? | No |

### Prompts utilizados

```text
<rol>Actua como analista de pruebas de software.</rol>
<contexto>Login web con correo y contrasena. La cuenta se bloquea despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado.</formato>

Revisa tu tabla: faltan casos limite como campos vacios, correo sin @ o contrasena con espacios? Agrega los que falten e indica cuales agregaste.
```
