# Arquitectura del Ecosistema AI-TPACK

Documento técnico que describe cómo se integran los componentes del proyecto, los flujos de datos entre ellos, los puntos de extensión y el modelo de persistencia. Complementa al `README.md` (cara pública) y al `CLAUDE.md` (identidad operativa).

---

## 1. Vista de Alto Nivel

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          CAPA DE INTERFAZ                                │
│   Claude Code CLI / VS Code Extension / Desktop App                      │
└────────────────────────────────┬────────────────────────────────────────┘
                                 │
┌────────────────────────────────▼────────────────────────────────────────┐
│                       CAPA DE ORQUESTACIÓN                               │
│                                                                          │
│   orchestrator.md  ──→  Detecta mode (student/teacher) en CLAUDE.md     │
│                    ──→  Despacha agentes según fase y nivel              │
│                    ──→  Aplica reglas de escalación                      │
└─────┬──────────────────────────────────────────────────────────┬────────┘
      │ (mode: student)                                          │ (mode: teacher)
      │                                                          │
┌─────▼─────────────────────────┐                ┌──────────────▼─────────────┐
│   CAPA PEDAGÓGICA              │                │   CAPA DE SUPERVISIÓN      │
│                                │                │                            │
│   tutor-pedagogico             │                │   /tools progress --teacher│
│   ├─ F1: Diagnostic            │                │   ├─ Dashboard textual     │
│   ├─ F2: Phase Briefing        │                │   ├─ --visual (canvas-PDF) │
│   ├─ F3: Pedagogical Translation│                │   └─ --investigate (E.D.) │
│   ├─ F4: Comprehension Check   │                │                            │
│   ├─ F5: Fading Decision       │                │   error-detective          │
│   └─ F6: Teacher Report        │                │   └─ Five Whys + patrones │
│                                │                │                            │
│   tutor-pedagogico-critic      │                │   /review --peer           │
│   └─ Score pedagógico /20       │                │   /submit                  │
│                                │                │   /revise                  │
└─────┬──────────────────────────┘                └────────────┬───────────────┘
      │                                                          │
      └──────────────────────┬──────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────────────────┐
│                  CAPA DE PIPELINE DE INVESTIGACIÓN                       │
│                                                                          │
│   workers (creators)        ←→        critics (reviewers)                │
│   ─ librarian              ←→         librarian-critic                   │
│   ─ explorer               ←→         explorer-critic                    │
│   ─ data-engineer          ←→         coder-critic                       │
│   ─ strategist             ←→         strategist-critic                  │
│   ─ coder                  ←→         coder-critic                       │
│   ─ writer                 ←→         writer-critic                      │
│   ─ storyteller            ←→         storyteller-critic                 │
│                                                                          │
│   peer review:    editor → domain-referee + methods-referee              │
│   verification:   verifier (pass/fail)                                   │
└────────────────────────────┬────────────────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────────────────┐
│                   CAPA DE SOPORTE (.claude/skills/ raíz)                 │
│                                                                          │
│   rag-engineer            → alimenta /discover lit (11 submodos)         │
│   research-engineer       → valida rigor científico (zero hallucination) │
│   academic-research-skills→ pipeline alterno con integrity gates         │
│   skill-creator           → permite extender el ecosistema               │
│   canvas-design           → genera dashboards visuales (PDF/PNG)         │
└────────────────────────────┬────────────────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────────────────┐
│                  CAPA DE PERSISTENCIA (quality_reports/)                 │
│                                                                          │
│   student-profile.md          → diagnóstico + niveles + evidencias ECD  │
│   research_journal.md         → timeline de actividad por agente         │
│   pedagogical-review.md       → calidad pedagógica del feedback (/20)   │
│   reviews/                    → reportes de críticos                     │
│   plans/                      → planes de implementación                 │
│   specs/                      → especificaciones de diseño               │
│   pre-registration/           → predicciones antes de análisis           │
│   progress/                   → snapshots de progreso (texto + visual)   │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Mapa de Componentes y Responsabilidades

### Núcleo (clo-author/)

| Componente | Tipo | Función Única | Lee | Escribe |
|---|---|---|---|---|
| **orchestrator** | Infraestructura | Despacha agentes según modo, fase y nivel | CLAUDE.md, dependency graph | research_journal.md |
| **tutor-pedagogico** | Worker (supervisor) | Diagnóstico + briefing + traducción pedagógica + checkpoints + fading + reportes | student-profile.md, todos los outputs | student-profile.md, research_journal.md |
| **tutor-pedagogico-critic** | Critic | Evalúa calidad pedagógica del feedback (/20) | feedback de todos los críticos | pedagogical-review.md |
| **error-detective** | Worker (diagnóstico) | Análisis de causa raíz de dificultades de aprendizaje (solo modo teacher) | student-profile.md, research_journal.md, pedagogical-review.md | reportes de intervención |
| **librarian / librarian-critic** | Worker / Critic | Revisión de literatura (TCK) | bases académicas vía rag-engineer | annotated bibliography |
| **explorer / explorer-critic** | Worker / Critic | Evaluación de fuentes de datos (TCK) | data documentation | data assessment |
| **data-engineer / coder-critic** | Worker / Critic | Pipeline de limpieza de datos (TPK) | raw data | cleaned data + scripts |
| **strategist / strategist-critic** | Worker / Critic | Diseño de estrategia empírica (PCK / AI-TPACK) | literatura, data | strategy memo |
| **coder / coder-critic** | Worker / Critic | Implementación de análisis (TPK) | strategy memo, data | scripts + results |
| **writer / writer-critic** | Worker / Critic | Redacción académica (PCK) | results, strategy | paper sections |
| **storyteller / storyteller-critic** | Worker / Critic | Presentaciones académicas (TPK) | paper | Beamer/Quarto |
| **editor** | Infraestructura (peer review) | Simulación editorial: desk review + asignación de referees + decisión | paper | decision letter |
| **domain-referee / methods-referee** | Referees | Revisión por pares simulada | paper | referee reports |
| **verifier** | Infraestructura | Verificación de compilación, ejecución, replicación | outputs | pass/fail report |

### Soporte (.claude/skills/ raíz)

| Skill | Función | Cuándo se invoca |
|---|---|---|
| **rag-engineer** | Diseño de sistema RAG sobre Scopus, WoS, ERIC, Redalyc, SciELO, Semantic Scholar, OpenAlex | Implementación técnica del backend de `/discover lit` |
| **research-engineer** | Rigor científico, zero hallucination, verificación formal | Cuando se requiere validación matemática estricta o implementación de algoritmos críticos |
| **academic-research-skills (ARS)** | Pipeline alterno con integrity gates contra failure modes de Lu et al. (2026) | Investigadores avanzados que quieren un pipeline complementario con calibración FNR/FPR |
| **skill-creator** | Crear nuevas skills (edición estudiante restringida a investigación) | Cuando el ecosistema necesita una nueva funcionalidad formativa |
| **canvas-design** | Generación de PDFs/PNGs con diseño profesional | `/tools progress --teacher --visual` |

---

## 3. Flujo de Datos: Modo `student`

```
[INICIO DE SESIÓN]
        │
        ▼
┌───────────────────────┐
│  CLAUDE.md cargado    │  (mode: student, level: auto)
└──────────┬────────────┘
           │
           ▼
┌────────────────────────────┐  Existe student-profile.md?
│  orchestrator detecta modo │ ─┬─→ NO  → dispatch tutor-pedagogico (F1)
└──────────┬─────────────────┘  │       └─→ Diagnóstico 6-8 preguntas
           │                     │       └─→ Genera student-profile.md
           │                     │
           │                     └─→ SI  → continúa al pipeline
           ▼
┌────────────────────────────────────────────────────────┐
│  USUARIO INVOCA UNA FASE (ej: /strategize)             │
└──────────┬─────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  PRE-PHASE                                              │
│  orchestrator → tutor-pedagogico (F2: Phase Briefing)   │
│  ├─ Lee student-profile.md (nivel D3 = strategist)      │
│  ├─ Lee tpack-competency-model.md (C3, evidencias)      │
│  └─ Genera briefing adaptado:                           │
│     • Principiante → Modeling con ejemplo               │
│     • Intermedio  → Coaching con plantilla              │
│     • Avanzado    → Fading                              │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  WORKER (strategist)                                    │
│  ├─ Aplica scaffolding según briefing                   │
│  ├─ Solicita autoevaluación al estudiante (Nicol P2)    │
│  └─ Estudiante envía artefacto                          │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  CRITIC (strategist-critic)                             │
│  ├─ Score estándar del artefacto                        │
│  ├─ Evalúa evidencias ECD (E3.1, E3.2, E3.3)            │
│  ├─ Genera feedback Feed Up/Back/Forward                │
│  └─ Máximo 3 brechas prioritarias (Shute)               │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  POST-FEEDBACK                                          │
│  orchestrator → tutor-pedagogico (F3 + F4)              │
│  ├─ F3: Verifica calidad del feedback                   │
│  │   └─ Si falta capa, complementa antes de entregar    │
│  └─ F4: Comprehension checkpoint                        │
│      └─ Pide explicación nivel ICAP mínimo:             │
│         • Principiante → Activo                         │
│         • Intermedio  → Constructivo                    │
│         • Avanzado    → Interactivo                     │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  QUALITY GATE                                           │
│  orchestrator → tutor-pedagogico-critic                 │
│  └─ Evalúa la interacción completa (5 dimensiones, /20) │
│     ├─ Score >= 13 → continúa                           │
│     └─ Score < 13 → reporta y agente ajusta             │
│                  └─ 3 fallos consecutivos → ESCALA      │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  FADING DECISION                                        │
│  orchestrator → tutor-pedagogico (F5)                   │
│  └─ Verifica criterios de fading:                       │
│     • Score >= 75/85                                    │
│     • Comprehension >= 2/3 o 3/3                        │
│     • ICAP alcanzado                                    │
│     • Evidencias ECD demostradas                        │
│  └─ Si todos cumplen → sube nivel en esa dimensión      │
│  └─ Actualiza student-profile.md                        │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
┌────────────────────────────────────────────────────────┐
│  REGISTRO                                               │
│  Todos los eventos → research_journal.md                │
│  Score pedagógico → pedagogical-review.md               │
│  Artefactos → carpetas correspondientes                 │
└──────────┬──────────────────────────────────────────────┘
           │
           ▼
[SIGUIENTE FASE — según dependency graph]
```

---

## 4. Flujo de Datos: Modo `teacher`

```
[CONFIGURACIÓN INICIAL]
        │
        ▼
┌─────────────────────────────────┐
│  CLAUDE.md (mode: teacher)      │
└──────────┬──────────────────────┘
           │
           │ Camino A: Supervisión continua
           ▼
┌─────────────────────────────────────────────┐
│  /tools progress --teacher                   │
│  ├─ Lee student-profile.md de cada estudiante│
│  ├─ Lee research_journal.md                  │
│  ├─ Lee pedagogical-review.md                │
│  └─ Genera dashboard textual:                │
│     • Alertas (inactividad, stalled, decline)│
│     • Comparativo entre estudiantes          │
│     • Mapa TPACK por estudiante              │
│     • Patrones ICAP                          │
│     • Calidad pedagógica del sistema         │
└─────────────────────────────────────────────┘

           │ Camino B: Dashboard visual
           ▼
┌─────────────────────────────────────────────┐
│  /tools progress --teacher --visual          │
│  ├─ Recolecta los datos del Camino A         │
│  ├─ Estructura JSON para visualización       │
│  └─ Invoca canvas-design skill:              │
│     • Filosofía de diseño académica          │
│     • Radar de competencias TPACK            │
│     • Trayectoria de scores                  │
│     • Distribución ICAP                      │
│     • Matriz ECD de evidencias               │
│     └─ Output: PDF en quality_reports/progress│
└─────────────────────────────────────────────┘

           │ Camino C: Diagnóstico profundo
           ▼
┌─────────────────────────────────────────────┐
│  /tools progress --teacher --investigate [E] │
│  └─ Despacha error-detective:                │
│     ├─ Phase 1: Data Landscape Analysis      │
│     ├─ Phase 2: Root Cause (Five Whys)       │
│     ├─ Phase 3: Cross-dimension correlation  │
│     └─ Phase 4: Intervention design          │
│  └─ Output: reporte diagnóstico              │
└─────────────────────────────────────────────┘

           │ Camino D: Peer Review supervisado
           ▼
┌─────────────────────────────────────────────┐
│  /review --peer [journal]                    │
│  └─ editor + domain-referee + methods-referee│
│     └─ Funcionalidad exclusiva docente       │
└─────────────────────────────────────────────┘
```

---

## 5. Pipeline de Investigación: 8 Fases con Dependencias

```
                    DESCUBRIMIENTO
        ┌────────────┬────────────┬────────────┐
        │            │            │            │
        ▼            ▼            ▼            ▼
   /discover    /discover    /discover     /discover
   interview    lit (11      data           ideate
   (D1, CK)     submodos)    (D2/D4, TCK)
                (D2, TCK)
        │            │            │            │
        └────────────┴─────┬──────┴────────────┘
                           │
                           ▼ (al menos uno completo)
                       ESTRATEGIA
                       /strategize
                       (D3, AI-TPACK / PCK)
                           │
                           ▼ (score >= 80)
                       EJECUCIÓN
            ┌──────────────┴──────────────┐
            │                             │
            ▼                             ▼
        /analyze                       /write
        (D4, TPK)                      (D5, PCK)
        coder + data-engineer          writer
            │                             │
            └──────────────┬──────────────┘
                           │
                           ▼ (ambos score >= 80)
                       PEER REVIEW
                       /review --peer
                       (modo teacher)
                           │
                           ▼ (Accept o R&R)
                       PRESENTACIÓN
                       /talk
                       (D6, TPK)
                           │
                           ▼
                       SUBMISSION
                       /submit
                       (modo teacher)
```

**Reglas de activación:**
- Una fase activa solo si sus dependencias están en estado >= PARTIAL
- Modo student: orchestrator verifica además que la competencia ECD prerrequisita esté demostrada
- Quality gates: 80 (commit), 90 (PR), 95 (submission)

---

## 6. Capas Pedagógicas: Cómo se Inyectan en el Pipeline

Las 5 capas no son código separado — se aplican como instrucciones que cada agente lee al momento de actuar:

```
Cada agente en modo student lee:
  ├─ Su sección "Modo Tutor (TPACK)" (en su propio archivo .md)
  └─ Si necesita más detalle:
       └─ references/tpack-pedagogical-framework.md (on-demand)
```

**Ejecución por capa:**

| Capa | Dónde se ejecuta | Cuándo |
|---|---|---|
| **L1: Feedback (Hattie+Shute)** | Agentes critic (sección TPACK) | Cuando entregan retroalimentación |
| **L2: Self-Regulation (Nicol)** | Agentes worker (P1, P2) + critic (P3, P5, P6) + tutor-pedagogico (P7) | Antes (criterios), durante (autoevaluación), después (diálogo) |
| **L3: Scaffolding (Cog. Apprenticeship)** | Agentes worker (Modeling/Coaching/Fading) | Al inicio de cada fase, según nivel |
| **L4: ECD (Mislevy)** | Agentes critic (evidencias) + tutor-pedagogico (decisiones de fading) | Después de scoring, antes de fading |
| **L5: ICAP (Chi & Wylie)** | tutor-pedagogico (checkpoints) + tutor-pedagogico-critic (verificación) | Después de feedback, antes de continuar |

---

## 7. Sistema RAG para `/discover lit` (11 Submodos)

```
┌───────────────────────────────────────────────────────────┐
│  Usuario: /discover lit estado                             │
└─────────────────┬─────────────────────────────────────────┘
                  │
                  ▼
┌───────────────────────────────────────────────────────────┐
│  librarian agent                                           │
│  └─ Consulta el sistema RAG (diseñado por rag-engineer)    │
└─────────────────┬─────────────────────────────────────────┘
                  │
                  ▼
┌───────────────────────────────────────────────────────────┐
│  CAPA RAG (Bases académicas — todo trazable)               │
│                                                            │
│   PRIORIDAD ALTA:                                          │
│   ├─ Scopus (Elsevier, 27k+ journals)                      │
│   ├─ Web of Science (Clarivate)                            │
│   ├─ ERIC (US Dept. of Education)                          │
│   ├─ Redalyc (Latinoamérica)                               │
│   └─ SciELO (acceso abierto LATAM)                         │
│                                                            │
│   PRIORIDAD MEDIA:                                         │
│   ├─ Semantic Scholar (AI2)                                │
│   ├─ OpenAlex                                              │
│   ├─ Google Scholar                                        │
│   ├─ Dialnet (España e Iberoamérica)                       │
│   └─ DOAJ (open access verificado)                         │
└─────────────────┬─────────────────────────────────────────┘
                  │
                  ▼
┌───────────────────────────────────────────────────────────┐
│  PRINCIPIO: Cero alucinaciones. Toda referencia trazable.  │
└───────────────────────────────────────────────────────────┘
```

**11 submodos disponibles** (cada uno con dimensión TPACK explícita):

| Submodo | Entrega | Dimensión |
|---|---|---|
| `estado` | Síntesis del estado del arte | TCK |
| `oportunidad` | Oportunidades de investigación | PCK |
| `riesgo` | Riesgos del tema | PCK |
| `vacio` | Vacíos documentados | TCK |
| `etica` | Consideraciones éticas | PCK |
| `marco` | Mapeo teórico | CK |
| `debates` | Controversias activas | PCK |
| `metodologia` | Tendencias metodológicas | TCK |
| `bibliometria` | Análisis bibliométrico | TK |
| `contexto` | Contextualización regional | PCK |
| `sintesis` | Documento integrador | AI-TPACK |

---

## 8. Persistencia y Estado

```
quality_reports/
├── student-profile.md            ← FUENTE DE VERDAD del nivel del estudiante
│   • Niveles por dimensión D1-D6
│   • Evidencias ECD demostradas (C1-C6, x.1, x.2, x.3)
│   • Trayectoria de fading
│   • Criterios pendientes para subir nivel
│
├── research_journal.md           ← TIMELINE de actividad
│   • Una entrada por invocación de agente
│   • Score, veredicto, ruta del reporte
│   • Phase transitions
│
├── pedagogical-review.md         ← CALIDAD del feedback del sistema
│   • Score /20 por interacción
│   • Dimensiones evaluadas
│   • Recomendaciones a agentes
│   • Escalaciones
│
├── reviews/                      ← REPORTES de los críticos
│   ├── librarian-critic_*.md
│   ├── strategist-critic_*.md
│   ├── coder-critic_*.md
│   └── ...
│
├── plans/                        ← PLANES de implementación
│   └── YYYY-MM-DD_*.md
│
├── specs/                        ← ESPECIFICACIONES de diseño
│   └── YYYY-MM-DD_*.md
│
├── pre-registration/             ← HIPÓTESIS antes de análisis
│   └── YYYY-MM-DD_*.md
│
└── progress/                     ← SNAPSHOTS de progreso
    ├── YYYY-MM-DD_progress.md   (texto)
    └── YYYY-MM-DD_visual_dashboard.pdf  (canvas-design)
```

**Reglas de persistencia:**
- `student-profile.md` se actualiza después de cada fase (F5 del tutor-pedagogico)
- `research_journal.md` se acumula append-only
- `pedagogical-review.md` se acumula append-only
- Los outputs de fase nunca sobrescriben — versionados por fecha
- Git tracking obligatorio para todos excepto datos crudos

---

## 9. Patrón Worker-Critic (Separación de Poderes)

Patrón fundacional heredado de clo-author original, extendido con tutor-pedagogico:

```
┌──────────────────────────────────────────────────────────┐
│   REGLA: Críticos nunca crean. Creadores nunca se        │
│          auto-evalúan. Score siempre del crítico pareado.│
└──────────────────────────────────────────────────────────┘

Pares Worker-Critic:
  librarian              ←→  librarian-critic
  explorer               ←→  explorer-critic
  data-engineer          ←→  coder-critic
  strategist             ←→  strategist-critic
  coder                  ←→  coder-critic
  writer                 ←→  writer-critic
  storyteller            ←→  storyteller-critic
  tutor-pedagogico       ←→  tutor-pedagogico-critic   ← NUEVO con TPACK
```

**Tres-strikes escalation:**
- 3 rondas sin convergencia → escala según `agents.md`
- Coder/data-engineer fallidos → strategist-critic
- Writer fallido → orchestrator
- Strategist/Librarian/Explorer/Storyteller fallidos → User
- **NUEVA: tutor-pedagogico-critic 3 fallos pedagógicos → tutor-pedagogico interviene + alerta al docente**

---

## 10. Puntos de Extensión

El ecosistema es extensible en cuatro vectores:

**A. Nuevos agentes especializados**
- Crear archivo en `clo-author/.claude/agents/`
- Agregar par worker-critic en `agents.md`
- Si es modo student: incluir sección "Modo Tutor (TPACK)"
- Definir dimensión TPACK + competencia ECD asignada

**B. Nuevas fases de pipeline**
- Modificar dependency graph en `orchestrator.md`
- Agregar comando en `/tools` o como skill independiente
- Mapear a competencia ECD existente o crear nueva en `tpack-competency-model.md`

**C. Nuevas dimensiones diagnósticas**
- Editar `tpack-diagnostic-rubric.md` (agregar D7+)
- Actualizar formato de `student-profile.md`
- Mapear nuevos agentes a la dimensión

**D. Nuevos frameworks pedagógicos**
- Editar `tpack-pedagogical-framework.md`
- Documentar en `theoretical-foundations.md`
- Modificar agentes afectados con nueva sección o ampliación de la existente

---

## 11. Integración con skill-creator

`skill-creator` (en .claude/skills/raíz, edición estudiante) está restringido a dominios académicos. Cuando se invoca, debe:

1. Verificar que la nueva skill esté en dominio de investigación/academia
2. Mapearla a una intersección TPACK específica
3. Generar la sección "Modo Tutor (TPACK)" si la skill operará en modo student
4. Registrar la skill en `architecture.md` (este archivo)
5. Documentar fundamento teórico en `theoretical-foundations.md`

---

## 12. Modelo de Modos: student vs teacher

```
┌──────────────────────────────────────────────────────────────┐
│                    CONFIGURACIÓN DE MODO                      │
│              (clo-author/CLAUDE.md, línea ~12)               │
└────────────────────────────┬─────────────────────────────────┘
                             │
                ┌────────────┴────────────┐
                │                         │
                ▼                         ▼
       ┌────────────────┐        ┌────────────────┐
       │  mode: student │        │  mode: teacher │
       └───────┬────────┘        └───────┬────────┘
               │                         │
   ┌───────────┴───────────┐    ┌───────┴────────┐
   │ Activa:                │    │ Activa:        │
   │ • TPACK secciones      │    │ • Pipeline     │
   │ • tutor-pedagogico     │    │   experto      │
   │ • Diagnóstico inicial  │    │ • /review --peer│
   │ • 5 capas pedagógicas  │    │ • /submit      │
   │ • Scaffolding adaptat. │    │ • /revise      │
   │ • Checkpoints ICAP     │    │ • progress     │
   │ • Fading decisions     │    │   --teacher    │
   │ • Pedagogical reviews  │    │ • error-detective│
   │                        │    │ • canvas-design│
   │ Bloquea:               │    │                │
   │ • /review --peer       │    │ Ignora:        │
   │ • /submit              │    │ • Secciones    │
   │ • /revise              │    │   "Modo Tutor" │
   └────────────────────────┘    └────────────────┘
```

---

## 13. Anti-Patrones (qué NO hacer)

- ❌ Que un crítico cree artefactos (rompe separación de poderes)
- ❌ Que un creator se auto-evalúe (rompe separación de poderes)
- ❌ Avanzar de fase sin que las competencias prerrequisitas estén PARTIAL+ (modo student)
- ❌ Marcar fading sin que TODOS los criterios se cumplan
- ❌ Bypass del checkpoint ICAP "porque el estudiante ya entendió"
- ❌ Usar referencias bibliográficas no trazables a las bases del RAG
- ❌ Saltar `/tools verify` antes de declarar trabajo completo
- ❌ Usar `/tools debug` con propuestas de fix antes de Phase 1 (root cause)
- ❌ Ejecutar análisis sin pre-registro documentado (modo student)

---

## 14. Métricas del Sistema

| Métrica | Origen | Uso |
|---|---|---|
| **Score por componente** | Critics (librarian-critic, etc.) | Quality gates 80/90/95 |
| **Score pedagógico** | tutor-pedagogico-critic | Detección de fallos pedagógicos |
| **Evidencias ECD** | Critics + tutor-pedagogico | Decisiones de fading |
| **Nivel ICAP alcanzado** | tutor-pedagogico (F4) | Verificación de comprensión |
| **Frecuencia de uso** | research_journal.md + git log | Learning Analytics docente |
| **Self-assessment accuracy** | Diferencia auto-eval vs critic eval | Metacognición del estudiante |
| **Tiempo en fase** | Timestamps en research_journal | Detección de stalled phases |

---

## 15. Resumen Operacional

```
PROYECTO = ECOSISTEMA AI-TPACK
├── PROPÓSITO: Validar empíricamente la hipótesis del proyecto
├── NÚCLEO: clo-author (pipeline TPACK con 20 agentes)
├── ÓRGANOS: rag-engineer, research-engineer, ARS, skill-creator, canvas-design
├── MODOS: student (formativo) | teacher (supervisión)
├── CAPAS: 5 pedagógicas + 1 de investigación + 1 de soporte
├── PERSISTENCIA: quality_reports/ (texto plano markdown, git-trackable)
└── EXTENSIBILIDAD: 4 vectores documentados
```

---

## Documentos Relacionados

- [CLAUDE.md](CLAUDE.md) — Identidad operativa cargada cada sesión
- [README.md](README.md) — Cara pública del proyecto
- [theoretical-foundations.md](theoretical-foundations.md) — Marcos teóricos consolidados (Paso 4)
- [entry-points.md](entry-points.md) — Routing entre componentes (Paso 5)
- [clo-author/CLAUDE.md](clo-author/CLAUDE.md) — Configuración del pipeline TPACK
- [clo-author/quality_reports/research_spec_ecosistema_ia.md](clo-author/quality_reports/research_spec_ecosistema_ia.md) — Especificación completa de la investigación
