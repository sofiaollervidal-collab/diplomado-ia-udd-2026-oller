# Guía visual — Clase 28 (Agentes)

## Antes de la clase
- [x] Cuenta Claude (usada vía Claude Projects / conversación con conector de Figma).
- [x] System prompt de la Clase 25 a mano (reutilizado como base del rol del agente en `docs/arquitectura_agente.md`).
- [x] Datos del proyecto listos para subir (Capítulo XII, notas de reunión de Fondos Generacionales, archivo Figma `ejercicio-diplomado`).
- [ ] Adobe Illustrator — **no se usó**; se hizo el ejercicio de MCP con Figma en su lugar (ver más abajo).

## Claude Projects (más simple)
1. [claude.ai](https://claude.ai) → sidebar → Projects → New.
2. Custom instructions: pega el system prompt (el de `docs/Clase_28_casos_de_uso_y_falla.md`, sección "System prompt listo para pegar").
3. Knowledge: subir 2-3 archivos (Capítulo XII, ficha de proyecto, fuente de NotebookLM de Fondos Generacionales).
4. Empezar a chatear.

## Claude Skills (si tu plan las incluye)
1. En el chat, ícono de tools/skills.
2. Activar las que necesitas: Web Search, Computer Use, etc.
3. Pedile algo que requiera acción externa.

## MCP de Figma (agente + herramienta real) — reemplaza el ejercicio de Illustrator
Se hizo en vivo, dentro de esta misma conversación, sobre un archivo real de Figma del proyecto (`ejercicio-diplomado`, flujo "Apertura APV / FCA Corto"):

1. Se pasó el link del archivo de Figma al agente.
2. El agente inspeccionó la estructura del archivo (`get_metadata`, `get_design_context`) antes de tocar nada — paso de **percepción**.
3. El agente propuso 3 acciones concretas y **esperó aprobación explícita** antes de ejecutar cualquier cambio — Regla de oro cumplida.
4. Una vez confirmado, se pidió: cambiar los botones "Continuar" a rosado, cambiar los textos a Comic Sans, y ocultar el logo Cuprum.
5. Resultado real (documentado con captura antes/después):
   - ✅ Botones cambiados a rosado.
   - ✅ Logo ocultado.
   - ⚠️ Cambio de tipografía **no se pudo aplicar**: la fuente de marca del archivo ("FS Elliot Pro") no está disponible en el entorno del agente, y Figma exige poder cargar la fuente actual de un texto antes de reemplazarla. El agente reportó la limitación en vez de forzar un sustituto sin avisar.

## Regla de oro
> Para acciones con consecuencias externas (email, compra, publicar, **modificar un archivo de diseño real**) → **siempre pedir aprobación humana**.
Validado en la práctica: el agente se detuvo a pedir confirmación antes de escribir cualquier cambio en el archivo de Figma.

## Subir al repo
- `docs/arquitectura_agente.md` completado (incluye el caso de uso y el riesgo detectado en el ejercicio con Figma).
- `docs/Clase_28_casos_de_uso_y_falla.md` con los 5 casos de uso, 3 casos de falla y el system prompt.
- Screenshot del antes/después de la pantalla "Comienza a ahorrar en APV" en Figma (botones rosados + logo oculto).
