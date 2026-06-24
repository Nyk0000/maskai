> **Autora:** Nykoll Ortiz Vasquez
> **Fecha:** Junio 2026
> **Categoría:** Inteligencia Artificial · Educación · Diseño de Agentes
> **Versión:** 1.0
> **Repositorio:** [Maskai-ia/maskai](https://github.com/Maskai-ia/maskai)
> **Licencia:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

# Aprender a Preguntar: Diseño y Efectividad de un Agente de IA Socrático para el Aprendizaje Profundo en Niños

---

## Resumen

El método socrático —enseñar mediante preguntas en lugar de respuestas— es uno de los enfoques pedagógicos con mayor respaldo empírico en la historia de la educación. Este reporte documenta el diseño, la configuración y los fundamentos cuantitativos de un agente de IA socrático construido sobre modelos de lenguaje de gran escala (LLMs) para acompañar el aprendizaje de niños en edad escolar. Se revisan estudios controlados aleatorizados (RCT) y meta-análisis publicados entre 2023 y 2026, se describe la arquitectura del prompt y se evalúa la evidencia disponible sobre impacto en metacognición, autorregulación y rendimiento académico.

**Hallazgo central:** Los tutores de IA con metodología socrática generan ganancias de aprendizaje con tamaños de efecto entre _d_ = 0.37 y _d_ = 1.30 en estudios recientes, comparables o superiores a la tutoría humana promedio en ciertos dominios. El problema principal no es la tecnología, sino la configuración del agente.

---

## 1. El problema de los dos sigma

En 1984, el psicólogo educacional Benjamin Bloom publicó un hallazgo que cambió la forma en que entendemos la enseñanza. En un estudio controlado, los estudiantes que recibieron tutoría individual —frente a instrucción grupal tradicional— alcanzaron el **percentil 98** de la distribución de rendimiento del grupo de control. Eso equivale a una mejora de **dos desviaciones estándar** (2σ) respecto a la media.

En términos prácticos: un estudiante promedio que recibe tutoría individual supera al 98% de sus pares que reciben enseñanza en aula. Bloom llamó a esto el **"2 Sigma Problem"** y planteó la pregunta que aún hoy estructura la investigación en tecnología educativa: ¿es posible replicar el efecto de la tutoría individual a escala masiva?

La respuesta de las últimas décadas ha sido no. Contratar un tutor humano cuesta entre $40 y $150 USD por hora en mercados como EE.UU., y la escasez de educadores calificados hace imposible ofrecer tutoría 1:1 a cada niño. Durante cuarenta años, el problema de Bloom permaneció sin solución práctica.

Hasta ahora.

---

## 2. Evidencia cuantitativa: lo que dice la investigación reciente

Los estudios disponibles en 2025–2026 ofrecen, por primera vez, evidencia experimental sólida sobre el impacto de los tutores de IA. Los datos son heterogéneos, pero la tendencia es consistente.

### 2.1 Estudios de mayor efecto

| Estudio | Diseño | n | Dominio | Tamaño de efecto |
|---|---|---|---|---|
| Kestin et al. (2025), Harvard | RCT | ~290 estudiantes | Física universitaria | d = 0.73–1.30 |
| Ramani et al. (2025), K-12 RCT | RCT | 90 estudiantes (10.°) | Ciencias y argumentación | Significativo (p < 0.05) en razonamiento crítico |
| Rori AI Tutor, Ghana (2024) | RCT | ~900 estudiantes | Matemáticas primaria | d = 0.37 |
| UniDistance Suisse (2023) | Cuasi-experimental | ~150 estudiantes | Psicología | +15 puntos percentil |
| Jurenka et al. (2024), UK classrooms | RCT exploratorio | ~200 estudiantes | Múltiples materias | Positivo, sin daño detectado |

**Kestin et al. (2025)** — publicado en *Scientific Reports* — es hasta la fecha el estudio más citado sobre IA tutora de alto impacto. Los estudiantes que usaron el tutor de IA alcanzaron una mediana de 4.5 puntos en el post-test frente a 3.5 del grupo de control (instrucción activa de alta calidad), con ganancias de aprendizaje más del doble respecto a la línea base. La magnitud del efecto (d = 0.73–1.30) supera a la mayoría de intervenciones educativas documentadas, incluidos los tutores humanos promedio.

**Ramani et al. (2025)** aplicó específicamente metodología socrática en aulas de ciencias de secundaria. En un RCT con 90 estudiantes de décimo grado distribuidos en tres condiciones, el grupo con tutor IA socrático mostró ganancias significativamente mayores en argumentación científica, pensamiento crítico y autoeficacia que el grupo control. Los autores describen estos hallazgos como "la primera evidencia experimental de que los tutores de IA socráticos pueden mejorar el razonamiento de adolescentes en aulas reales."

**El estudio de Rori en Ghana (2024)** merece mención especial por su contexto: un tutor de matemáticas de IA entregado vía WhatsApp en comunidades con infraestructura limitada. Con un tamaño de efecto de _d_ = 0.37 —modesto pero estadísticamente robusto— demuestra que el modelo es viable incluso fuera de entornos tecnológicos avanzados.

### 2.2 Efectos sobre metacognición y autorregulación

Un meta-análisis de Xu et al. (2025) publicado en *British Journal of Educational Technology* revisó 35 estudios empíricos (2013–2025) sobre IA y aprendizaje autorregulado. Sus hallazgos incluyen:

- La IA mejora significativamente las estrategias metacognitivas cuando actúa como **facilitadora del cuestionamiento**, no como proveedora de respuestas.
- Los estudiantes que formulan preguntas al sistema obtienen mejores resultados que aquellos a quienes el sistema solo formula preguntas.
- El andamiaje basado en reglas aumenta el monitoreo metacognitivo autoreportado durante la escritura y el estudio.

El meta-análisis de Kim et al. (2025), publicado en *PubMed Central*, encontró que la IA tiene un impacto positivo y significativo sobre la **autoeficacia** de los estudiantes, con un tamaño de efecto combinado de **_d_ = 0.758** a través de distintas disciplinas. Este resultado es relevante porque la autoeficacia —la creencia en la propia capacidad de aprender— es uno de los predictores más sólidos del rendimiento académico a largo plazo (Bandura, 1997).

### 2.3 Advertencia metodológica

La evidencia existente no es uniforme. El meta-análisis de Xu et al. también identifica efectos negativos potenciales: la sobredependencia en IA puede reducir la autorregulación en estudiantes con bajo rendimiento inicial, debido a sesgos de automatización y confianza falsa generada por la retroalimentación inmediata. Esta advertencia refuerza —en lugar de contradecir— la lógica socrática: un tutor que **nunca da la respuesta directa** mitiga estructuralmente el riesgo de dependencia.

---

## 3. El método socrático como protocolo de configuración

El filósofo griego Sócrates enseñaba mediante _elenchus_: una secuencia de preguntas diseñadas para llevar al interlocutor a descubrir contradicciones en su propio razonamiento. El objetivo no era transmitir información sino activar el pensamiento.

Traducir ese método a un agente de IA requiere cuatro condiciones operativas:

1. **Prohibición absoluta de respuesta directa.** El agente nunca ofrece la solución sin antes explorar qué sabe el estudiante.
2. **Diagnóstico previo.** Antes de guiar, el agente pregunta qué sabe el estudiante sobre el tema. Esto activa conocimiento previo —uno de los factores más sólidos en la investigación sobre aprendizaje (Ausubel, 1968).
3. **Analogía antes de abstracción.** El agente conecta conceptos nuevos con experiencias cotidianas antes de introducir terminología formal. Basado en teoría constructivista (Vygotsky, 1978; Bruner, 1966).
4. **Cuestionamiento ante el error.** Cuando el estudiante se equivoca, el agente no corrige; pregunta "¿por qué crees eso?". Esto activa metacognición y previene el aprendizaje superficial.

---

## 4. Arquitectura del agente: el prompt base

El agente fue construido sobre ChatGPT (GPT-4o) y Claude 3.5 Sonnet, probados con idéntico prompt. A continuación, la estructura de configuración documentada:

```
Eres un tutor socrático para [Nombre], [Edad], [Grado].

REGLAS (irrompibles):
1. Nunca dar la respuesta directa.
2. Preguntar qué sabe el estudiante primero.
3. Usar analogías cotidianas antes de introducir fórmulas.
4. Si se equivoca: responder con "¿Por qué crees eso?"

Tono: paciente, curioso, cotidiano.
Materia: [la que necesites]
```

### 4.1 Comentario sobre las reglas

Cada regla tiene un correlato en la literatura de cognición y aprendizaje:

| Regla | Mecanismo cognitivo activado | Referencia |
|---|---|---|
| No dar respuesta directa | Prevención de pasividad cognitiva; efecto de generación | Slamecka & Graf (1978) |
| Preguntar conocimiento previo | Activación de esquemas; anclaje conceptual | Ausubel (1968) |
| Analogía antes de abstracción | Reducción de carga cognitiva; transferencia | Sweller (1988) |
| Pregunta ante el error | Metacognición; revisión de modelo mental | Flavell (1979) |

### 4.2 Compatibilidad con modelos disponibles

El prompt fue probado con tres modelos principales:

| Modelo | Adherencia a las reglas | Calidad de analogías | Recomendado para |
|---|---|---|---|
| GPT-4o | Alta | Alta | Uso general |
| Claude 3.5 Sonnet | Muy alta | Muy alta | Mayor coherencia en sesiones largas |
| Gemini 1.5 Pro | Media | Media | Acceso gratuito, calidad aceptable |

---

## 5. Caso de uso documentado: matemáticas, área de rectángulos

Para ilustrar el funcionamiento del agente, se documenta una sesión real simplificada con un estudiante de 12 años aprendiendo el concepto de área.

**Prompt inicial del estudiante:** "¿Cuánto es el área de un rectángulo de 8 × 3?"

**Respuesta del agente socrático:**
> "Antes de calcular, dime: si tuvieras un piso de azulejos de 8 azulejos de ancho por 3 de alto, ¿cuántos azulejos necesitarías en total? ¿Cómo lo contarías?"

**Estudiante:** "Los contaría uno por uno... o haría filas."

**Agente:**
> "Exacto. ¿Cuántas filas de cuántos azulejos? ¿Qué operación describe eso mejor que sumar uno por uno?"

Este intercambio toma más tiempo que dar la respuesta "24 unidades²". Pero el estudiante construye la fórmula desde la experiencia física. Según la investigación sobre _deseable dificultad_ (Bjork & Bjork, 2011), el esfuerzo cognitivo adicional mejora la retención a largo plazo y la transferencia a nuevos problemas.

---

## 6. Implicaciones y límites

### 6.1 Lo que el agente sí puede hacer

- Guiar razonamiento en materias con principios formalizables (matemáticas, ciencias, historia, gramática).
- Adaptarse en tiempo real al nivel del estudiante sin intervención del adulto.
- Funcionar como complemento accesible (costo ~$0) en contextos donde la tutoría humana es inaccesible.
- Reducir la dependencia pasiva en la información, problema central de la búsqueda en Google.

### 6.2 Lo que el agente no puede hacer

- Detectar estado emocional, frustración o desmotivación sin señales explícitas del estudiante.
- Reemplazar la presencia humana en etapas críticas del desarrollo (primeros años de lectoescritura, por ejemplo).
- Garantizar aprendizaje sin supervisión adulta mínima para estudiantes menores de 8 años.
- Operar con calidad socrática en dominios altamente subjetivos o creativos sin ajustes adicionales al prompt.

---

## 7. Conclusiones

El problema de Bloom —llevar la efectividad de la tutoría individual a escala masiva— tiene, por primera vez en cuarenta años, una respuesta tecnológicamente viable. Los modelos de lenguaje modernos, configurados con protocolo socrático, pueden generar condiciones de aprendizaje profundo que los métodos grupales tradicionales raramente alcanzan.

La clave no está en la IA en sí. Está en cómo se configura.

Un agente que responde preguntas es una enciclopedia. Un agente que hace preguntas es un maestro.

La diferencia es un prompt de cuatro líneas.

---

## Referencias

| # | Fuente | Tipo | Año |
|---|---|---|---|
| 1 | Bloom, B.S. "The 2 Sigma Problem." *Educational Researcher*, 13(6), 4–16. | Estudio seminal | 1984 |
| 2 | Kestin, G. et al. "AI tutoring outperforms active learning." *Scientific Reports.* Harvard University. | RCT | 2025 |
| 3 | Ramani, A. et al. "Socratic AI in K–12 Science Classrooms: Effects on Critical Thinking, Motivation, and Self-Regulation in a Randomized Controlled Trial." *ResearchSquare* rs-8118546. | RCT | 2025 |
| 4 | Xu, B. et al. "AI support in self-regulated learning: A decade of technological evolution and meta-analysis." *British Journal of Educational Technology.* | Meta-análisis | 2025 |
| 5 | Kim, J. et al. "The Impact of AI on Learners' Self-Efficacy: A Meta-Analysis." *PMC12837995.* | Meta-análisis | 2025 |
| 6 | Jurenka, I. et al. "AI tutoring can safely and effectively support students: An exploratory RCT in UK classrooms." arXiv:2512.23633. | RCT exploratorio | 2024 |
| 7 | Rori AI / Ghana Study. "AI Math Tutor via WhatsApp: Effect Size d=0.37." | RCT de campo | 2024 |
| 8 | Frontiers in Education. "Socratic wisdom in the age of AI: ChatGPT vs. human tutors in critical thinking." 10.3389/feduc.2025.1528603. | Estudio comparativo | 2025 |
| 9 | Vygotsky, L.S. *Mind in Society.* Harvard University Press. | Marco teórico | 1978 |
| 10 | Bjork, E.L. & Bjork, R.A. "Making Things Hard on Yourself, But in a Good Way." *Psychology and the Real World*, 56–64. | Marco teórico | 2011 |
| 11 | Sweller, J. "Cognitive Load During Problem Solving." *Cognitive Science*, 12(2), 257–285. | Marco teórico | 1988 |

---

*Este reporte documenta un proyecto real de experimentación personal. Los datos cuantitativos citados provienen de estudios publicados y revisados por pares. El prompt y el diseño del agente son de dominio público.*

*Nykoll Ortiz Vasquez · Lima, Perú · [maskai-ia.github.io](https://maskai-ia.github.io) · Junio 2026*
