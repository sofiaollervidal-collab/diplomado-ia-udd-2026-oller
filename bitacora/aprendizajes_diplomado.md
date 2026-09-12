# Bitácora — Diplomado IA Aplicada al Diseño

## Clase 22
**Aprendizaje en clases:** antes de meterse a construir algo, conviene armar una "ficha de proyecto" tipo model card — objetivo, usuarios, tipo de modelo (generativo/analítico), modelos candidatos.
**Aprendizaje de trabajo:** nos sirvió para aterrizar en una sola página quién usa esto en Cuprum (UX vs. Legal/Compliance) y qué tipo de modelo necesitamos — algo que teníamos disperso en la cabeza.

## Clase 23
**Aprendizaje en clases:** cómo detectar sesgos reales en un dataset — balance de clases, largo del texto por categoría, duplicados — antes de confiar en él.
**Aprendizaje de trabajo:** armamos el datasheet de nuestra extracción del Capítulo XII y nos dimos cuenta de que tiene vacíos (no habla de pensionados ni de género) que hay que marcar como "no cubierto", no como "sin restricción" — error fácil de cometer en compliance.

## Clase 24
**Aprendizaje en clases:** qué es RAG y por qué reduce alucinaciones — el modelo responde solo con lo que le diste, no con memoria general.
**Aprendizaje de trabajo:** usamos una nota real de reunión (Fondos Generacionales) como fuente y sacamos 5 hallazgos con cita textual — útil para no perder detalles de las actas, como quién quedó a cargo de cada pendiente.

## Clase 25
**Aprendizaje en clases:** los 6 componentes de un prompt profesional (rol, contexto, instrucción, formato, ejemplos, restricciones) y cómo comparar el mismo prompt en distintos modelos.
**Aprendizaje de trabajo:** probamos el mismo prompt de compliance en Claude/ChatGPT/DeepSeek sobre el Capítulo XII — los tres coincidieron en el fondo, pero DeepSeek fue el único que agregó columna de cita normativa, algo que nos sirve para el system prompt definitivo.

## Clase 26
**Aprendizaje en clases:** cómo leer una model card (intended use, bias, license) y probar un modelo sin instalar nada vía Spaces.
**Aprendizaje de trabajo:** encontramos modelos candidatos reales para nuestro proyecto (Salamandra para el copy adapter, RoBERTalex para tagging normativo) y probamos un clasificador zero-shot que mostró que necesitamos fine-tuning, no un modelo genérico, si queremos un dictamen automático confiable.

## Clase 27
**Aprendizaje en clases:** edición conversacional en vez de reescribir el prompt completo, y que fusionar imágenes de referencia funciona mejor que describirlo todo en palabras.
**Aprendizaje de trabajo:** armamos el sistema visual del dashboard de compliance, pero aprendimos que Nano Banana puede ignorar un cambio de estilo grande sin avisar — hay que verificar cada resultado, no asumir que se aplicó.

## Clase 28
**Aprendizaje en clases:** la diferencia entre LLM y agente (percepción → razonamiento → acción), el patrón ReAct, y la regla de oro de pedir aprobación humana antes de acciones con consecuencias externas.
**Aprendizaje de trabajo:** probamos el loop completo con el MCP de Figma sobre un archivo real de nuestro proyecto — el agente pidió nuestra aprobación antes de modificar nada, y cuando no pudo cambiar la tipografía (fuente de marca no disponible) avisó en vez de forzar un reemplazo silencioso.

## Clase 29
**Aprendizaje en clases:**
**Aprendizaje de trabajo:**


## Clase 31
**Aprendizaje en clases:** el patrón Loop (Research → Plan → Execute → Verify → Fix) y que un agente bien diseñado pide aprobación en los cambios grandes (el plan), pero itera solo en los chicos.
**Aprendizaje de trabajo:** simulamos el Loop sobre nuestros propios hallazgos de Fondos Generacionales — funcionó bien iterando el mismo archivo sin romper lo anterior, pero al pedir a propósito un cambio que no aplicaba (formato de fecha en un HTML sin fechas), quedó claro el riesgo real: un agente puede "inventar" un dato para cumplir el pedido en vez de avisar que no corresponde — el mismo riesgo que ya habíamos anotado en la arquitectura del agente de la Clase 28.
