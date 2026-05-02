# Mapeo TPACK — Cada Componente a su Dimensión

Documento operacional que mapea **cada componente del ecosistema** (skills auxiliares incluidas) a sus dimensiones AI-TPACK específicas. Este es el complemento técnico de `theoretical-foundations.md` (sección 11) y de `architecture.md` (sección 2): aquí cada componente aparece con su justificación pedagógica completa, el nivel de scaffolding que aporta, y la forma exacta de invocarlo.

**Propósito:** garantizar que ningún componente opere fuera del marco AI-TPACK. Si un componente no puede mapearse a una intersección TPACK con justificación pedagógica, NO debe formar parte del ecosistema.

---

## 1. Convenciones del Mapeo

### 1.1 Las 7 Intersecciones TPACK

| Sigla | Significado | Qué representa en el ecosistema |
|---|---|---|
| **CK** | Content Knowledge | Conocimiento disciplinar puro (qué sabe el campo) |
| **PK** | Pedagogical Knowledge | Conocimiento sobre cómo se enseña |
| **TK** | Technological Knowledge | Conocimiento sobre la tecnología en sí |
| **PCK** | Pedagogy + Content | Cómo enseñar el contenido específico |
| **TCK** | Technology + Content | Cómo la tecnología media el acceso al contenido |
| **TPK** | Technology + Pedagogy | Cómo la tecnología media la enseñanza |
| **AI-TPACK** | Intersección total | Integración de los tres dominios con la IA como tercer actor |

### 1.2 Tipos de Componente

| Tipo | Vive en | Ejemplo |
|---|---|---|
| **Agente núcleo** | `clo-author/.claude/agents/` | librarian, strategist, tutor-pedagogico |
| **Skill núcleo** | `clo-author/.claude/skills/` | discover, strategize, write, tools |
| **Reference núcleo** | `clo-author/.claude/references/` | tpack-pedagogical-framework.md |
| **Skill auxiliar** | `.claude/skills/` (raíz) | rag-engineer, research-engineer |
| **Submódulo** | `.claude/skills/` o raíz | academic-research-skills, clo-author |

### 1.3 Niveles de Activación

| Nivel | Cuándo se activa el componente |
|---|---|
| **Always** | Activo en cada sesión, independiente del modo |
| **Student-only** | Solo cuando `mode: student` |
| **Teacher-only** | Solo cuando `mode: teacher` |
| **On-demand** | Cuando el usuario lo invoca explícitamente |
| **Background** | Llamado por otros agentes, no directamente por el usuario |

---

## 2. Matriz Maestra de Componentes a TPACK

### 2.1 Agentes del núcleo (clo-author)

| Agente | TPACK Primario | TPACK Secundario | Diagnóstico (D1-D6) | Competencia (C1-C6) | Activación | Justificación |
|---|---|---|---|---|---|---|
| **tutor-pedagogico** | AI-TPACK | — | Todas | Todas | Student-only, Always | Tercer actor en la tríada (Mishra & Koehler 2006 reconfigurado) |
| **tutor-pedagogico-critic** | AI-TPACK | — | Todas | Todas | Student-only, Always | Calidad pedagógica del sistema (Hattie+Shute+Nicol+Collins+Mislevy+Chi) |
| **error-detective** | AI-TPACK | PK | Todas | Todas | Teacher-only, On-demand | Diagnóstico de aprendizaje (Mislevy ECD + Vygotsky ZPD + Black & Wiliam) |
| **orchestrator** | AI-TPACK | — | — | — | Always | Coordina pedagogía y pipeline |
| **librarian** | TCK | — | D2 | C2 | Always | Tecnología (RAG, bases) sirve al contenido (literatura) |
| **librarian-critic** | TCK | PK | D2 | C2 | Always | Evalúa calidad técnica de la búsqueda con feedback formativo |
| **explorer** | TCK | — | D2/D4 | C2 | Always | Tecnología (búsqueda de datos) sirve al contenido (datos) |
| **explorer-critic** | TCK | PK | D2/D4 | C2 | Always | Evalúa validez de medición y selección |
| **data-engineer** | TPK | TCK | D4 | C4 | Always | Tecnología (R/Python) como medio de aprendizaje (TPK) |
| **strategist** | AI-TPACK | PCK | D3 | C3 | Always | Diseño metodológico integra los tres dominios |
| **strategist-critic** | PCK | PK | D3 | C3 | Always | Evalúa supuestos con pedagogía formativa |
| **coder** | TPK | TCK | D4 | C4 | Always | Código como artefacto de aprendizaje |
| **coder-critic** | TPK | PK | D4 | C4 | Always | Evalúa código con feedback formativo |
| **writer** | PCK | — | D5 | C5 | Always | Pedagogía de la escritura científica |
| **writer-critic** | PCK | PK | D5 | C5 | Always | Evalúa argumentación con feedback formativo |
| **storyteller** | TPK | PCK | D6 | C6 | Always | Tecnología (Beamer/Quarto) al servicio de comunicación pedagógica |
| **storyteller-critic** | TPK | PK | D6 | C6 | Always | Evalúa narrativa con feedback formativo |
| **domain-referee** | CK | — | D1/D6 | C6 | Teacher-only | Conocimiento disciplinar puro |
| **methods-referee** | PCK | — | D3 | C3 | Teacher-only | Conocimiento metodológico (PCK) |
| **editor** | AI-TPACK | — | D6 | C6 | Teacher-only | Integración total del proceso editorial |
| **verifier** | TK | — | — | — | Always | Conocimiento tecnológico puro (compilación, ejecución) |

### 2.2 Skills del núcleo (clo-author/.claude/skills/)

| Skill | TPACK | Comando | Justificación |
|---|---|---|---|
| **discover** (interview) | PCK | `/discover interview` | Pedagogía + contenido para formular pregunta |
| **discover** (lit) | TCK | `/discover lit [submodo]` | Tecnología RAG accede a contenido bibliográfico |
| **discover** (data) | TCK | `/discover data` | Tecnología accede a contenido empírico |
| **discover** (ideate) | PCK | `/discover ideate` | Pedagogía guía generación de preguntas |
| **strategize** | AI-TPACK | `/strategize` | Diseño integrado |
| **strategize** (pap) | AI-TPACK | `/strategize pap` | Pre-analysis plan formal |
| **analyze** | TPK | `/analyze` | Tecnología pedagógica para análisis |
| **write** | PCK | `/write [section]` | Pedagogía de la escritura académica |
| **review** | PCK | `/review` | Evaluación con pedagogía formativa |
| **review --peer** | AI-TPACK | `/review --peer [journal]` | Simulación editorial (Teacher-only) |
| **revise** | PCK | `/revise` | Pedagogía del proceso R&R |
| **talk** | TPK | `/talk [format]` | Tecnología pedagógica de presentación |
| **submit** | AI-TPACK | `/submit [mode]` | Pipeline editorial completo (Teacher-only) |
| **new-project** | AI-TPACK | `/new-project [topic]` | Orquestación total |
| **tools** (commit, compile, validate-bib, journal, context, deploy, learn, upgrade) | TK | `/tools [subcmd]` | Herramientas técnicas |
| **tools** (debug) | TPK | `/tools debug [tipo]` | Resolución sistemática como competencia investigativa |
| **tools** (verify) | AI-TPACK | `/tools verify [target]` | Verificación rigurosa como competencia |
| **tools** (pre-register) | PCK | `/tools pre-register` | Pedagogía de hipótesis-driven research |
| **tools** (progress) | TPK | `/tools progress [flags]` | Learning Analytics (Siemens & Long 2011) |

### 2.3 Skills Auxiliares (raíz `.claude/skills/`)

| Skill | TPACK Primario | TPACK Secundario | Función en el ecosistema | Activación | Justificación pedagógica |
|---|---|---|---|---|---|
| **rag-engineer** | TK | TCK | Diseño técnico del backend RAG que alimenta `/discover lit` (Scopus, WoS, ERIC, Redalyc, SciELO) | On-demand, Background | Conocimiento tecnológico puro (TK) sobre embeddings y vector search; sirve a TCK al alimentar el pipeline de literatura |
| **research-engineer** | CK | TK | Validación matemática estricta, zero hallucination, implementaciones de alto rendimiento | On-demand | Conocimiento disciplinar (CK) en algoritmos + tecnológico (TK) en implementación; garantiza rigor científico (Lu et al. 2026 failure modes) |
| **academic-research-skills (ARS)** | AI-TPACK | PCK | Pipeline alterno con integrity gates contra failure modes documentados | On-demand | Implementa human-in-the-loop philosophy de Lu et al. 2026; complementa clo-author para investigadores avanzados |
| **skill-creator** (student edition) | TPK | PCK | Crear nuevas skills para extender el ecosistema (restringido a investigación) | On-demand | Tecnología que pedagógicamente extiende competencias formativas; restricción mantiene coherencia AI-TPACK |
| **canvas-design** | TK | TPK | Generación de PDFs/PNGs profesionales para dashboards docentes | Background (vía `/tools progress --teacher --visual`) | Tecnología puramente visual (TK); cuando se aplica a Learning Analytics se convierte en TPK |

### 2.4 References del núcleo (clo-author/.claude/references/)

| Reference | Propósito | TPACK |
|---|---|---|
| **tpack-pedagogical-framework.md** | Operacionaliza las 5 capas pedagógicas | AI-TPACK |
| **tpack-competency-model.md** | Modelo ECD: 6 competencias × 3 evidencias | AI-TPACK |
| **tpack-diagnostic-rubric.md** | Rúbrica adaptativa de diagnóstico inicial | AI-TPACK |
| **domain-profile.md** | Perfil del campo (Innovación Educativa) | CK |
| **journal-profiles.md** | Perfiles de journals para `/review --peer` | CK |

---

## 3. Mapeo Detallado: Skills Auxiliares al Pipeline TPACK

### 3.1 rag-engineer → `/discover lit`

**Relación:** rag-engineer NO se invoca por el usuario directamente. Es la base técnica que el equipo de desarrollo usa para diseñar y mantener el sistema RAG que alimenta `/discover lit`.

```
┌─────────────────────────────────────────────────────────────┐
│  ESTUDIANTE: /discover lit estado                            │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  librarian agent (TCK)                                       │
│  └─ Su sección "Modo Tutor" sabe cómo guiar al estudiante    │
└──────────────────────┬──────────────────────────────────────┘
                       │ (consulta backend RAG)
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  RAG SYSTEM (diseñado por rag-engineer — TK)                 │
│  ├─ Embeddings: text-embedding-3-large o equivalente         │
│  ├─ Vector DB: Pinecone / Chroma / Weaviate                  │
│  ├─ Chunking: párrafos académicos con overlap                │
│  ├─ Retrieval: hybrid search (semantic + BM25)               │
│  └─ Re-ranking: relevance + recency + impact                 │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────┐
│  BASES ACADÉMICAS                                            │
│  Scopus / WoS / ERIC / Redalyc / SciELO / etc.               │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
              [Resultados al librarian → al estudiante]
```

**Cuándo se invoca rag-engineer directamente:**
- Configurar/mejorar el sistema RAG
- Optimizar parámetros de retrieval
- Conectar nueva base académica
- Evaluar calidad del retrieval

**Mapeo TPACK:** TK puro (tecnología en sí); su producto sirve al pipeline TCK (acceso técnico a contenido).

### 3.2 research-engineer → Validación de Rigor

**Relación:** research-engineer es invocado cuando una tarea requiere validación matemática estricta o implementación de alto rendimiento que excede la capacidad de los agentes generales.

**Casos de uso típicos:**

| Caso | Por qué research-engineer | Mapeo TPACK |
|---|---|---|
| Implementar un estimador no estándar (e.g., bootstrap específico) | Garantiza correctitud matemática | CK + TK |
| Validar bounds teóricos de un algoritmo | Exige conocimiento formal | CK |
| Optimizar performance crítico | Implementación de bajo nivel | TK |
| Verificar zero-hallucination en outputs críticos | Filosofía contra Lu et al. 2026 failure modes | CK |

**Cómo invocarlo:**
- El strategist o coder pueden delegar a research-engineer cuando detectan que la tarea excede su scope
- Modo teacher puede invocarlo directamente para revisión de rigor

**Justificación pedagógica:** garantiza que el ecosistema NUNCA enseña al estudiante una implementación matemáticamente incorrecta. Esto es fundamental porque el aprendizaje se basa en lo que el sistema produce.

### 3.3 academic-research-skills (ARS) → Pipeline Alternativo

**Relación:** ARS es un pipeline complementario, NO un reemplazo de clo-author.

**Cuándo cada uno:**

| Necesidad | Usar |
|---|---|
| Pipeline TPACK validado para Maestría Innovación Educativa | clo-author (núcleo) |
| Investigador externo al programa que necesita pipeline general | ARS |
| Integrity gates explícitos contra Lu et al. 2026 failure modes | ARS (Stage 2.5 + Stage 4.5) |
| Modo Socrático específico para development de research questions | ARS |
| Calibración FNR/FPR del reviewer | ARS |
| Ecosistema con tutor-pedagogico, ECD, ICAP, fading | clo-author |

**Justificación AI-TPACK:** ARS aporta principios de human-in-the-loop y rigor contra failure modes que enriquecen el ecosistema. Es un órgano consultivo (Brodo 2006: consultores) más que infraestructura central.

### 3.4 skill-creator → Extensibilidad Restringida

**Relación:** skill-creator (edición estudiante) permite crear nuevas skills, pero solo en dominios académicos.

**Restricción operacional:** Antes de crear una skill, el agente verifica:

```
¿La skill propuesta cae en alguno de estos dominios?
  ✓ Metodología investigativa (revisiones, meta-análisis)
  ✓ Análisis estadístico/cualitativo
  ✓ Escritura académica
  ✓ Procesos editoriales / peer review
  ✓ Análisis bibliométrico
  ✓ Pedagogía / didáctica investigativa
  ✓ Diseño instruccional
  ✓ Evaluación educativa
  ✗ Cualquier cosa fuera de academia → RECHAZA
```

**Proceso obligatorio para nuevas skills:**

1. Verificar dominio académico
2. Asignar intersección TPACK específica
3. Definir competencia ECD que desarrolla
4. Determinar nivel de scaffolding (Modeling/Coaching/Fading)
5. Escribir sección "Modo Tutor (TPACK)" si opera en modo student
6. Documentar fundamento teórico en `theoretical-foundations.md`
7. Registrar en `architecture.md` y este documento

**Justificación AI-TPACK:** mantiene la coherencia teórica del ecosistema. Sin esta restricción, el ecosistema podría diluirse en herramientas no formativas.

### 3.5 canvas-design → Dashboard Visual Docente

**Relación:** canvas-design es invocado por `/tools progress --teacher --visual` para generar PDFs.

```
┌────────────────────────────────────────────────────────┐
│  DOCENTE: /tools progress --teacher --visual            │
└────────────────────┬───────────────────────────────────┘
                     │
                     ▼
┌────────────────────────────────────────────────────────┐
│  /tools (subcomando progress)                           │
│  └─ Recolecta datos: student-profile, journal, reviews │
└────────────────────┬───────────────────────────────────┘
                     │
                     ▼
┌────────────────────────────────────────────────────────┐
│  canvas-design skill                                    │
│  ├─ Crea filosofía de diseño académica                  │
│  ├─ Renderiza visualizaciones:                          │
│  │   • Radar de competencias TPACK (D1-D6)              │
│  │   • Trayectoria de scores                            │
│  │   • Distribución ICAP                                │
│  │   • Matriz ECD                                       │
│  │   • Badges de alertas                                │
│  └─ Output: PDF profesional                             │
└────────────────────┬───────────────────────────────────┘
                     │
                     ▼
[quality_reports/progress/YYYY-MM-DD_visual_dashboard.pdf]
```

**Mapeo TPACK:**
- canvas-design por sí solo: TK (tecnología visual)
- Aplicado a Learning Analytics docente: TPK (tecnología al servicio de la pedagogía supervisora)

**Justificación pedagógica:** los dashboards visuales mejoran la toma de decisiones del docente al permitir reconocer patrones de un vistazo (visualización para Learning Analytics — Siemens & Long, 2011).

---

## 4. Skills NO Mapeadas a TPACK (a Evitar)

Si en el futuro alguien intenta agregar una skill que NO tiene mapeo TPACK válido, NO debe formar parte del ecosistema. Ejemplos de skills que serían rechazadas:

| Skill hipotética | Por qué se rechazaría |
|---|---|
| **Generador de excusas de envío tardío** | No es académica, no enseña competencia |
| **Auto-completador del paper sin intervención** | Viola principio de "IA enseña, no escribe por el estudiante" |
| **Detector de plagio para evadir** | Filosofía asistiva, no decepcionante (Lu et al. 2026) |
| **Generador de figuras decorativas no informativas** | No mapea a competencia investigativa |
| **Chatbot conversacional general** | No tiene función pedagógica específica TPACK |

**Regla:** Antes de aceptar cualquier nueva skill o componente, este documento debe poder ubicarla en una intersección TPACK con justificación. Si no se puede, no entra.

---

## 5. Mapeo a Versiones del Ecosistema (Estudiante vs Docente)

### 5.1 Versión Estudiante

```
COMANDOS DISPONIBLES (mode: student)
┌────────────────────┬─────────────┬──────────────────────────┐
│ Comando            │ TPACK       │ Disponible en student?   │
├────────────────────┼─────────────┼──────────────────────────┤
│ /discover          │ PCK/TCK     │ ✓                        │
│ /strategize        │ AI-TPACK    │ ✓                        │
│ /analyze           │ TPK         │ ✓ (requires pre-register)│
│ /write             │ PCK         │ ✓                        │
│ /talk              │ TPK         │ ✓                        │
│ /tools (la mayoría)│ TK/TPK      │ ✓                        │
│ /tools progress    │ TPK         │ ✓ (sin --teacher)        │
│ /review (auto)     │ PCK         │ ✓                        │
│ /review --peer     │ AI-TPACK    │ ✗ Solo docente           │
│ /revise            │ PCK         │ ✗ Solo docente           │
│ /submit            │ AI-TPACK    │ ✗ Solo docente           │
│ /new-project       │ AI-TPACK    │ ✓ (con scaffolding)      │
└────────────────────┴─────────────┴──────────────────────────┘

AGENTES ACTIVOS (en student mode)
└─ Todos los workers + critics CON sección "Modo Tutor (TPACK)" activada
└─ tutor-pedagogico (supervisor pedagógico)
└─ tutor-pedagogico-critic (calidad pedagógica)

SKILLS AUXILIARES INVOCABLES
└─ canvas-design (background, vía /tools)
└─ rag-engineer (background, NO directamente)
└─ research-engineer (cuando un agente lo necesite)
└─ skill-creator (solo si admin lo permite, restringido a academia)
└─ ARS (solo si el estudiante avanzado lo elige conscientemente)
```

### 5.2 Versión Docente

```
COMANDOS DISPONIBLES (mode: teacher)
┌────────────────────┬─────────────┬──────────────────────────┐
│ Comando            │ TPACK       │ Disponible en teacher?   │
├────────────────────┼─────────────┼──────────────────────────┤
│ Todo lo anterior   │ —           │ ✓                        │
│ /review --peer     │ AI-TPACK    │ ✓ EXCLUSIVO              │
│ /revise            │ PCK         │ ✓ EXCLUSIVO              │
│ /submit            │ AI-TPACK    │ ✓ EXCLUSIVO              │
│ /tools progress    │ TPK         │ ✓ con --teacher          │
│   --teacher        │             │                          │
│ /tools progress    │ TK + TPK    │ ✓ EXCLUSIVO              │
│   --teacher        │             │                          │
│   --visual         │             │                          │
│ /tools progress    │ AI-TPACK    │ ✓ EXCLUSIVO              │
│   --teacher        │             │ (despacha error-detective)│
│   --investigate    │             │                          │
└────────────────────┴─────────────┴──────────────────────────┘

AGENTES EXCLUSIVOS DOCENTE
├─ editor (peer review)
├─ domain-referee (peer review)
├─ methods-referee (peer review)
└─ error-detective (diagnóstico de aprendizaje)

SECCIONES "Modo Tutor (TPACK)" en docente: IGNORADAS
└─ Los agentes operan en modo experto (sin scaffolding pedagógico)
```

---

## 6. Mapeo a las 6 Dimensiones Diagnósticas

### 6.1 Cobertura por Dimensión

```
DIMENSIÓN          AGENTES QUE LA IMPACTAN              SKILLS QUE LA DESARROLLAN
─────────────      ─────────────────────────            ──────────────────────────
D1 (CK)            tutor-pedagogico (diagnóstico)       /discover interview
                   domain-referee (peer review)         /new-project (briefing)

D2 (TCK)           librarian + librarian-critic         /discover lit (11 submodos)
                   explorer + explorer-critic           /discover data
                   ─ alimentado por rag-engineer ─

D3 (PCK)           strategist + strategist-critic       /strategize
                   methods-referee (peer review)        /strategize pap
                   ─ rigor validable por research-engineer ─

D4 (TPK)           data-engineer + coder-critic         /analyze
                   coder + coder-critic                 /tools pre-register
                                                        /tools debug

D5 (PCK)           writer + writer-critic               /write [section]
                                                        /revise (teacher)

D6 (TPK)           storyteller + storyteller-critic     /talk [format]
                   editor (teacher)                     /review --peer (teacher)
```

### 6.2 Skills Auxiliares por Dimensión

| Dimensión | Skill auxiliar relevante | Cómo aporta |
|---|---|---|
| D2 | rag-engineer | Backend RAG para acceso bibliográfico |
| D3 | research-engineer, ARS | Validación de rigor metodológico |
| D4 | research-engineer | Implementaciones críticas |
| D5 | ARS (modo Socrático) | Desarrollo de argumentación |
| D6 | canvas-design | Visualizaciones para presentaciones |
| Todas | skill-creator | Crear skills específicas si falta cobertura |

---

## 7. Mapeo a las 5 Capas Pedagógicas

Cada componente del ecosistema implementa una o varias capas pedagógicas:

| Componente | L1 Feedback | L2 Self-Reg | L3 Andamiaje | L4 ECD | L5 ICAP |
|---|:---:|:---:|:---:|:---:|:---:|
| Workers (librarian, strategist, etc.) | — | ✓ (P1, P2) | ✓ (Modeling/Coaching/Fading) | — | — |
| Critics (librarian-critic, etc.) | ✓ (Feed Up/Back/Forward) | ✓ (P3, P5, P6) | — | ✓ (evidencias) | — |
| tutor-pedagogico | ✓ (verificación) | ✓ (P7) | ✓ (briefing por nivel) | ✓ (decisiones de fading) | ✓ (checkpoints) |
| tutor-pedagogico-critic | ✓ (verifica calidad) | ✓ (verifica P1-P6) | ✓ (verifica scaffolding) | ✓ (verifica evaluación) | ✓ (verifica ICAP) |
| error-detective | — | — | — | ✓ (correlación de evidencias) | — |
| editor | ✓ (decisión formativa) | — | ✓ (calibración severidad) | — | — |
| rag-engineer | — | — | — | — | — |
| research-engineer | — | — | — | — | — |
| ARS | ✓ (integrity gates como feedback) | ✓ (modo Socrático) | — | ✓ (calibration mode) | ✓ (Socrático) |
| skill-creator | — | — | — | — | — |
| canvas-design | — | — | — | — | — |

**Lectura clave:**
- Componentes con ✓ en L1-L5: agentes formativos directos
- Componentes sin ningún ✓: infraestructura técnica que sirve a los formativos
- ARS implementa parcialmente todas las capas: por eso es "pipeline alterno", no infraestructura

---

## 8. Diagrama Completo: Sinergia TPACK del Ecosistema

```
                              ┌────────────────────────────┐
                              │       AI-TPACK (centro)    │
                              │   Tutor IA como 3er actor  │
                              └─────────────┬──────────────┘
                                            │
         ┌──────────────────┬───────────────┼───────────────┬──────────────────┐
         │                  │               │               │                  │
         ▼                  ▼               ▼               ▼                  ▼
    ┌────────┐        ┌─────────┐      ┌─────────┐    ┌─────────┐         ┌─────────┐
    │   CK   │        │   PK    │      │   TK    │    │  PCK    │         │  TCK    │
    │contenido│       │pedagogía│      │tecnología│    │ped+cont │         │tec+cont │
    └────┬───┘        └────┬────┘      └────┬────┘    └────┬────┘         └────┬────┘
         │                 │                │              │                   │
         ▼                 ▼                ▼              ▼                   ▼
   domain-          tutor-          rag-engineer    strategist           librarian
   referee          pedagogico      research-eng.   strategist-critic    librarian-c.
   research-eng.    tutor-ped-c.    canvas-design   writer               explorer
                    error-detect.   verifier        writer-critic        explorer-c.
                                    /tools (TK)     methods-referee      /discover
                                                    /strategize          (lit, data)
                                                    /write
                                                    /revise
                                                    /tools pre-register
                                                                ▲
                                                                │
                                            ┌───────────────────┴───────────────────┐
                                            │                  TPK                  │
                                            │            tec + pedagogía            │
                                            └───────────────────┬───────────────────┘
                                                                │
                                                                ▼
                                                       data-engineer
                                                       coder + coder-critic
                                                       storyteller + storyteller-c.
                                                       /analyze
                                                       /talk
                                                       /tools debug
                                                       /tools progress
                                                       canvas-design (aplicado)
                                                       skill-creator

         ┌──────────────────────────────────────────────────────────────────┐
         │   AI-TPACK (intersección total) — agentes y skills que integran  │
         │   pedagogía + tecnología + contenido + IA como tercer actor      │
         └─────────────────────────┬────────────────────────────────────────┘
                                   │
                                   ▼
                tutor-pedagogico, tutor-pedagogico-critic, error-detective,
                orchestrator, editor, /strategize, /review --peer, /submit,
                /new-project, /tools verify, ARS (pipeline alterno)
```

---

## 9. Reglas Operacionales Derivadas del Mapeo

### 9.1 Reglas de Invocación

1. **rag-engineer NUNCA es invocado por el estudiante.** Solo el equipo de desarrollo lo usa para diseñar el backend de `/discover lit`.

2. **research-engineer es delegado por otros agentes.** El estudiante no lo invoca directamente; los agentes (strategist, coder) lo llaman cuando necesitan validación matemática estricta.

3. **canvas-design siempre es background.** Se invoca via `/tools progress --teacher --visual`, no directamente.

4. **skill-creator requiere validación de dominio académico ANTES de crear.** Sin esto, viola la coherencia AI-TPACK.

5. **ARS y clo-author NUNCA se ejecutan simultáneamente en la misma fase.** Son pipelines separados; el estudiante elige uno y se compromete.

### 9.2 Reglas de Coherencia

1. **Toda nueva skill debe declarar su intersección TPACK.** Sin declaración, no entra al ecosistema.

2. **Toda skill que opera en modo student debe tener sección "Modo Tutor (TPACK)".** Sin esto, no respeta la pedagogía.

3. **Toda decisión de evaluación debe basarse en evidencias ECD, no solo en scores.** Score 85/100 sin evidencias demostradas = competencia NO lograda.

4. **Toda interacción en modo student debe alcanzar el ICAP mínimo.** Bypass = fallo pedagógico registrado por tutor-pedagogico-critic.

### 9.3 Reglas de Documentación

Cuando se agrega un componente nuevo, debe actualizarse:

- [ ] Este documento (`tpack-skill-mapping.md`) — mapeo TPACK
- [ ] `architecture.md` sección 2 — responsabilidades técnicas
- [ ] `theoretical-foundations.md` sección 11 — autores que justifican
- [ ] `entry-points.md` — cuándo usarlo
- [ ] `CLAUDE.md` raíz — solo si afecta identidad operativa
- [ ] `clo-author/CLAUDE.md` — solo si es parte del núcleo

---

## 10. Síntesis Ejecutiva

```
ECOSISTEMA AI-TPACK = NÚCLEO + ÓRGANOS DE SOPORTE
├── NÚCLEO (clo-author)
│   • 20 agentes con dimensión TPACK declarada
│   • 10 skills (discover, strategize, analyze, write, talk, review, revise, submit, talk, tools)
│   • 3 references (pedagogical-framework, competency-model, diagnostic-rubric)
│   • 5 capas pedagógicas implementadas
│   • Modo student/teacher con scaffolding adaptativo
│
└── ÓRGANOS DE SOPORTE (.claude/skills/ raíz)
    • rag-engineer (TK)        → backend técnico para /discover lit
    • research-engineer (CK+TK) → validación de rigor científico
    • ARS (AI-TPACK alterno)    → pipeline complementario
    • skill-creator (TPK+PCK)   → extensibilidad restringida a academia
    • canvas-design (TK→TPK)    → dashboards visuales docentes

REGLA MAESTRA: Si no mapea a TPACK, no entra al ecosistema.
```

---

## Documentos Relacionados

- [CLAUDE.md](CLAUDE.md) — Identidad operativa
- [README.md](README.md) — Cara pública con sinergia
- [architecture.md](architecture.md) — Arquitectura técnica
- [theoretical-foundations.md](theoretical-foundations.md) — Fundamentación académica
- [entry-points.md](entry-points.md) — Cuándo usar qué componente
- [clo-author/.claude/references/tpack-pedagogical-framework.md](clo-author/.claude/references/tpack-pedagogical-framework.md) — Las 5 capas operacionalizadas
- [clo-author/.claude/references/tpack-competency-model.md](clo-author/.claude/references/tpack-competency-model.md) — Modelo ECD
- [clo-author/.claude/references/tpack-diagnostic-rubric.md](clo-author/.claude/references/tpack-diagnostic-rubric.md) — Rúbrica diagnóstica
