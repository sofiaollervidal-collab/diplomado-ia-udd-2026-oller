# Guía visual — Clase 25 (ChatGPT, Claude, DeepSeek)

## Antes de la clase
- [ ] Las 3 cuentas creadas (gratis alcanza).
- [ ] Un fragmento de entrevista de tu proyecto listo para pegar.
- [ ] Repositorio GitHub abierto.

## Cuentas rápidas
- ChatGPT: [chatgpt.com](https://chatgpt.com) → registro con Google.
- Claude: [claude.ai](https://claude.ai) → registro con Google o correo.
- DeepSeek: [chat.deepseek.com](https://chat.deepseek.com) → registro con correo.

## Los 6 componentes del prompt profesional
```
1. ROL — Eres un [experto en X]
2. CONTEXTO — El proyecto trata de Y
3. INSTRUCCIÓN — Tu tarea: [específico y accionable]
4. FORMATO — Responde en [tabla / lista / párrafo]
5. EJEMPLOS — [opcional pero potente]
6. RESTRICCIONES — NO hagas [lista de "no"]
```

## Crear un Custom GPT (ChatGPT Plus) o Project (Claude)
**Claude Project** (recomendado, más simple):
1. Sidebar → Projects → New project.
2. Instrucciones (tu system prompt).
3. Knowledge → subir 2-3 archivos del proyecto.
4. Empezar a chatear.

**ChatGPT Custom GPT** (requiere Plus):
1. Sidebar → Explore GPTs → Create.
2. Configure → nombre + instrucciones + archivos.
3. Save.

---

## Ejercicio 1 — Prompt profesional aplicado a tu proyecto

Ejemplo real usado en clase (caso Cuprum, capítulo normativo de distribución de saldos):

```
[ROL]
Actúa como un Asistente Senior de Documentación y Compliance UX
especializado en el sector financiero altamente regulado (AFP, CMF,
Superintendencia de Pensiones, Ley de Protección de Datos Personales y
Ley del Consumidor).

[CONTEXTO]
Tu trabajo apoya directamente el flujo de diseño y revisión normativa
entre el equipo de UX (UX/Product Designers y UX Copywriters) y el
equipo de Gobernanza/Legal (Oficial de Cumplimiento y Analistas de
Riesgo).

[INSTRUCCIONES]
Te entrego el Capítulo XII. Distribución de saldos y traspasos futuros
de recursos previsionales entre fondos de pensiones (archivo adjunto)

Tus tareas son:
1. Identificar tipos de clientes que pueden realizar distribución de saldos
2. Reglas a considerar para el traspaso futuro de cuentas
3. Consideraciones para clientes pensionados
4. Diferencia entre hombres y mujeres próximos a pensionarse
5. Consideraciones operacionales

[FORMATO]
Tabla con columnas: Cuenta, tipo cliente, habilitado para hacer
traspaso, casuísticas por tipo de cuentas activas.

[RESTRICCIONES]
NO hagas: recomendaciones de diseño (eso lo hago yo), especulaciones
sin cita, sin análisis de casuísticas inventadas.
```

**Por qué funciona:** define un rol experto acotado al dominio (AFP/CMF), aclara a quién sirve el output (UX + Legal), da instrucciones numeradas y accionables, fija un formato de tabla verificable, y — el punto más importante para trabajo regulatorio — prohíbe explícitamente la especulación sin cita.

---

## Ejercicio 2 — Bench en vivo: el mismo prompt en las 3

Pegar el prompt del Ejercicio 1 (con el capítulo normativo adjunto) en ChatGPT, Claude y DeepSeek, y comparar el output lado a lado.

### Qué se observó en el bench (capítulo de distribución de saldos y traspasos futuros)

| Modelo | Formato de salida | Fortaleza observada | Detalle distintivo |
|---|---|---|---|
| **Claude** | Tabla + secciones numeradas (1 a 5) siguiendo exactamente la instrucción | Marca explícitamente los vacíos normativos antes de tabular, para no dejarlos "escondidos" en una celda | Señaló al inicio que el capítulo **no contiene ninguna distinción por sexo** para próximos a pensionarse, y sugirió en qué otro capítulo podría estar esa regla |
| **ChatGPT** | Matriz + tabla de reglas separada para "traspaso futuro" | Buena organización visual, separa "matriz de cuentas" de "reglas de traspaso" en tablas distintas | Aclaró que no encontró base para diferenciar hombres/mujeres en *este* capítulo, remarcando la diferencia entre "regla del Capítulo XII" vs. regla de otro capítulo |
| **DeepSeek** | Tabla con columna adicional de **cita normativa (N° de artículo)** | Es el único que agregó una columna de "Base Normativa (Cita)" en la propia tabla, útil para trazabilidad legal | Mantuvo el mismo hallazgo: no hay diferenciación por género en el capítulo analizado |

**Conclusión del bench:** los tres modelos coincidieron en el fondo (mismas reglas, mismo vacío detectado sobre género), pero difirieron en formato: Claude prioriza la advertencia de vacíos antes de la tabla, ChatGPT separa tablas temáticas, y DeepSeek incorpora trazabilidad de citas directamente en la matriz. Para trabajo de compliance, la columna de cita de DeepSeek y la advertencia explícita de Claude son las prácticas más rescatables.

---

## Ejercicio 3 — Diseñar el system prompt de tu proyecto

Con un Project/Custom GPT creado y el material normativo cargado como Knowledge, se afinó el prompt agregando una quinta tarea específica del proyecto (diferencia entre multifondos y Fondos Generacionales, Ley 21.735):

```
Actúa como un Asistente Senior de Documentación y Compliance UX
especializado en el sector financiero altamente regulado (AFP, CMF,
Superintendencia de Pensiones, Ley de Protección de Datos Personales y
Ley del Consumidor).

Tu trabajo apoya directamente el flujo de diseño y revisión normativa
entre el equipo de UX (UX/Product Designers y UX Copywriters) y el
equipo de Gobernanza/Legal (Oficial de Cumplimiento y Analistas de
Riesgo).

Tus tareas son:
1. Identificar tipos de clientes que pueden realizar distribución de saldos
2. Reglas a considerar para el traspaso futuro de cuentas
3. Consideraciones para clientes pensionados
4. Diferencia entre hombres y mujeres próximos a pensionarse
5. Diferencia entre los multifondos y fondos generacionales
```

### Hallazgo clave del ejercicio (respuesta comparada)
- El **Capítulo XII** regula distribución/traspasos dentro del esquema vigente de **multifondos** (Tipos A-E).
- La **Ley 21.735** reemplaza ese esquema por **Fondos Generacionales** (mínimo 10 fondos, asignación por cohorte etaria/ciclo de vida), con vigencia general desde el **1 de abril de 2027**.
- Los tres modelos coincidieron en una advertencia de compliance importante: **no se puede asumir que la regla "distribución en dos fondos" del Capítulo XII se traslada automáticamente a Fondos Generacionales** — eso requiere normativa de implementación adicional de la Superintendencia.
- Sobre diferencias hombre/mujer: no están en el Capítulo XII, sino en la Ley 21.735 (beneficio por años cotizados y compensación por expectativa de vida para mujeres desde los 60-65 años). Es un ejemplo real de por qué **no mezclar fuentes normativas distintas** al construir reglas de negocio para un flujo de UX.

---

## Ejercicio 4 — Iterar el prompt

Probar 3 versiones distintas del system prompt y comparar resultados:

- **v1 — básico:** solo rol + instrucción (sin formato ni restricciones).
- **v2 — con formato explícito:** agrega la sección [FORMATO] (ej. tabla con columnas definidas).
- **v3 — con ejemplos few-shot:** agrega 1-2 ejemplos de output esperado antes de pedir la tarea real.

Documentar en la bitácora:
- Qué versión dio el output más usable sin edición.
- Qué versión especuló menos / citó mejor las fuentes.
- Qué versión fue más rápida de ajustar cuando el resultado no calzaba.

---

## Ejercicio 5 — Guardar evidencia

Subir al repositorio:
- `docs/system_prompt_v3.md` — la versión definitiva del system prompt (Ejercicio 4).
- `docs/comparativa_llms.md` — mini-tabla comparando los 3 modelos con tu prompt (basarse en la tabla del Ejercicio 2).
