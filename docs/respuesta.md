# Respuesta a la Auditoría (Parte 3)

| N.º de hallazgo | Decisión | Justificación con la norma | Evidencia antes y después | Commit |
|---|---|---|---|---|
| 1. HTML Válido | Acepta | Según la especificación de WHATWG, las rutas de imágenes no deben contener espacios sin codificar y las etiquetas deben estar correctamente balanceadas. | ![Antes](evidencias/auditoria-html.png) | `fix: corrige ruta de imagen y eliminacion de etiqueta div sobrante` |
| 2. Navegación | Acepta | Los enlaces de navegación deben apuntar a un atributo `id` existente en el documento para garantizar el funcionamiento y la accesibilidad por teclado. | ![Antes](evidencias/auditoria-navegacion.png) | `feat: agregación de ids a las secciones y actualización href del nav` |
| 3. Validación nativa | Acepta | Según el estándar HTML5, los controles de tiempo (`datetime-local`) deben incluir atributos `min` y `max` para restringir la entrada a un rango lógico. | ![Antes](evidencias/auditoria-validacion.png) | `feat: añade atributos min y max al input datetime-local` |

---

### Problemas adicionales detectados y corregidos (No vistos por el auditor)

1. **Atributo title faltante en input con pattern (Accesibilidad):** El auditor no notó que el campo de teléfono (`<input type="tel">`) tenía un atributo `pattern="[0-9]{10}"` pero le faltaba el atributo `title`. Según las normas de accesibilidad y HTML, siempre que se usa un `pattern`, se debe proveer un `title` para que el navegador explique al usuario el formato esperado si ocurre un error. 

**Solución:** Se añadió `title="Debe ingresar exactamente 10 números"` al input.
   * *Commit:* `feat: adición de title al input de telefono`