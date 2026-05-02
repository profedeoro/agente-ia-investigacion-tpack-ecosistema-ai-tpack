# Fundamentación Teórica del Ecosistema AI-TPACK

Este documento consolida todos los marcos teóricos que sustentan las decisiones de diseño del ecosistema. Cada autor y framework aparece junto con: (a) la cita académica, (b) el principio que aporta, y (c) el componente del ecosistema donde se manifiesta operacionalmente.

**Principio rector:** ningún componente del ecosistema existe por preferencia técnica. Cada decisión arquitectónica está fundamentada en literatura educativa revisada por pares. Si alguien cuestiona un diseño, este documento ofrece la respuesta académica.

---

## 1. Marco Teórico Central: AI-TPACK

### 1.1 TPACK Original (base)

**Mishra, P., & Koehler, M. J. (2006).** Technological pedagogical content knowledge: A framework for teacher knowledge. *Teachers College Record, 108*(6), 1017–1054.

**Aporte:** Modelo TPACK identifica 7 intersecciones de conocimiento docente:
- **CK** (Content Knowledge) — conocimiento disciplinar
- **PK** (Pedagogical Knowledge) — conocimiento pedagógico
- **TK** (Technological Knowledge) — conocimiento tecnológico
- **PCK** (Pedagogical + Content) — cómo enseñar el contenido
- **TCK** (Technological + Content) — cómo la tecnología media el contenido
- **TPK** (Technological + Pedagogical) — cómo la tecnología media la pedagogía
- **TPACK** — intersección total

**Operacionalización en el ecosistema:** Cada agente tiene asignada UNA intersección TPACK específica que define qué tipo de conocimiento aporta a la formación. Ver `clo-author/.claude/agents/` — cada agente declara su dimensión.

### 1.2 Reconfiguración AI-TPACK

**Aporte propio del proyecto:** AI-TPACK NO es una extensión donde la IA reemplaza el componente tecnológico. Es una **reconfiguración profunda** donde la IA adquiere agencia pedagógica diferenciada como **tercer actor** en la relación formativa:

| Actor | Rol | Funciones |
|---|---|---|
| Estudiante | Sujeto en formación | Desarrolla competencias con apoyo del tutor IA; mantiene autonomía |
| Tutor IA | Tercer actor pedagógico | Orientación metodológica, retroalimentación inmediata, apoyo en escritura — NO sustituye al docente |
| Docente | Asesor experto | Aspectos complejos y formativos; supervisión; validación final |

**Operacionalización:** La tríada se manifiesta en los 2 modos del ecosistema (`student` / `teacher`) y en la división de funcionalidades exclusivas docentes (`/review --peer`, `/submit`, `/revise`, dashboards).

---

## 2. Las 5 Capas Pedagógicas

### Capa 1: Feedback Estructurado

**Hattie, J., & Timperley, H. (2007).** The power of feedback. *Review of Educational Research, 77*(1), 81–112.

**Aporte:** El feedback efectivo responde tres preguntas: (1) ¿Hacia dónde voy? (Feed Up), (2) ¿Cómo voy? (Feed Back), (3) ¿Qué sigue? (Feed Forward).

**Shute, V. J. (2008).** Focus on formative feedback. *Review of Educational Research, 78*(1), 153–189.

**Aporte:** Principios de feedback efectivo: específico, oportuno, orientado a tarea (no a persona), elaborativo (incluye el porqué), manejable (máximo 3 puntos), no evaluativo en tono.

**Operacionalización:**
- Cada agente crítico en modo student aplica formato Feed Up/Back/Forward (sección "Modo Tutor (TPACK)" de cada `*-critic.md`)
- Máximo 3 brechas prioritarias por ronda
- Adaptación de lenguaje por nivel (Principiante/Intermedio/Avanzado)
- Documento maestro: `clo-author/.claude/references/tpack-pedagogical-framework.md` (Layer 1)

### Capa 2: Autorregulación

**Nicol, D. J., & Macfarlane-Dick, D. (2006).** Formative assessment and self-regulated learning: A model and seven principles of good feedback practice. *Studies in Higher Education, 31*(2), 199–218.

**Aporte:** Siete principios para fomentar autorregulación:
- P1: Clarificar criterios antes del trabajo
- P2: Facilitar autoevaluación
- P3: Entregar información de calidad
- P4: Fomentar diálogo (no transmisión)
- P5: Motivar positivamente
- P6: Cerrar la brecha (acciones concretas)
- P7: Informar al docente

**Zimmerman, B. J. (2002).** Becoming a self-regulated learner: An overview. *Theory into Practice, 41*(2), 64–70.

**Pintrich, P. R. (2000).** The role of goal orientation in self-regulated learning. En *Handbook of self-regulation* (pp. 451–502).

**Aporte combinado:** El aprendizaje autorregulado requiere monitoreo metacognitivo, automotivación, y regulación del propio comportamiento de estudio.

**Operacionalización:**
- Agentes worker piden autoevaluación al estudiante antes de enviar al crítico (P2)
- Críticos comparan autoevaluación con su evaluación → diferencia = oportunidad de aprendizaje
- Todos los agentes preguntan "¿qué parte del feedback no te queda clara?" (P4)
- tutor-pedagogico genera reportes para docente (P7)
- Documento maestro: `clo-author/.claude/references/tpack-pedagogical-framework.md` (Layer 2)

### Capa 3: Andamiaje Disciplinar

**Collins, A., Brown, J. S., & Newman, S. E. (1989).** Cognitive apprenticeship: Teaching the crafts of reading, writing, and mathematics. En *Knowing, learning, and instruction* (pp. 453–494).

**Aporte:** Cognitive Apprenticeship adapta el aprendizaje artesanal a habilidades cognitivas. Seis métodos de enseñanza, de los cuales operacionalizamos cuatro:
- **Modeling** — el experto demuestra el proceso completo
- **Coaching** — el experto guía mientras el aprendiz ejecuta
- **Scaffolding** — el experto provee estructura que el aprendiz completa
- **Fading** — el experto retira apoyo gradualmente

**Vygotsky, L. S. (1978).** *Mind in society: The development of higher psychological processes.* Harvard University Press.

**Aporte:** Zona de Desarrollo Próximo (ZPD) — el aprendiz necesita apoyo en lo que está más allá de su capacidad actual pero alcanzable con guía.

**Wood, D., Bruner, J. S., & Ross, G. (1976).** The role of tutoring in problem solving. *Journal of Child Psychology and Psychiatry, 17*(2), 89–100.

**Aporte:** Concepto operacional de scaffolding que Vygotsky inspiró.

**Kuhlthau, C. C., Maniotes, L. K., & Caspari, A. K. (2007).** *Guided inquiry: Learning in the 21st century.* Libraries Unlimited.

**Aporte:** Guided Inquiry estructura el proceso de indagación en 6 fases: Open, Immerse, Explore, Identify, Gather, Create. Cada fase tiene preguntas guía que el tutor formula al aprendiz para conducirlo al descubrimiento.

**VanLehn, K. (2011).** The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist, 46*(4), 197–221.

**Aporte:** Los sistemas de tutoría inteligente que combinan retroalimentación inmediata con supervisión humana logran efectos cercanos a la tutoría humana 1:1 (effect size 0.79 vs 0.76).

**Operacionalización:**
- Cada agente worker en modo student aplica el método correspondiente al nivel del estudiante:
  - Principiante → Modeling
  - Intermedio → Coaching + Scaffolding
  - Avanzado → Fading
- Mapeo Guided Inquiry → fases del pipeline:
  - Open → /discover interview
  - Immerse → /discover lit
  - Explore → /discover data + /strategize
  - Identify → /strategize
  - Gather → /analyze
  - Create → /write + /talk
- Decisiones de fading basadas en evidencias (no en tiempo o intuición)
- Documento maestro: `clo-author/.claude/references/tpack-pedagogical-framework.md` (Layer 3)

### Capa 4: Evaluación por Evidencias

**Mislevy, R. J., Steinberg, L. S., & Almond, R. G. (2003).** On the structure of educational assessments. *Measurement: Interdisciplinary Research and Perspectives, 1*(1), 3–62.

**Aporte:** Evidence-Centered Design (ECD) separa tres modelos:
1. **Competency Model** — qué puede hacer el aprendiz (latente, no observable)
2. **Evidence Model** — comportamientos observables que demuestran competencia
3. **Task Model** — tareas que producen esa evidencia

**Principio crítico:** la calidad del artefacto y la demostración de competencia son INDEPENDIENTES. Un artefacto puede tener score 85/100 pero si las evidencias no se demuestran, la competencia no está lograda.

**Jonsson, A., & Svingby, G. (2007).** The use of scoring rubrics: Reliability, validity and educational consequences. *Educational Research Review, 2*(2), 130–144.

**Panadero, E., & Jonsson, A. (2013).** The use of scoring rubrics for formative assessment purposes revisited: A review. *Educational Research Review, 9*, 129–144.

**Aporte:** Las rúbricas analíticas mejoran consistencia y transparencia de la evaluación; usadas formativamente, mejoran el aprendizaje.

**Biggs, J., & Tang, C. (2011).** *Teaching for quality learning at university* (4ª ed.). Open University Press.

**Aporte:** Alineamiento constructivo — los criterios de evaluación deben alinearse con los resultados de aprendizaje esperados.

**Shermis, M. D., & Burstein, J. (Eds.). (2013).** *Handbook of automated essay evaluation: Current applications and new directions.* Routledge.

**Aporte:** Automated Essay Scoring (AES) — referente tecnológico para la rúbrica automatizada del ecosistema, adaptado a competencias investigativas.

**Operacionalización:**
- 6 competencias ECD definidas (C1–C6) con evidencias específicas (E1.1–E6.3)
- Cada agente crítico evalúa evidencias además del score del artefacto
- Evidencias clasificadas: DEMONSTRATED / PARTIAL / NOT DEMONSTRATED
- Decisiones de fading requieren evidencias demostradas, no solo score
- Rúbrica automatizada en modo teacher: evaluación preliminar que el docente valida o rechaza (NUNCA evaluación final)
- Documento maestro: `clo-author/.claude/references/tpack-competency-model.md`

### Capa 5: Diseño de Interacciones

**Chi, M. T. H., & Wylie, R. (2014).** The ICAP framework: Linking cognitive engagement to active learning outcomes. *Educational Psychologist, 49*(4), 219–243.

**Aporte:** ICAP clasifica actividades de aprendizaje por nivel cognitivo:
- **Passive** — recibe sin procesar (mínimo aprendizaje)
- **Active** — manipula, repite (bajo aprendizaje)
- **Constructive** — genera ideas nuevas más allá del input (alto aprendizaje)
- **Interactive** — co-construye con otro agente (máximo aprendizaje)

**Hipótesis ICAP:** Interactive > Constructive > Active > Passive para resultados de aprendizaje.

**Operacionalización:**
- Cada nivel de estudiante tiene un mínimo ICAP requerido:
  - Principiante → Activo
  - Intermedio → Constructivo
  - Avanzado → Interactivo
- Los agentes NO proceden tras feedback hasta que el estudiante alcance el ICAP mínimo
- Máximo 2 intentos por checkpoint; si no alcanza, registra como "needs reinforcement"
- tutor-pedagogico-critic verifica el cumplimiento ICAP en cada interacción
- Documento maestro: `clo-author/.claude/references/tpack-pedagogical-framework.md` (Layer 5)

---

## 3. Fundamentación de "Ecosistema"

### 3.1 Definición Conceptual

**Gómez Valderrama** (citado en spec del proyecto): No existe definición concreta de qué es un sistema; el ecosistema es interpretado como un conjunto de organismos donde cada subsistema cumple funciones específicas que generan sinergia hacia la función general del núcleo.

**Operacionalización:** clo-author es el núcleo (función general: pipeline de investigación formativa); las skills auxiliares (rag-engineer, research-engineer, ARS, skill-creator, canvas-design) son subsistemas con funciones específicas que generan sinergia.

### 3.2 Categorías de Ecosistemas de Aprendizaje

**Brodo, R. (2006).** Learning ecosystem: A new paradigm for next-generation learning. *Learning Solutions Magazine.*

**Aporte:** Tres categorías en ecosistemas de aprendizaje:
- Proveedores de contenido
- Consultores
- Infraestructura

**Operacionalización:**
- Proveedores de contenido: librarian (literatura), explorer (datos), bases académicas (Scopus, WoS, etc.)
- Consultores: tutor-pedagogico, error-detective, los critics
- Infraestructura: orchestrator, verifier, rag-engineer

### 3.3 Partes Vivas y No Vivas

**Chang, V., & Güetl, C. (2007).** E-learning ecosystem (ELES) - A holistic approach for the development of more effective learning environment for SMEs. En *Inaugural IEEE-IES Digital EcoSystems and Technologies Conference* (pp. 420–425).

**Aporte:** Distinción entre:
- **Partes vivas:** maestros, tutores, diseñadores instruccionales, expertos pedagógicos
- **Partes no vivas:** medios de aprendizaje, contenidos, tecnologías, herramientas

**Operacionalización:**
- Partes vivas del ecosistema: estudiante, docente, tutor-pedagogico, agentes con función formativa
- Partes no vivas: bases académicas, sistema RAG, archivos de referencia, persistencia en quality_reports/

### 3.4 Aprendiz Autónomo y Relaciones Simbióticas

**Pata, K. (2011).** Meta-design framework for open learning ecosystems. *Mobile and Open Learning Network Workshop.*

**Aporte:** Ecosistemas centrados en aprendiz autónomo y autodirigido. Procesos simbióticos (mutualismo) entre componentes. Cuatro enfoques pedagógicos: aprendizaje autodirigido, basado en competencias, construcción de conocimiento, conectivismo.

**Operacionalización:**
- El estudiante mantiene autonomía y responsabilidad sobre su proceso (mode: student no le hace el trabajo)
- Mutualismo: estudiante alimenta el sistema con respuestas → sistema alimenta al estudiante con scaffolding adaptado
- Aprendizaje basado en competencias: ECD model con C1–C6
- Aprendizaje autodirigido: fading progresivo según evidencias

---

## 4. Contexto Latinoamericano e Institucional

### 4.1 Sobrecarga Docente en Posgrado

**De Kleijn, R. A. M., Mainhard, M. T., Meijer, P. C., Pilot, A., & Brekelmans, M. (2012).** Master's thesis supervision: Relations between perceptions of the supervisor–student relationship, final grade, perceived supervisor contribution to learning and student satisfaction. *Studies in Higher Education, 37*(8), 925–939.

**Lee, A. (2008).** How are doctoral students supervised? Concepts of doctoral research supervision. *Studies in Higher Education, 33*(3), 267–281.

**Pyhältö, K., Vekkaila, J., & Keskinen, J. (2015).** Fit matters in the supervisory relationship: Doctoral students and supervisors' perceptions about the supervisory activities. *Innovations in Education and Teaching International, 52*(1), 4–16.

**Aporte combinado:** La relación estudiante-asesor excede la capacidad efectiva de acompañamiento; la frecuencia y calidad del monitoreo predice el éxito del estudiante.

**Operacionalización:** Justifica el problema central del proyecto y la necesidad del modo teacher con dashboards.

### 4.2 Alfabetización Académica en Latinoamérica

**Carlino, P. (2013).** Alfabetización académica diez años después. *Revista Mexicana de Investigación Educativa, 18*(57), 355–381.

**Aporte:** Las competencias de escritura académica no se desarrollan sistemáticamente en planes de estudio latinoamericanos. La escritura es proceso, no producto.

**Kamler, B., & Thomson, P. (2014).** *Helping doctoral students write: Pedagogies for supervision* (2ª ed.). Routledge.

**Aporte:** Los estudiantes de posgrado frecuentemente tienen dificultad para identificar y articular su marco teórico, formular problemas y escribir académicamente.

**Moreno et al. (2024)** (citado en spec) — refuerza el problema en contexto latinoamericano contemporáneo.

**Flower, L. S., & Hayes, J. R. (1981).** A cognitive process theory of writing. *College Composition and Communication, 32*(4), 365–387.

**Aporte:** Modelo cognitivo de la escritura como proceso iterativo de planificación, traducción y revisión.

**Operacionalización:**
- writer + writer-critic enfocados en escritura como proceso
- Comparación de versiones (modo teacher) basada en escritura iterativa
- Diagnóstico D5 (Academic Writing) reconoce la brecha latinoamericana

### 4.3 Tendencia Internacional

**OECD. (2021).** *AI and the future of skills, Volume 1: Capabilities and assessments.* OECD Publishing.

**UNESCO. (2021).** *AI and education: Guidance for policy-makers.* UNESCO.

**Aporte:** Necesidad de integrar tecnologías digitales para promover autonomía investigativa en educación superior.

**Operacionalización:** Justifica la pertinencia del proyecto en marco internacional.

---

## 5. Validación Empírica: Design-Based Research

**Reeves, T. C. (2006).** Design research from a technology perspective. En *Educational design research* (pp. 52–66). Routledge.

**McKenney, S., & Reeves, T. C. (2012).** *Conducting educational design research.* Routledge.

**Aporte:** Design-Based Research (DBR) — metodología para diseño y validación de innovaciones educativas. Diferencias con cuasi-experimentos: foco en pertinencia y funcionalidad, no en inferencia causal.

**Operacionalización:**
- Tipo de estudio: diseño y validación (no cuasi-experimental)
- Muestra de 15-20 estudiantes consistente con estándares DBR
- Indicadores principales: percepción cualitativa + Likert
- Indicadores complementarios: ciclos de corrección, tiempo de retroalimentación
- Duración: 1 año (preparación 3m + implementación 5m + análisis 4m)

---

## 6. Funcionalidades Docentes — Bases Científicas

### 6.1 Dashboard de Seguimiento

**Siemens, G., & Long, P. (2011).** Penetrating the fog: Analytics in learning and education. *EDUCAUSE Review, 46*(5), 30–40.

**Ferguson, R. (2012).** Learning analytics: Drivers, developments and challenges. *International Journal of Technology Enhanced Learning, 4*(5/6), 304–317.

**Gašević, D., Dawson, S., & Siemens, G. (2015).** Let's not forget: Learning analytics are about learning. *TechTrends, 59*(1), 64–71.

**Aporte combinado:** Learning Analytics — uso sistemático de datos sobre el aprendiz para optimizar el proceso formativo. Patrones de interacción como indicadores de engagement y autorregulación.

**Operacionalización:** `/tools progress --teacher` lee patrones de uso de research_journal.md, frecuencia, regularidad, dimensiones ICAP.

### 6.2 Comparación de Versiones

**Black, P., & Wiliam, D. (1998).** Inside the black box: Raising standards through classroom assessment. *Phi Delta Kappan, 80*(2), 139–148.

**Aporte:** Evaluación formativa progresiva — el aprendizaje se evidencia en la trayectoria, no en producto aislado.

**Operacionalización:** Modo teacher compara versiones del trabajo del estudiante usando `git diff` con contexto pedagógico (mejoras estructurales, fortalecimiento de argumentos, reducción de hedging).

### 6.3 Retroalimentación Asistida (ya cubierto en Capa 1, 3 y VanLehn)

### 6.4 Rúbrica Automatizada (ya cubierto en Capa 4)

### 6.5 Reporte de Uso

**Operacionalización combinada de Siemens & Long, Gašević, Zimmerman, Pintrich:**
- Frecuencia por comando
- Patrones temporales (constante vs concentrado antes de entregas)
- Identificación de estudiantes en riesgo
- Distinción uso superficial vs profundo

---

## 7. error-detective: Diagnóstico de Dificultades de Aprendizaje

### 7.1 Análisis de Causa Raíz Educativo

**Mislevy ECD (ya citado)** — base para correlación de evidencias

**Vygotsky ZPD (ya citado)** — identificar cuando el scaffolding está mal calibrado

**Black & Wiliam (1998)** (ya citado) — evaluación formativa como diagnóstico, no juicio

**Operacionalización:** error-detective aplica:
- Five Whys para dificultades de aprendizaje (no técnicas)
- Correlación cross-dimensión (D1–D6)
- Patrones comunes documentados (diagnostic mismatch, scaffolding gap, passive learning, cross-phase cascade, vocabulary barrier, motivation decline, self-regulation failure)
- Recomendaciones de intervención específicas (re-diagnosis, level adjustment, reinforcement activity, metacognitive scaffolding, motivational calibration, upstream fix, peer modeling)

---

## 8. Diagnóstico Inicial — Rúbrica Científica

### 8.1 Estructura de la Entrevista

**Mislevy, Steinberg & Almond (ya citado)** — ECD para diagnóstico

**Kuhlthau et al. (ya citado)** — Guided Inquiry para entrevista adaptativa

**Aporte combinado:** Entrevista semi-estructurada de 6-8 preguntas adaptativas. Cada respuesta determina la profundidad de la siguiente. La evaluación se basa en evidencias observables, no en juicios subjetivos.

### 8.2 Competencias Investigativas

**Meerah, T. S. M., & Arsad, N. M. (2010).** Developing research skills at secondary school. *Procedia - Social and Behavioral Sciences, 9*, 512–516.

**Aporte:** Indicadores observables de competencias investigativas, base para los indicadores por nivel en cada dimensión D1–D6.

### 8.3 Alfabetización Académica como Marco

**Carlino (2013)** y **Kamler & Thomson (2014)** (ya citados) — base para D5 (escritura) y D2 (literatura).

---

## 9. Integridad Académica de la IA

### 9.1 Cero Alucinaciones

**Operacionalización:** El tutor IA NUNCA genera referencias inventadas. Toda referencia bibliográfica debe ser trazable a Scopus, WoS, ERIC, Redalyc, SciELO, Semantic Scholar, OpenAlex, Google Scholar, Dialnet o DOAJ. La capa RAG es la columna vertebral tecnológica para esto.

### 9.2 Failure Modes en Investigación Autónoma

**Lu, C., et al. (2026).** The AI Scientist: Towards fully automated open-ended scientific discovery. *Nature, 651*, 914–919.

**Aporte:** Primer benchmark publicado de investigación autónoma de IA. Identifica 7 modos de falla:
- Bugs de implementación que pasan auto-revisión
- Resultados experimentales alucinados
- Dependencia de atajos
- Bugs reframeados como insights novedosos
- Fabricación metodológica
- Frame-lock en estadios tempranos
- Alucinaciones de citas

**Operacionalización (a través de academic-research-skills):** ARS implementa Stage 2.5 y Stage 4.5 integrity gates contra estos failure modes. El ecosistema TPACK adopta el principio de human-in-the-loop con docente como validador final.

### 9.3 Filosofía Asistiva, No Autónoma

**Principio del proyecto:** "AI is your copilot, not the pilot." El ecosistema NO escribe el paper por el estudiante. Maneja el trabajo de soporte (búsqueda de referencias, verificación, formato) para que el estudiante se enfoque en lo que requiere su cerebro: definir preguntas, elegir métodos, interpretar datos, articular argumentos.

---

## 10. Patrones de Software Adaptados al Contexto Académico

### 10.1 Test-Driven Development como Pre-Registro

**Fuente:** Patrón TDD del software (Beck, 2003) adaptado.

**Operacionalización:** `/tools pre-register` — el estudiante documenta hipótesis, sign esperado, magnitud esperada y significancia ANTES de correr análisis. RED-GREEN-REFACTOR aplicado a investigación: predicción → ejecución → reconciliación.

### 10.2 Systematic Debugging como Resolución de Problemas

**Operacionalización:** `/tools debug` — protocolo de 4 fases (Investigar causa raíz → Analizar patrón → Hipótesis y prueba → Implementar fix). Adaptado de patrones de superpowers (obra) al contexto académico (LaTeX, scripts, datos, resultados). Iron law: "No hay fix sin investigación de causa raíz primero".

### 10.3 Verification Before Completion como Integridad

**Operacionalización:** `/tools verify` — gate function que exige evidencia fresca antes de declarar trabajo completo. "No hay claim de completitud sin evidencia fresca de verificación". Aplicado a: compilación LaTeX, ejecución de scripts, validación bibliográfica, scores de calidad, replicación.

---

## 11. Mapa Sinóptico: Autor → Componente

| Autor / Framework | Componente del ecosistema donde se manifiesta |
|---|---|
| Mishra & Koehler (2006) — TPACK | Sección "Modo Tutor (TPACK)" en cada agente |
| Hattie & Timperley (2007) | Formato Feed Up/Back/Forward en críticos |
| Shute (2008) | Reglas de feedback (max 3 brechas, elaborativo, etc.) |
| Nicol & Macfarlane-Dick (2006) | Autoevaluación pre-entrega + diálogo post-feedback |
| Zimmerman (2002), Pintrich (2000) | Reportes docentes sobre autorregulación |
| Collins, Brown & Newman (1989) | Modeling/Coaching/Scaffolding/Fading por nivel |
| Vygotsky (1978), Wood et al. (1976) | Calibración del scaffolding según ZPD |
| Kuhlthau et al. (2007) | Guided Inquiry mapeado a fases del pipeline |
| VanLehn (2011) | Justificación de retroalimentación asistida |
| Mislevy, Steinberg & Almond (2003) | tpack-competency-model.md (6 competencias, evidencias) |
| Jonsson & Svingby (2007), Biggs (2011) | Rúbrica automatizada del docente |
| Shermis & Burstein (2013) | Referente tecnológico de AES |
| Chi & Wylie (2014) | Checkpoints ICAP entre fases |
| Brodo (2006) | Categorización de componentes del ecosistema |
| Chang & Güetl (2007) | Distinción partes vivas / no vivas |
| Pata (2011) | Aprendiz autónomo + relaciones simbióticas |
| Gómez Valderrama | Definición conceptual de ecosistema |
| De Kleijn et al. (2012), Pyhältö et al. (2015), Lee (2008) | Justificación del problema (sobrecarga docente) |
| Carlino (2013), Kamler & Thomson (2014), Moreno et al. (2024) | Justificación del contexto LATAM |
| Flower & Hayes (1981) | Escritura como proceso (writer + comparación de versiones) |
| OECD (2021), UNESCO (2021) | Marco internacional |
| Reeves (2006), McKenney & Reeves (2012) | Metodología DBR de validación |
| Siemens & Long (2011), Ferguson (2012), Gašević et al. (2015) | Dashboard docente con Learning Analytics |
| Black & Wiliam (1998) | Comparación de versiones + diagnóstico formativo |
| Meerah & Arsad (2010) | Indicadores observables del diagnóstico |
| Lu et al. (2026) | Filosofía human-in-the-loop, integrity gates |

---

## 12. Cómo Usar Este Documento

**Si eres investigador defendiendo el proyecto:**
- Cualquier decisión arquitectónica del ecosistema tiene su justificación aquí
- Cita las referencias en publicaciones, presentaciones de tesis, reportes
- Ningún componente está sin fundamento — si encuentras uno, repórtalo

**Si eres docente o estudiante:**
- Este documento explica POR QUÉ el sistema funciona como funciona
- Si dudas de una decisión pedagógica del tutor IA, busca aquí su fundamento
- Las recomendaciones del tutor están basadas en literatura, no en preferencias

**Si eres desarrollador extendiendo el ecosistema:**
- Antes de agregar un componente, identifica qué framework lo justifica
- Si no hay fundamento teórico, NO lo agregues — el ecosistema requiere coherencia
- Usa skill-creator (edición restringida a investigación) para mantener este principio

---

## 13. Bibliografía Completa (Orden Alfabético)

Beck, K. (2003). *Test-driven development: By example.* Addison-Wesley.

Biggs, J., & Tang, C. (2011). *Teaching for quality learning at university* (4ª ed.). Open University Press.

Black, P., & Wiliam, D. (1998). Inside the black box: Raising standards through classroom assessment. *Phi Delta Kappan, 80*(2), 139–148.

Brodo, R. (2006). Learning ecosystem: A new paradigm for next-generation learning. *Learning Solutions Magazine.*

Carlino, P. (2013). Alfabetización académica diez años después. *Revista Mexicana de Investigación Educativa, 18*(57), 355–381.

Chang, V., & Güetl, C. (2007). E-learning ecosystem (ELES) - A holistic approach for the development of more effective learning environment for SMEs. En *Inaugural IEEE-IES Digital EcoSystems and Technologies Conference* (pp. 420–425).

Chi, M. T. H., & Wylie, R. (2014). The ICAP framework: Linking cognitive engagement to active learning outcomes. *Educational Psychologist, 49*(4), 219–243.

Collins, A., Brown, J. S., & Newman, S. E. (1989). Cognitive apprenticeship: Teaching the crafts of reading, writing, and mathematics. En L. B. Resnick (Ed.), *Knowing, learning, and instruction* (pp. 453–494). Lawrence Erlbaum.

De Kleijn, R. A. M., Mainhard, M. T., Meijer, P. C., Pilot, A., & Brekelmans, M. (2012). Master's thesis supervision: Relations between perceptions of the supervisor–student relationship, final grade, perceived supervisor contribution to learning and student satisfaction. *Studies in Higher Education, 37*(8), 925–939.

Ferguson, R. (2012). Learning analytics: Drivers, developments and challenges. *International Journal of Technology Enhanced Learning, 4*(5/6), 304–317.

Flower, L. S., & Hayes, J. R. (1981). A cognitive process theory of writing. *College Composition and Communication, 32*(4), 365–387.

Gašević, D., Dawson, S., & Siemens, G. (2015). Let's not forget: Learning analytics are about learning. *TechTrends, 59*(1), 64–71.

Hattie, J., & Timperley, H. (2007). The power of feedback. *Review of Educational Research, 77*(1), 81–112.

Jonsson, A., & Svingby, G. (2007). The use of scoring rubrics: Reliability, validity and educational consequences. *Educational Research Review, 2*(2), 130–144.

Kamler, B., & Thomson, P. (2014). *Helping doctoral students write: Pedagogies for supervision* (2ª ed.). Routledge.

Kuhlthau, C. C., Maniotes, L. K., & Caspari, A. K. (2007). *Guided inquiry: Learning in the 21st century.* Libraries Unlimited.

Lee, A. (2008). How are doctoral students supervised? Concepts of doctoral research supervision. *Studies in Higher Education, 33*(3), 267–281.

Lu, C., et al. (2026). The AI Scientist: Towards fully automated open-ended scientific discovery. *Nature, 651*, 914–919.

McKenney, S., & Reeves, T. C. (2012). *Conducting educational design research.* Routledge.

Meerah, T. S. M., & Arsad, N. M. (2010). Developing research skills at secondary school. *Procedia - Social and Behavioral Sciences, 9*, 512–516.

Mishra, P., & Koehler, M. J. (2006). Technological pedagogical content knowledge: A framework for teacher knowledge. *Teachers College Record, 108*(6), 1017–1054.

Mislevy, R. J., Steinberg, L. S., & Almond, R. G. (2003). On the structure of educational assessments. *Measurement: Interdisciplinary Research and Perspectives, 1*(1), 3–62.

Moreno et al. (2024). [Cita por completar — referenciado en spec del proyecto]

Nicol, D. J., & Macfarlane-Dick, D. (2006). Formative assessment and self-regulated learning: A model and seven principles of good feedback practice. *Studies in Higher Education, 31*(2), 199–218.

OECD. (2021). *AI and the future of skills, Volume 1: Capabilities and assessments.* OECD Publishing.

Panadero, E., & Jonsson, A. (2013). The use of scoring rubrics for formative assessment purposes revisited: A review. *Educational Research Review, 9*, 129–144.

Pata, K. (2011). Meta-design framework for open learning ecosystems. *Mobile and Open Learning Network Workshop.*

Pintrich, P. R. (2000). The role of goal orientation in self-regulated learning. En M. Boekaerts, P. R. Pintrich, & M. Zeidner (Eds.), *Handbook of self-regulation* (pp. 451–502). Academic Press.

Pyhältö, K., Vekkaila, J., & Keskinen, J. (2015). Fit matters in the supervisory relationship: Doctoral students and supervisors' perceptions about the supervisory activities. *Innovations in Education and Teaching International, 52*(1), 4–16.

Reeves, T. C. (2006). Design research from a technology perspective. En J. van den Akker, K. Gravemeijer, S. McKenney, & N. Nieveen (Eds.), *Educational design research* (pp. 52–66). Routledge.

Shermis, M. D., & Burstein, J. (Eds.). (2013). *Handbook of automated essay evaluation: Current applications and new directions.* Routledge.

Shute, V. J. (2008). Focus on formative feedback. *Review of Educational Research, 78*(1), 153–189.

Siemens, G., & Long, P. (2011). Penetrating the fog: Analytics in learning and education. *EDUCAUSE Review, 46*(5), 30–40.

UNESCO. (2021). *AI and education: Guidance for policy-makers.* UNESCO.

VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist, 46*(4), 197–221.

Vygotsky, L. S. (1978). *Mind in society: The development of higher psychological processes.* Harvard University Press.

Wood, D., Bruner, J. S., & Ross, G. (1976). The role of tutoring in problem solving. *Journal of Child Psychology and Psychiatry, 17*(2), 89–100.

Zimmerman, B. J. (2002). Becoming a self-regulated learner: An overview. *Theory into Practice, 41*(2), 64–70.

---

## Documentos Relacionados

- [CLAUDE.md](CLAUDE.md) — Identidad operativa
- [README.md](README.md) — Cara pública
- [architecture.md](architecture.md) — Arquitectura técnica
- [entry-points.md](entry-points.md) — Routing entre componentes (próximo paso)
- [clo-author/.claude/references/tpack-pedagogical-framework.md](clo-author/.claude/references/tpack-pedagogical-framework.md) — Operacionalización detallada de las 5 capas
- [clo-author/.claude/references/tpack-competency-model.md](clo-author/.claude/references/tpack-competency-model.md) — Modelo ECD completo
- [clo-author/.claude/references/tpack-diagnostic-rubric.md](clo-author/.claude/references/tpack-diagnostic-rubric.md) — Rúbrica diagnóstica
- [clo-author/quality_reports/research_spec_ecosistema_ia.md](clo-author/quality_reports/research_spec_ecosistema_ia.md) — Especificación de la investigación
