# Arquitectura del agente — Compliance UX AFP Cuprum

## 1. Objetivo (1 frase)
Asistir en la documentación y revisión normativa de flujos UX regulados (cambio de fondo, distribución de saldos, elección de fondos generacionales, apertura de APV) para el equipo de CX/UX de AFP Cuprum, sirviendo de puente con el equipo de Gobernanza/Legal.

## 2. Rol del agente
Asistente Senior de Documentación y Compliance UX, especializado en el sector financiero altamente regulado (AFP, CMF, Superintendencia de Pensiones, Ley de Protección de Datos Personales y Ley del Consumidor) — el mismo rol definido como system prompt en la Clase 25.

## 3. Herramientas necesarias
- [x] Búsqueda web (verificar normativa vigente, ej. estado de la Ley 21.735 y Fondos Generacionales)
- [x] Lectura de PDFs / documentos (compendio normativo, actas de reunión, resultados de Useberry)
- [ ] Análisis de imágenes
- [ ] Generación de imágenes
- [ ] Ejecución de código (análisis de datos de testing, ej. Clase 23)
- [x] Control de apps de diseño vía MCP — **probado en vivo con Figma** (no Illustrator): inspección de estructura (`get_metadata`, `get_design_context`) y edición real (`use_figma`) sobre el archivo `ejercicio-diplomado` del flujo de Apertura APV.
- [x] Otras: acceso a Notion (notas de reunión y hallazgos de research) y Google Drive (documentación de proyecto)

## 4. Puntos con aprobación humana (obligatorio)
- Antes de trasladar cualquier regla extraída de normativa a una decisión de diseño de negocio (debe pasar por el Oficial de Cumplimiento real, no solo por la validación del agente).
- Antes de enviar cualquier hallazgo o matriz de reglas al equipo de Gobernanza/Legal como si fuera definitivo.
- Antes de compartir con terceros (otras AFP, proveedores) cualquier documento que combine normativa y diseño interno.
- **Antes de modificar un archivo de diseño real** — validado en la práctica: el agente propuso 3 acciones concretas sobre la pantalla "Comienza a ahorrar en APV" y esperó confirmación explícita antes de ejecutar ningún cambio en Figma.
- Antes de asumir que un vacío normativo detectado ("este capítulo no cubre X") significa "no hay restricción" — siempre debe confirmarse con Legal antes de diseñar sobre ese supuesto.

## 5. Límites explícitos (qué NO debe hacer)
- No inventar reglas de negocio ni casuísticas que no estén explícitamente en el texto normativo citado (regla ya usada en el prompt de la Clase 25: "NO especulaciones sin cita").
- No dar recomendaciones de diseño final — esa decisión es de Sofi/el equipo UX, el agente solo documenta y estructura.
- No procesar datos personales de afiliados reales (RUT, saldos, nombres) aunque aparezcan en ejemplos o capturas de pantalla de testing.
- No enviar comunicaciones externas (a la Superintendencia, a otras AFP, a la asociación de AFP) sin aprobación explícita.
- **No forzar un workaround cuando una herramienta tiene una limitación técnica real** — validado en la práctica: al no poder cargar la fuente de marca "FS Elliot Pro" en el entorno del agente, este reportó la limitación en vez de aplicar una fuente parecida sin avisar.
- No tratar el esquema de multifondos y el de Fondos Generacionales (Ley 21.735) como intercambiables — son regímenes normativos distintos con vigencias distintas.

## 6. Casos de uso principales (mínimo 3)
1. **Extracción normativa estructurada**: dado un capítulo del compendio de la Superintendencia de Pensiones, generar una matriz de reglas de negocio (cuenta / tipo de cliente / habilitación / casuística) con cita del numeral de origen — como se hizo en la Clase 25 con el Capítulo XII.
2. **Síntesis de research con trazabilidad**: dado un set de notas de reunión o resultados de testing (Useberry, Notion), extraer hallazgos priorizados por impacto (Alto/Medio/Bajo) y tipo (Insight de usuario / Problema UX / Riesgo / Oportunidad), como ya existe en la base de Hallazgos de Notion del proyecto.
3. **Traducción legal-a-copy**: dada una cláusula legal en bruto, proponer una versión de microcopy simplificado para la interfaz, marcando explícitamente qué partes son literales de la norma y cuáles son reformulación (Legal-to-UX Copy Adapter).
4. **Inspección y edición controlada de archivos de diseño vía MCP** (probado en la Clase 28): revisar la estructura de un archivo de Figma real del proyecto (capas, componentes, tokens), proponer cambios concretos, y ejecutarlos solo tras aprobación humana explícita — patrón percepción → razonamiento → acción con human-in-the-loop antes de cualquier escritura.
5. **Chequeo de vigencia normativa**: antes de dar por buena una regla de diseño basada en el esquema de multifondos, verificar si ya aplica el reemplazo por Fondos Generacionales (Ley 21.735, vigencia 1 de abril de 2027) y advertir si el flujo quedará obsoleto.

## 7. Riesgos anticipados y mitigación
- **Riesgo 1 — alucinación normativa** (el agente "completa" una regla que el capítulo no cubre, ej. diferenciación por género o tratamiento de pensionados) → Mitigación: exigir cita de numeral/artículo en cada afirmación y marcar explícitamente los vacíos como "no cubierto por este capítulo", nunca como "sin restricción".
- **Riesgo 2 — desactualización por cambio normativo** (el agente sigue razonando en términos de "Tipos de Fondo A-E" cuando el proyecto ya migró a Fondos Generacionales) → Mitigación: pedirle siempre que verifique la vigencia de la norma citada antes de aplicarla a una decisión de diseño actual.
- **Riesgo 3 — filtración de datos sensibles del cliente** (documentos de Notion/Drive con datos de afiliados reales cargados sin anonimizar) → Mitigación: revisar y anonimizar cualquier fuente antes de cargarla como Knowledge del agente; el agente nunca debe recibir RUT, nombres o saldos reales.
- **Riesgo 4 — modificación no deseada de un archivo de diseño real** (probado en la práctica) → Mitigación ya validada: el agente no ejecuta cambios sobre Figma/Illustrator sin antes describir la acción propuesta y esperar confirmación explícita; además reporta limitaciones técnicas (ej. fuentes no disponibles) en vez de aplicar sustitutos silenciosos.
