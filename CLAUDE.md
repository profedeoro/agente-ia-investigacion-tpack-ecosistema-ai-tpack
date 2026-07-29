# Agente IA para Investigación — Ecosistema AI-TPACK

**Proyecto:** Diseño y validación de un ecosistema de formación investigativa mediado por la interacción estudiante-IA-docente desde el enfoque AI-TPACK
**Institución:** Politécnico Grancolombiano
**Programa:** Maestría en Innovación Educativa
**Investigador principal:** Daniel Eduardo Villalba de Oro
**Repositorio TPACK:** https://github.com/profedeoro/AI-academicresearchtutorTPACK

---

## Identidad del Proyecto

Este NO es un asistente de investigación generalista. Es un **ecosistema tecnopedagógico** diseñado bajo el modelo AI-TPACK donde la IA actúa como **tercer actor pedagógico** en la tríada estudiante-IA-docente, no como herramienta que el estudiante "usa".

**Pregunta de investigación que articula todo el proyecto:**
> ¿Cómo diseñar y validar un ecosistema de formación investigativa mediado por IA que, fundamentado en AI-TPACK y articulado con la tríada estudiante-IA-docente, fortalezca las competencias investigativas y reduzca la sobrecarga de acompañamiento docente en posgrado?

**Hipótesis:** El ecosistema mejora la calidad de avances de trabajo de grado y reduce la carga de correcciones repetitivas para docentes asesores.

---

## Principios Operativos (cargados cada sesión)

1. **La IA es actor pedagógico, no herramienta.** Cada agente del ecosistema cumple una función formativa específica dentro de una intersección TPACK (CK / PK / TK / PCK / TCK / TPK / AI-TPACK).

2. **Tríada inseparable.** Estudiante (sujeto en formación) ↔ Tutor IA (tercer actor) ↔ Docente (asesor experto). La IA nunca sustituye al docente; lo libera de tareas rutinarias para que se enfoque en lo formativo complejo.

3. **Dos modos, tres niveles.**
   - Modo `student`: tutor formativo con scaffolding adaptativo (Principiante / Intermedio / Avanzado)
   - Modo `teacher`: pipeline experto + dashboard de supervisión + diagnóstico de dificultades

4. **Cinco capas pedagógicas científicamente fundamentadas:**
   - L1: Feedback estructurado (Hattie & Timperley, 2007 + Shute, 2008)
   - L2: Autorregulación (Nicol & Macfarlane-Dick, 2006)
   - L3: Andamiaje disciplinar (Cognitive Apprenticeship — Collins, Brown & Newman, 1989 + Guided Inquiry — Kuhlthau et al., 2007)
   - L4: Evaluación por evidencias (Evidence-Centered Design — Mislevy et al., 2003)
   - L5: Diseño de interacciones (ICAP — Chi & Wylie, 2014)

5. **Verificación bibliográfica obligatoria.** El tutor IA debe verificar toda cita contra un identificador resoluble (DOI) antes de presentarla; toda cita no verificable debe marcarse explícitamente como tal. El modelo puede equivocarse: estudiantes y docentes asesores deben verificar las referencias entregadas. La integración automatizada con bases de suscripción (Scopus, WoS) requiere convenio institucional y **no está implementada**; el mecanismo de verificación actual se apoya en búsqueda web y APIs abiertas.

6. **Calidad medida por evidencias, no por scores.** Un artefacto puede tener score 85/100, pero si las evidencias ECD no se demuestran, la competencia no está lograda.

7. **Plan-first, verify-after.** Antes de tareas no triviales: planificar. Al final: verificar con evidencia fresca (`/tools verify`).

---

## Arquitectura del Ecosistema

```
agente_ia/                          (raíz del proyecto)
├── CLAUDE.md                       (este archivo — cargado cada sesión)
├── README.md                       (cara pública del proyecto)
├── architecture.md                 (mapeo de componentes)
├── theoretical-foundations.md      (todos los frameworks consolidados)
├── entry-points.md                 (cuándo usar qué componente)
│
├── .claude/
│   └── skills/                     (skills disponibles a nivel raíz)
│       ├── academic-research-skills/    (suite ARS — pipeline alterno)
│       ├── rag-engineer/                (sistemas RAG para /discover lit)
│       ├── research-engineer/           (rigor científico, zero hallucination)
│       └── skill-creator/               (extender el ecosistema)
│
└── clo-author/                     (NÚCLEO TPACK — pipeline principal)
    ├── CLAUDE.md                   (config del pipeline)
    ├── .claude/
    │   ├── agents/                 (20 agentes con lógica TPACK)
    │   │   ├── tutor-pedagogico.md           (supervisor pedagógico)
    │   │   ├── tutor-pedagogico-critic.md    (calidad pedagógica)
    │   │   ├── error-detective.md            (diagnóstico aprendizaje — docente)
    │   │   ├── orchestrator.md               (flujo modo estudiante)
    │   │   ├── librarian / explorer / strategist / coder / writer / storyteller
    │   │   └── + critics + referees + editor
    │   ├── references/             (frameworks teóricos cargados on-demand)
    │   │   ├── tpack-pedagogical-framework.md
    │   │   ├── tpack-competency-model.md
    │   │   └── tpack-diagnostic-rubric.md
    │   └── skills/                 (10 skills del pipeline)
    │       ├── /discover, /strategize, /analyze, /write, /talk, /review, /revise, /submit, /new-project
    │       └── /tools (commit, compile, debug, verify, pre-register, progress, ...)
    └── quality_reports/            (planes, perfiles, reportes pedagógicos)
        ├── student-profile.md      (generado por diagnóstico inicial)
        ├── pedagogical-review.md   (calidad del feedback del sistema)
        ├── research_journal.md     (timeline del proceso)
        └── specs/, plans/          (diseño y planificación)
```

**Núcleo (clo-author):** El ecosistema TPACK opera aquí. Es el artefacto tecnopedagógico que se valida en la prueba piloto.
**Soporte (.claude/skills/):** Skills auxiliares que alimentan el núcleo (RAG para literatura, rigor científico, creación de nuevas skills).

---

## Fundamentación de "Ecosistema"

El término "ecosistema" no es metáfora suelta — está fundamentado en literatura pedagógica:

- **Gómez Valderrama:** un ecosistema es un conjunto de organismos donde cada subsistema cumple funciones específicas que generan sinergia hacia la función general del núcleo.
- **Brodo (2006):** los ecosistemas de aprendizaje tienen tres categorías — proveedores de contenido, consultores, infraestructura.
- **Chang & Güetl (2007):** distinguen partes vivas (maestros, tutores, diseñadores) de partes no vivas (contenidos, tecnologías, herramientas).
- **Pata (2011):** ecosistemas centrados en aprendiz autónomo y autodirigido, con relaciones simbióticas (mutualismo) entre componentes.

**En este proyecto:** clo-author es el núcleo (pipeline de investigación), las skills auxiliares son organismos especializados, y la tríada estudiante-IA-docente genera la sinergia formativa.

---

## Estado del Proyecto (Validación Empírica)

| Fase | Estado | Detalle |
|------|--------|---------|
| Encuesta de percepción docente | Completada | Resultados positivos en pregrado y posgrado |
| Validación por juicio de expertos | Completada | Instrumento Likert validado |
| Prueba piloto | Pendiente | 15-20 estudiantes Maestría Innovación Educativa, 1 año |

**Diseño de la prueba piloto:**
- Muestra: 15-20 estudiantes de semestre 1 + sus docentes asesores
- Duración: 1 año (3 meses preparación + 5 meses implementación + 4 meses análisis)
- Tipo de estudio: diseño y validación (Design-Based Research; Reeves, 2006; McKenney & Reeves, 2012)
- Indicador principal: percepción de docentes y estudiantes (cualitativo + Likert)
- Indicadores complementarios: ciclos de corrección, tiempo de retroalimentación

---

## Cómo Operar en Este Proyecto

**Si el modo es `student`** (definido en `clo-author/CLAUDE.md`):
1. El `tutor-pedagogico` realiza diagnóstico inicial si no existe `student-profile.md`
2. Cada fase del pipeline activa scaffolding adaptado al nivel del estudiante en esa dimensión
3. Los críticos entregan feedback formativo (Feed Up/Back/Forward + ECD evidences + ICAP)
4. El `tutor-pedagogico-critic` evalúa la calidad pedagógica del feedback (escala /20)

**Si el modo es `teacher`:**
1. Pipeline opera en modo experto (sin scaffolding pedagógico)
2. Disponible: `/tools progress --teacher` (dashboard), `--visual` (PDF), `--investigate` (error-detective)
3. Funcionalidades exclusivas: `/review --peer`, `/submit`, `/revise`

**Comandos universales (ambos modos):**
- `/discover` (interview, lit con 11 submodos, data, ideate)
- `/strategize`, `/analyze`, `/write`, `/talk`
- `/tools` (commit, compile, validate-bib, debug, verify, pre-register, progress, ...)

---

## Documentación Detallada

| Documento | Cuándo consultar |
|-----------|------------------|
| `README.md` | Visión general del proyecto, instalación, primeros pasos |
| `architecture.md` | Cómo se integran clo-author + skills auxiliares |
| `theoretical-foundations.md` | Todos los frameworks teóricos con citas completas |
| `entry-points.md` | Routing: cuándo usar qué componente |
| `tpack-skill-mapping.md` | Mapeo operacional de cada componente a su intersección TPACK |
| `clo-author/CLAUDE.md` | Configuración operativa del pipeline TPACK |
| `clo-author/quality_reports/research_spec_ecosistema_ia.md` | Especificación completa de la investigación |

---

## Marca del Proyecto

Este proyecto es un **ecosistema de formación investigativa**, no un generador de papers. Los outputs sin reflexión metacognitiva ni verificación de evidencias ECD no son válidos en el modo estudiante. La IA enseña; el estudiante aprende; el docente supervisa.

**Bottom line:** Si el estudiante no puede explicar lo que produjo, no lo aprendió. Si el docente no validó la rúbrica automatizada, no es evaluación final. Si el feedback no cumple las 5 capas, no es formativo.
