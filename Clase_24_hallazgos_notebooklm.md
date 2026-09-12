# Hallazgos NotebookLM — Proyecto Fondos Generacionales (Cuprum)

**Fuente cargada:** `fuente_notebooklm_fondos_generacionales.md` — nota de reunión real de planificación (18 de agosto de 2026), extraída de Notion.
**Nota:** este mini-reporte fue elaborado leyendo la fuente completa y citando solo lo que aparece en ella, siguiendo la misma lógica de NotebookLM (RAG: responder solo con lo que está en el documento, no inventar).

---

## Las 5 preguntas (Ejercicio 3, adaptadas al proyecto)

**1. ¿Cuáles son los 3 principales puntos de fricción/incertidumbre mencionados?**
- La distribución de saldo en uno o dos fondos generacionales no tiene pronunciamiento de la Superintendencia todavía, pero el equipo decidió diseñar contemplando dos fondos como escenario más exigente.
- La portabilidad de la elección cuando un afiliado se traspasa a otra AFP es una duda abierta que ni siquiera tiene dueño claro todavía — quedó como "escalar con la asociación de AFP".
- A nivel técnico, no está resuelto si el cambio de elección será una anulación + nueva solicitud o una reescritura de la solicitud existente, lo que condiciona cómo se diseña el flujo de edición.

**2. ¿Qué se dijo sobre el tema clave del proyecto (uno vs. dos fondos)?**
La fuente indica explícitamente: *"Sin pronunciamiento regulatorio aún; se recomienda diseñar considerando dos fondos"*, y agrega la complejidad adicional de qué ocurre con aportes futuros y balanceo si se permiten dos fondos. Es una decisión de diseño tomada bajo incertidumbre normativa deliberada, no un vacío ignorado.

**3. ¿Hay diferencias entre las áreas participantes (no hay "usuarios jóvenes/mayores" en esta fuente, pero sí distintos equipos)?**
Sí: normativa/legal (Nico, Seba) empuja por validar todo antes de publicar; el equipo técnico (Cristóbal, Seba/CIEX) prioriza resolver los tres servicios base (consultar, guardar, editar elección); y UX (Sofi) empuja por un enfoque "transaccional con asesoría" en vez de informativo. Las tres miradas convergen en la misma reunión, lo cual explica por qué el foco del acta es "alinear", no solo "informar".

**4. ¿Qué oportunidades de diseño emergen?**
- Reducir de 10 fondos a 3 opciones predeterminadas (recomendado por Cuprum / equivalente por fecha de nacimiento / manual) es la oportunidad de simplificación más clara y ya está acordada.
- Reutilizar la landing existente de fondos generacionales (CIEX) para la recomendación, en vez de construir una nueva, evita duplicar trabajo.
- El banner/derivación desde la sección de cuentas hacia el nuevo menú dedicado es una oportunidad de descubribilidad que todavía no tiene solución de interacción definida.

**5. ¿Qué apareció que quizás no se había considerado antes de leer la fuente completa?**
El detalle del **plan B por si una AFP competidora se adelanta** (usando como referencia que multifondos tomó 90 días de plazo) es una consideración de negocio/competitiva que normalmente no aparece en un brief de diseño puramente funcional, y condiciona los tiempos: el diseño formal recién arranca a mediados de septiembre, dejando un margen ajustado frente a la meta de enero.

---

## 5 hallazgos con cita textual (para el mini-reporte de trabajo autónomo)

1. **Decisión estratégica de no hacer MVP:** *"Se descarta el enfoque MVP; se prioriza una experiencia completa con campaña de acompañamiento."* — condiciona el alcance de todo el flujo desde el día uno.
2. **Diseñar bajo incertidumbre regulatoria:** *"Diseñar contemplando la opción de que el cliente distribuya su saldo en dos fondos, aunque la Superintendencia aún no se pronuncia al respecto."* — riesgo de rediseño si la norma define lo contrario.
3. **Simplificación de la elección:** *"Mostrar los 10 fondos a priori genera confusión; la decisión debe simplificarse al máximo"* → se acordaron 3 opciones predeterminadas (recomendado, por fecha de nacimiento, manual).
4. **Enfoque transaccional, no informativo:** *"La landing debe ser transaccional con asesoría, no informativa/explicativa extensa (para eso está la landing de CIEX)"* — define el tono y profundidad de contenido de la pantalla.
5. **Dependencia técnica crítica:** el recomendador de fondos generacionales (que sí considera perfil de riesgo) *"no está listo aún; se planifica desarrollarlo en Q4"* — es una dependencia de desarrollo que puede bloquear la recomendación personalizada si no se resuelve a tiempo.

---

## 2 cosas que una síntesis automática podría dejar afuera (chequeo manual)

- El **detalle de a quién le corresponde cada pendiente** (Nico, Seba, Cristóbal, Sofi) — una síntesis genérica tiende a listar los pendientes sin dueño, pero el acta original sí los asigna, y eso es clave para dar seguimiento real.
- El **matiz de "no confirmada ni descartada"** sobre la tabla de equivalencias de la Superintendencia: es fácil que una síntesis lo simplifique a "está validada" o "no está validada", cuando en realidad el acta dice que la versión propia de Cuprum avanza independientemente de que exista o no la versión oficial.

---

## Posible alucinación a vigilar si usas NotebookLM con esta fuente
Ninguna herramienta de síntesis "sabe" qué pasó *después* del 5 de abril con el proceso de cambio de elección — el acta dice literalmente que *"no hay decisión tomada aún sobre el cierre definitivo"*. Si le preguntas a NotebookLM "qué pasa después del 15 de marzo" y responde con una regla categórica en vez de reconocer que está abierta, es una señal de alucinación que hay que verificar contra la fuente.
