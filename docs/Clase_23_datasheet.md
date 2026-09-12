# Datasheet — Compliance UX: Extracción Capítulo XII (Distribución de saldos y traspasos futuros)

*Documento vivo. Se completa clase a clase.*
*Completado en Clase 23 (Diplomado IA Aplicada al Diseño, UDD 2026) a partir del trabajo previo de la Clase 25.*

## 1. Motivación

- **¿Para qué usarás este dataset en tu proyecto?** Como insumo estructurado para diseñar y documentar los flujos de UX de "distribución de saldos y traspasos futuros" del proyecto Compliance UX: alimenta la matriz de reglas de negocio (tipo de cuenta × tipo de cliente × habilitación × casuística) que sirve de base al **Regulatory Tagging Engine** (vincular componentes de interfaz con artículos normativos) y al **Legal-to-UX Copy Adapter** (traducir cláusulas legales en microcopy).
- **¿Quién lo creó originalmente?** El texto fuente (Capítulo XII del Compendio de Normas del Sistema de Pensiones) fue emitido por la **Superintendencia de Pensiones** de Chile — es normativa pública, no un dataset creado por mí. La versión "dataset" (la extracción tabular estructurada: cuenta / tipo cliente / habilitación / casuística / cita) es una derivación propia, construida en la Clase 25 con apoyo de tres LLMs (Claude, ChatGPT, DeepSeek) a partir de ese capítulo.

## 2. Composición

- **Tipo de datos:** texto normativo (prosa legal, numerada por artículos/numerales) + una extracción tabular derivada (texto estructurado).
- **Cantidad de instancias:** 1 capítulo completo (21 numerales), del cual se derivaron ~6-7 filas de la matriz "tipo de cuenta / tipo de cliente" y ~10 reglas operacionales listadas aparte.
- **¿Hay subgrupos identificables?** Sí, pero no son demográficos: los subgrupos son **tipos de afiliado** (afiliado activo, imponente del IPS, afiliado con solicitud de pensión en trámite, afiliado fallecido, afiliado con Orden de Traspaso Irrevocable en curso) y **tipos de cuenta** (CCI obligatoria, cuenta de ahorro voluntario, APV, APVC). El capítulo **no** distingue subgrupos por edad ni género — eso se identificó como un vacío (ver sección 4).

## 3. Recolección

- **¿Cómo se recolectaron?** Descarga directa del Compendio de Normas del Sistema de Pensiones (documento público de la Superintendencia de Pensiones); no hubo scraping ni API. La estructuración en tabla se hizo con apoyo de LLMs, bajo un prompt que exigía explícitamente no especular y citar el numeral de origen para cada regla.
- **¿Cuándo?** Extracción realizada en la Clase 25 del diplomado (2026), sobre el texto vigente del compendio a esa fecha.
- **¿Se pidió consentimiento?** No aplica — es normativa pública, sin datos personales ni de terceros involucrados.

## 4. Sesgos identificados (mínimo 2)

- **Sesgo 1 — confianza excesiva en el resumen del modelo:** al ser una extracción mediada por LLMs, existe el riesgo de que una regla parezca "verificada" solo porque aparece en una tabla ordenada, cuando en realidad debería contrastarse siempre contra el numeral citado en el texto original. El bench de la Clase 25 mostró que los tres modelos coincidieron en el fondo, pero eso no reemplaza una revisión humana del texto legal.
- **Sesgo 2 — vacío de cobertura documental:** el Capítulo XII no cubre a todos los tipos de clientes (no aborda pensionados en modalidad renta vitalicia/retiro programado, no distingue por sexo/edad). Si este vacío no se marca explícitamente, se puede terminar diseñando un flujo de UX que asuma "sin restricción" cuando la restricción real simplemente está en **otro** capítulo del compendio que no fue incluido en la extracción.
- **Sesgo 3 — desactualización temporal:** el compendio refleja el esquema de **multifondos** vigente; la Ley 21.735 reemplaza ese esquema por **Fondos Generacionales** desde el 1 de abril de 2027. Un dataset extraído hoy quedará parcialmente obsoleto en su terminología y reglas cuando entre en vigencia el nuevo régimen.

## 5. Estrategias de mitigación (mínimo 2)

- **Estrategia 1 — trazabilidad obligatoria:** cada fila de la matriz de reglas debe llevar el número de numeral/artículo citado (como hizo el bench de DeepSeek en la Clase 25), para poder verificar rápidamente contra el texto original y actualizar cuando cambie la norma.
- **Estrategia 2 — marcar vacíos como vacíos, no como ausencia de regla:** cuando el capítulo no cubre un caso (género, pensionados en retiro), documentarlo explícitamente como "no cubierto por este capítulo — verificar en [capítulo/norma correspondiente]" en vez de interpretarlo como "sin restricción".
- **Estrategia 3 — revisión cruzada con Legal/Compliance:** antes de que cualquier regla de esta matriz se traduzca en una regla de negocio del flujo UX, debe pasar por el Oficial de Cumplimiento real del equipo, no solo por la validación de los LLMs.

## 6. Uso recomendado / desaconsejado

- **Para qué SÍ debería usarse:** como base de trabajo para diseñar y documentar reglas de negocio de las pantallas de distribución de saldos y traspasos futuros; como insumo para entrenar o afinar un tagging engine que vincule componentes de UX con artículos normativos; como material de brief compartido entre UX y Legal para acelerar la conversación inicial.
- **Para qué NO debería usarse:** como fuente única para determinar reglas sobre clientes pensionados o diferencias de género (el capítulo no las cubre — esas reglas están, si existen, en otros capítulos o en la Ley 21.735); como sustituto de asesoría legal formal; como base para validar el comportamiento del flujo bajo el futuro esquema de Fondos Generacionales sin revisar la normativa de implementación que dicte la Superintendencia.

## 7. Notas para Mauricio (Unidad 4)

- Este dataset es una **extracción derivada** de un capítulo específico del compendio, no el compendio completo — no asumir que cubre todo el universo normativo de distribución de fondos.
- Las reglas fueron contrastadas entre tres LLMs distintos (Claude, ChatGPT, DeepSeek) para reducir el riesgo de alucinación, pero **no** han sido validadas todavía por el equipo Legal/Compliance real de Cuprum.
- Hay vacíos identificados explícitamente (diferenciación por género, tratamiento de pensionados) que deben tratarse como pendientes de verificación, no como reglas confirmadas de "sin restricción".
- Si en la Unidad 4 se entrena o afina un modelo con este material, considerar que el esquema regulatorio de base (multifondos) tiene fecha de caducidad conocida (Ley 21.735, vigencia 1 de abril de 2027).
