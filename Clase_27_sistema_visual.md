# Guía visual — Clase 27 (Imagen generativa con Nano Banana)

## Antes de la clase
- [ ] Cuenta Google activa (para Gemini) → [gemini.google.com](https://gemini.google.com)
- [ ] Opcional: cuenta en [aistudio.google.com](https://aistudio.google.com) si quieres más control técnico

## Estructura de prompt visual
```
[SUJETO] Diseñadora chilena de 35 años en su estudio
[ESTILO] fotografía editorial, Wallpaper Magazine
[COMPOSICIÓN] plano medio, frontal, centrado
[ILUMINACIÓN] luz natural cálida desde la izquierda
[PALETA] tierras y blanco
[TÉCNICO] look hiperrealista, formato vertical 9:16
```

La estructura base usada en los ejercicios de esta clase (idéntica en lógica, aplicada a un caso de producto/UX):
```
[SUJETO PRINCIPAL]
[ESTILO VISUAL]
[COMPOSICIÓN / ENCUADRE]
[ILUMINACIÓN]
[PALETA]
[PARÁMETROS TÉCNICOS]
```

## Trucos con Nano Banana (Gemini 2.5 Flash Image)
- **Edición conversacional**: no reescribas el prompt completo para ajustar algo. Sigue el mismo hilo: "cambia la luz a fría", "saca el objeto del fondo", "que mire hacia la cámara".
- **Consistencia de sujeto**: pide explícitamente "mantén al mismo personaje/producto" cuando generes variantes — así no se te "transforma" entre imágenes.
- **Fusión de imágenes**: sube 2-3 imágenes de referencia (sujeto + escena + estilo) y pide que las combine, en vez de describir todo en palabras.
- **SynthID**: toda imagen que generes queda marcada como IA (marca de agua invisible). Es esperable y es parte del uso responsable — no intentes "ocultarlo".

---

## Ejercicio 1 — Prompt básico vs. profesional

Concepto elegido: producto / escena de uso — pantalla de una app.

| Versión | Prompt | Observaciones |
|---|---|---|
| **Básico** | "Pantalla de una app de compliance" | Al no especificar "revisión de interfaces", "WCAG" o "hallazgos UX", el modelo asumió compliance en sentido amplio (legal/corporativo) en vez de compliance aplicado a diseño de producto. |
| **Profesional** | "Interfaz de dashboard 'Regulatory UI Checker' en pantalla de laptop, mostrando una tabla de hallazgos con dictamen 'Observado' resaltado, mockup flotante sobre fondo degradado suave, estilo de producto SaaS B2B minimalista, iluminación de estudio suave desde arriba, paleta azul marino, blanco y gris con acentos semáforo (verde/ámbar/rojo), composición centrada con espacio negativo, render limpio tipo landing page, formato cuadrado 1:1" | Resultado bastante fiel al prompt: generó tabla de hallazgos, columna de estados, paleta azul marino y blanco, y un laptop como soporte del mockup. Coincidió bastante con la matriz del proyecto real. |

**Aprendizaje:** un prompt "básico" deja que el modelo rellene los vacíos con su propia interpretación genérica del término (compliance = legal, no UX). El prompt profesional, al nombrar el producto exacto, el estado del dictamen, la paleta y el formato técnico, ancla el resultado al contexto real del proyecto.

---

## Ejercicio 2 — Variantes por edición conversacional

Partiendo de la imagen del dashboard "Regulatory UI Checker" (Ejercicio 1), se probaron 4 instrucciones de edición conversacional sobre el mismo hilo:

| Variante | Instrucción | Pregunta a verificar | Resultado |
|---|---|---|---|
| **Estilo** | "Mantén el mismo dashboard y el mismo dictamen 'Observado', pero cambia el estilo a ilustración isométrica" | ¿Se mantiene el layout de la tabla de hallazgos y el color ámbar del dictamen, o se pierde al cambiar de render fotográfico a ilustración? | **No se cumplió.** Entregó una imagen prácticamente idéntica: mantuvo la identidad del dashboard, pero ignoró el cambio de estilo pedido. |
| **Iluminación** | "Cambia la iluminación a fría (tonos azulados), manteniendo todo lo demás igual" | ¿Los acentos semáforo (verde/ámbar/rojo) siguen siendo legibles con luz fría, o se desaturan? | **Se cumplió.** Layout, tabla y semáforo intactos; tono azulado aplicado de forma consistente en toda la escena. |
| **Composición** | "Cambia la composición: aleja la cámara y muestra el mockup del dashboard sobre un escritorio real con laptop y notas, en vez del mockup flotante aislado" | ¿La pantalla sigue siendo legible a esa distancia? ¿Se mantiene la identidad visual del dashboard? | **Se cumplió, con detalles no pedidos.** Agregó notas adhesivas, una persona de fondo y una taza de café, coherentes temáticamente con compliance/UX, aunque no estaban en el prompt. |
| **Paleta** | "Cambia la paleta de azul marino/blanco/gris a una paleta neón cian/magenta, conservando el código semáforo verde/ámbar/rojo para los dictámenes" | ¿Nano Banana logra combinar una paleta neón con el semáforo funcional, o el semáforo se pierde en el cambio? | **Cumplimiento parcial.** Aplicó la paleta neón de forma consistente, pero al saturar todo con esa luz es dudoso que el código semáforo siga siendo funcionalmente distinguible. |

**Conclusión:** de las 4 variantes, 3 mantuvieron bien la identidad del sujeto (dashboard, tabla, contenido). La que falló (cambio de estilo a ilustración) sugiere que Nano Banana es más confiable editando atributos "de superficie" (luz, color) que haciendo transformaciones de render completas dentro del mismo hilo — para eso conviene generar una imagen nueva desde cero en vez de editar conversacionalmente.

---

## Ejercicio 3 — Fusión de imágenes

**Imágenes usadas:**
- **Sujeto:** imagen generada de una UX Designer (pelirroja, anteojos, revisando el laptop).
- **Escena:** imagen con gente de compliance en una oficina (hombre de fondo junto a archivadores "Regulatory Reports"/"Compliance Logs").
- **Estilo:** captura del dashboard "Regulatory UI Checker".

**Instrucción:** "Combina estas tres imágenes en una sola composición coherente: la persona de la primera imagen revisando en su laptop el dashboard con el estilo visual de la tercera imagen, ambientada en el espacio de la segunda imagen."

**Resultado:** fusión lograda — combinó las tres fuentes en una escena única y coherente, pero también mezcló contenido de dos versiones distintas del dashboard que se habían generado antes.

**Edición posterior:** "elimina el hombre que se encuentra en el fondo de la imagen."

**¿Cuándo conviene fusionar vs. describir todo en palabras?** Fusionar conviene cuando ya existen elementos visuales concretos que se quieren preservar; describirlos en un prompt largo pierde fidelidad. Pero, como se vio en este resultado, cuando las imágenes fuente vienen de iteraciones distintas de la misma conversación, el modelo puede combinar elementos que en realidad eran alternativas — hay que ser explícito sobre cuál versión usar para no generar confusión en el resultado.

---

## Ejercicio 4 — Sistema visual (galería final)

Secuencia completa de edición conversacional y fusión, sobre el mismo hilo, hasta armar un sistema visual coherente para el proyecto:

1. "Mantén el mismo dashboard y el mismo dictamen 'Observado', pero cambia el estilo a ilustración isométrica."
2. "Cambia la iluminación a fría (tonos azulados), manteniendo todo lo demás igual."
3. "Cambia la composición: aleja la cámara y muestra el mockup del dashboard sobre un escritorio real con laptop y notas, en vez del mockup flotante aislado."
4. "Cambia la paleta de azul marino/blanco/gris a una paleta neón cian/magenta, conservando el código semáforo verde/ámbar/rojo para los dictámenes."
5. "Combina estas tres imágenes en una sola composición coherente: la persona de la primera imagen revisando en su laptop el dashboard con el estilo visual de la tercera imagen, ambientada en el espacio de la segunda imagen."
6. "No consideraste a la persona UX entregada en las imágenes" (corrección).
7. "Considera el primer dashboard creado, y falta el compliance" (corrección).
8. "Ahora muestra a la misma persona presentando el dashboard a un colega en una reunión."
9. "Muestra al Oficial de Cumplimiento (mismo estilo visual) revisando la matriz de trazabilidad regulatoria en su escritorio."
10. "Genera una escena con la UX Designer y el Oficial de Cumplimiento trabajando juntos frente a la pantalla."
11. "Ahora muestra la misma interfaz pero en la vista de la Matriz de Trazabilidad Regulatoria, con columnas de componente UX y artículo normativo."
12. "Muestra la misma interfaz en la vista del Legal-to-UX Copy Adapter, con una cláusula legal a la izquierda y la propuesta de microcopy simplificado a la derecha."
13. "Muestra la vista del Accessibility & Clarity Reviewer con los resultados de contraste WCAG 2.1 AA."

> Nota: las imágenes generadas para cada paso quedaron en el documento original de la clase (`Clase_27.docx`); al recrear tu propia galería, guarda cada imagen numerada junto a su prompt exacto siguiendo esta misma secuencia.

### Reflexión del ejercicio

**Qué agrega:** edición conversacional real (mantuvo el dashboard intacto en 3 de 4 variantes del Ejercicio 2), fusión de imágenes que combina referencias concretas (persona + escena + estilo) sin perder coherencia, y hasta agregó detalles temáticamente relevantes sin que se los pidieran.

**Qué limita:** ignoró un cambio de estilo grande (fotográfico → isométrico) sin avisar que no lo había aplicado — hay que verificar cada resultado, no asumir que la instrucción se ejecutó. También mezcló contenido de dos versiones distintas del dashboard en la fusión, cuando en realidad eran alternativas, no complementarias.

**Tensión de diseño:** una paleta llamativa (neón) puede ser incoherente con el propósito funcional de la app (accesibilidad/contraste) — se solicitó en los prompts seguir con la paleta neutra elegida en un principio, pero no se logró revertir el cambio pese a las iteraciones.

---

## Documentar cada imagen
- Prompt o instrucción de edición exacta.
- Herramienta: Nano Banana (Gemini 2.5 Flash Image).
- Nombre de archivo descriptivo.

## Subir al repo
- `outputs/sistema_visual/` con las imágenes.
- `docs/sistema_visual.md` con prompts + comentarios.
