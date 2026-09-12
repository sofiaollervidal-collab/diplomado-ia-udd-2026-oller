# Fuente — Reunión de planificación: Landing de Elección de Fondos Generacionales
*(Extraído de Notion — Notas de Reunión desde Audio, 18 de agosto de 2026)*
*Participantes: equipo de CX/UX (Sofi), operaciones (Nico, Vale), técnico (Cristóbal, Seba/CIEX), diseño.*

## Contexto y objetivo
- Meta estratégica: lanzar con una experiencia completa y campaña de acompañamiento (no MVP), siendo la primera AFP del mercado en ofrecerla.
- Objetivo de la reunión: alinear dudas normativas, técnicas y de diseño para estimar tiempos de diseño y desarrollo de la landing.

## Temas normativos y fechas clave
- 15 de marzo: plazo para que el afiliado ingrese su elección (según presentación posterior de la Superintendencia).
- Meta interna de lanzamiento: enero, para maximizar difusión y reducir afiliados sin elección.
- Referencia histórica: en multifondos se usaron 90 días de plazo; se sugiere considerar un plan B por si una AFP competidora se adelanta.
- Diseño formal comienza a mediados de septiembre según el roadmap.
- Desde el 5 de abril en adelante, cualquier cambio se procesa como cambio de fondo generacional.
- Sin pronunciamiento de la Superintendencia sobre si el afiliado podrá distribuir su saldo en uno o dos fondos; se recomienda diseñar contemplando dos fondos.
- Duda abierta sobre portabilidad de la elección al traspasarse entre AFP; pendiente escalar con la asociación de AFP.
- Por ley, si no hay elección, los ahorros voluntarios van al fondo generacional correspondiente al de cotización obligatoria.
- La tabla de equivalencias multifondos → fondos generacionales ya está validada con el área legal, independiente de si existe la versión oficial de la Superintendencia.
- El recomendador de fondos (que sí considera perfil de riesgo) es distinto de la tabla de equivalencias; se planifica desarrollarlo en Q4.

## Temas técnicos
- Se necesitan tres servicios: (1) consultar si el cliente ya tiene una elección registrada, (2) guardar una nueva elección, (3) actualizar/editar una elección existente.
- Pendiente definir si el flujo de cambio de elección es "anulación + nueva solicitud" o "reescritura de la solicitud existente".
- La landing vivirá en NSK, con limitaciones conocidas para incluirla en el home sin workarounds técnicos.
- El recomendador de fondos generacionales es una dependencia técnica para ofrecer recomendación personalizada; si el cliente no tiene perfil, no recibirá recomendación.

## Diseño y experiencia de usuario
- Sofi presentó tres prototipos: (1) resumen informativo + recomendación, (2) estructura por pestañas, (3) integración con la landing existente de fondos generacionales (CIEX).
- Acuerdo: la landing debe ser transaccional con asesoría, no informativa/explicativa extensa.
- Debe incluir sí o sí una recomendación de fondo como parte del servicio.
- Enfoque preferido: tres opciones predeterminadas — (1) fondo recomendado por Cuprum, (2) fondo equivalente por fecha de nacimiento, (3) selección manual.
- Mostrar los 10 fondos generacionales a priori genera confusión; la decisión debe simplificarse al máximo.
- La landing vivirá en un nuevo menú dedicado a fondos generacionales, con derivaciones desde otras secciones (cuentas, banner).
- Referencia de competencia: AFP Capital ya tiene en su sitio privado una sección "Reforma Pensiones" con línea de tiempo.

## Pendientes abiertos
- Compartir presentación de la Superintendencia con fechas actualizadas (Nico).
- Definir qué pasa con las solicitudes después del 15 de marzo.
- Confirmar si la distribución de saldo será en uno o dos fondos (depende de la Superintendencia).
- Escalar duda sobre portabilidad de la elección entre AFP (depende de la Asociación de AFP).
- Validar normativamente el recomendador de fondos generacionales (Legal, Seba).
- Confirmar si la elección es anulación+nueva o reescritura (Operaciones).
- Integrar el widget de elección con la landing existente (equipo Fondos Generacionales, Seba/CIEX).
- Tener listo el recomendador de fondos generacionales (Desarrollo, Q4).
- Iterar las propuestas de diseño según las definiciones de esta reunión (Sofi).
