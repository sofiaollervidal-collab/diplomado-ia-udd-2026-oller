# Guía visual — Clase 26 (Hugging Face)

## Antes de la clase
- [ ] Cuenta en [huggingface.co](https://huggingface.co) (gratis).

## Navegar el Hub
- Menú superior → `Models` o `Spaces` o `Datasets`.
- Filtros a la izquierda: Task, Language, License, Framework.

## Leer una model card (los campos que importan)
1. **Intended use** — para qué SÍ y para qué NO.
2. **Training data** — de dónde vienen los datos.
3. **Bias, risks and limitations** — lo que el autor admite que falla.
4. **License** — MIT / Apache 2.0 / Llama Community / etc.
5. **How to use** — código o comando.

## Probar un modelo sin instalar nada
- Buscar el modelo → tab `Spaces` en su página → click en cualquier demo.
- O directamente en la sección `Spaces` del sitio.

## Duplicar un Space (para tu propio uso)
1. En cualquier Space, click `⋮` arriba a la derecha → `Duplicate this Space`.
2. Se crea tu copia en tu usuario.
3. Puedes editar el README, subir tus propios archivos, personalizar.

---

## Ejercicio 1 — Comparar 3 modelos en español

| Modelo | Autor | Tamaño | Licencia | Limitación declarada |
|---|---|---|---|---|
| [BSC-LT/salamandra-7b-instruct](https://huggingface.co/BSC-LT/salamandra-7b-instruct) | Language Technologies Unit, Barcelona Supercomputing Center | 7B parámetros | Apache 2.0 | Preentrenado en 35 idiomas europeos; la model card advierte que puede contener sesgos y distorsiones no intencionadas, y que quien lo despliegue es responsable de mitigar esos riesgos. |
| [CohereLabs/aya-101](https://huggingface.co/CohereLabs/aya-101) | Cohere for AI | 13B parámetros | Apache 2.0 | Cubre 101 idiomas (incluido español), pero al ser tan multilingüe el rendimiento por idioma individual es más variable que un modelo entrenado solo en español. |
| [DeepESP/gpt2-spanish](https://huggingface.co/DeepESP/gpt2-spanish) | Comunidad DeepESP (Alejandro Oñate y Jorge Ortiz Fuentes, chileno) | ~124M parámetros (GPT-2 small) | MIT | Entrenado solo con 11.5GB de texto (Wikipedia + libros); sin instruction-tuning, sigue instrucciones peor que Salamandra o Aya. |

**Lectura rápida:** a mayor especialización en español y mayor tamaño (Salamandra, Aya), mejor seguimiento de instrucciones y menor "ruido" multilingüe; el modelo más liviano (GPT-2 Spanish) es útil como referencia histórica/educativa, pero no compite con los otros dos para tareas de producción.

---

## Ejercicio 2 — Probar un Space (clasificación zero-shot)

**Contexto:** se buscaba probar si un modelo genérico podía clasificar automáticamente un hallazgo de UX/UI contra las categorías normativas del proyecto (CMF, Superintendencia de Pensiones, Ley de Protección de Datos Personales, Ley del Consumidor), simulando el **Regulatory Tagging Engine**, sin necesidad de entrenar nada.

- **Space/modelo usado:** [MoritzLaurer/mDeBERTa-v3-base-mnli-xnli](https://huggingface.co/MoritzLaurer/mDeBERTa-v3-base-mnli-xnli) (zero-shot classification), probado desde el widget de inferencia del modelo.
- **Texto de entrada:** "El formulario de registro no incluye una casilla de consentimiento explícito (opt-in) para el tratamiento de datos personales, y el texto del disclaimer aparece en letra pequeña al final de la página."
- **Resultado:** clasificó correctamente el caso como **Ley de Protección de Datos Personales (33%)**, pero con muy poco margen sobre **CMF (29%)** y **Ley del Consumidor (25%)**; **Superintendencia de Pensiones** quedó bien abajo (13%), coherente porque el texto no toca pensiones.

**Conclusión:** el acierto es correcto, pero el margen tan estrecho entre las tres primeras categorías muestra que un clasificador genérico no da la certeza necesaria para un dictamen automático — se necesitaría fine-tuning con normativa chilena real etiquetada.

---

## Ejercicio 3 — Modelos para el proyecto (Aplicación Compliance UX 2026)

| Tipo | Recurso | Por qué sirve |
|---|---|---|
| **Modelo generativo** | [BSC-LT/salamandra-7b-instruct](https://huggingface.co/BSC-LT/salamandra-7b-instruct) (Apache 2.0, 7B) | Instruction-tuned en español; es el tipo de modelo que respalda la función **Legal-to-UX Copy Adapter** — reescribir cláusulas legales en bruto como microcopy claro, sin "letra chica". |
| **Modelo analítico** | [PlanTL-GOB-ES/RoBERTalex](https://huggingface.co/PlanTL-GOB-ES/RoBERTalex) (Apache 2.0) | RoBERTa preentrenado exclusivamente en corpus legal en español (BOE, legislación); pensado para ser afinado en clasificación de texto o NER — encaja con el **Regulatory Tagging Engine** (vincular componentes UX con artículos normativos). |
| **Dataset** | [coastalcph/multi_eurlex](https://huggingface.co/datasets/coastalcph/multi_eurlex) | Legislación europea multilingüe (incluye español) etiquetada con temas EuroVoc — referencia metodológica de cómo estructurar un dataset de clasificación multi-etiqueta de texto normativo, aplicable como base para entrenar/evaluar el tagging regulatorio de CMF/Superintendencia. |

---

## Ejercicio 4 — Space duplicado

*(Pendiente — completar con el link a tu Space personal en huggingface.co/spaces/tu-usuario/...)*

---

## Subir al repo
- `docs/modelos_hf_candidatos.md` con 3 modelos + justificación (Ejercicio 1).
- Screenshots de los Spaces probados (Ejercicio 2).
- `docs/modelos_proyecto_compliance_ux.md` con la tabla del Ejercicio 3 (generativo + analítico + dataset).

## Salas breakout
Mostrar:
1. Los 3 modelos elegidos (Ejercicio 1).
2. Un Space en vivo (Ejercicio 2 — clasificación zero-shot con mDeBERTa).
3. Escuchar 1 sugerencia alternativa del grupo.
