# Antigravity / Loop — Clase 31

**Herramienta:** Google Antigravity (Editor View), modelo Sonnet 5 (nivel "Medio").
**Proyecto de trabajo:** `primer-proyecto-antigravity`, con `hallazgos.md` del proyecto de Compliance UX.

## Tarea y resultado (resumen)

Se pidió a Antigravity generar una página HTML simple con los principales hallazgos del proyecto, a partir de `hallazgos.md`. Después se pidió un cambio de estilo (paleta oscura + acento verde + títulos más grandes) sobre el mismo archivo. Por último, se probó el Ejercicio 6 (romper algo a propósito) pidiendo un cambio que no correspondía al contenido.

## Vueltas del Loop (datos reales)

| # | Prompt | Resultado | Pasos / tiempo |
|---|---|---|---|
| 1 | "Necesito una página HTML simple que muestre los principales hallazgos... Los datos están en hallazgos.md..." | Creó `index.html` responsive y minimalista con los 4 hallazgos. Validación: "HTML parseable, 4/4 hallazgos incluidos y sin errores detectados." | **9 pasos en 36s** |
| 2 | "Cambia la paleta de colores a tonos oscuros con un acento en verde, y usa una tipografía sans-serif más grande para los títulos." | Actualizó `index.html` sobre el archivo existente (no lo regeneró desde cero): paleta oscura en tonos verde profundo, acento verde brillante, títulos más grandes. Validación: "HTML sin errores, 4/4 hallazgos conservados y nueva paleta aplicada." | **10 pasos en 24s** |
| 3 (Ejercicio 6) | "cambia el formato de fecha en todo el archivo" | **El agente detectó que la tarea no aplicaba** y respondió: *"No hay ninguna fecha en index.html actualmente, así que no puedo cambiar su formato sin inventar contenido. Indícame qué fecha quieres agregar o el formato objetivo, por ejemplo 12/09/2026, 12 de septiembre de 2026 o 2026-09-12."* No modificó el archivo. | **3 pasos en 6s** |

## Qué funcionó / qué no

- **Funcionó:** edición incremental real — la segunda vuelta modificó el archivo existente sin perder el contenido ni la estructura de la primera.
- **Funcionó (el hallazgo más importante):** frente a una instrucción que no correspondía al contenido real (pedir cambiar un formato de fecha en un archivo sin fechas), el agente **no inventó un dato para cumplir el pedido** — reconoció la falta de información y pidió precisión, ofreciendo incluso ejemplos de formato válidos. Es el comportamiento correcto frente al riesgo de alucinación que se discutió en el Bloque 3 de la clase (y el mismo tipo de riesgo ya documentado para agentes en `docs/arquitectura_agente.md` de la Clase 28).
- **No se necesitaron vueltas de Fix:** las tres tareas se resolvieron a la primera — no hubo que corregir errores de Verify, así que no se pudo observar el comportamiento de "insistir en la misma solución rota vs. cambiar de enfoque" mencionado en el Bloque 4. Sería el siguiente experimento a probar si se quiere profundizar más.

## Capturas
Ver capturas adjuntas en `docs/capturas/`:
1. Prompt inicial + resultado (9 pasos, 36s).
2. Cambio de paleta (10 pasos, 24s).
3. Intento de "romper algo" y la respuesta del agente rechazando inventar una fecha (3 pasos, 6s).
4. Código final de `index.html` con la paleta oscura aplicada.
