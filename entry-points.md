# Entry Points — Cuándo Usar Qué Componente

Guía de routing para el ecosistema. Cuando el ecosistema tiene múltiples componentes que pueden parecer redundantes, este documento define cuál usar y cuándo, con árboles de decisión y ejemplos concretos.

**Principio rector:** ningún componente es de uso "general". Cada uno tiene un dominio específico. Si dudas, consulta el árbol de decisión correspondiente a tu tarea.

---

## 0. Decisión Madre: ¿Qué Estás Haciendo?

```
┌─────────────────────────────────────────────────────────────┐
│             ¿QUÉ ESTÁS INTENTANDO HACER?                     │
└────────────────────────────┬────────────────────────────────┘
                             │
        ┌────────────────────┼────────────────────┬───────────────┐
        │                    │                    │               │
        ▼                    ▼                    ▼               ▼
┌────────────────┐  ┌────────────────┐  ┌────────────────┐  ┌──────────────┐
│ INVESTIGAR     │  │ SUPERVISAR     │  │ DESARROLLAR    │  │ DISEÑAR/EXTENDER│
│ (estudiante)   │  │ (docente)      │  │ (técnico)      │  │ (extensión)   │
└────────┬───────┘  └────────┬───────┘  └────────┬───────┘  └──────┬───────┘
         │                   │                   │                 │
         ▼                   ▼                   ▼                 ▼
   Sección 1          Sección 2         Sección 3 + 4       Sección 5
```

---

## 1. Para el Estudiante: Pipeline de Investigación

**Modo:** `student` (configurado en `clo-author/CLAUDE.md`)

### 1.1 Mi primera vez en el ecosistema

```
¿Existe student-profile.md en quality_reports/?
        │
   ┌────┴────┐
   │         │
  NO         SÍ
   │         │
   ▼         ▼
Saluda al    Continúa con
tutor-       el pipeline
pedagogico   normal
   │
   ▼
Diagnóstico inicial automático
(6-8 preguntas adaptativas)
   │
   ▼
student-profile.md generado
   │
   ▼
Confirma tu perfil con el tutor
```

**Comando:** Simplemente saluda al ecosistema. El `tutor-pedagogico` toma control automáticamente.

### 1.2 Tengo un tema de investigación en mente

```
            ┌──────────────────────────┐
            │ ¿Qué tan claro está      │
            │ tu problema de invest.?  │
            └────────────┬─────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
   "Solo un tema"   "Pregunta vaga"  "Pregunta clara"
        │                │                │
        ▼                ▼                ▼
  /discover         /discover         Salta a
  interview         interview         /discover lit
  (6 preguntas)     (refinamiento)    directamente
```

### 1.3 Necesito hacer revisión de literatura

```
                    /discover lit
                          │
           ┌──────────────┴──────────────┐
           │                             │
   ¿Qué tipo de revisión?          Si no sabes:
           │                       Ejecuta secuencia
   ┌───────┼─────────┬─────────┐   recomendada:
   │       │         │         │
   ▼       ▼         ▼         ▼   1. estado
estado  marco    metodología vacio  2. marco
   │       │         │         │   3. metodologia
   │       │         │         │   4. bibliometria
   ▼       ▼         ▼         ▼   5. contexto
oportunidad debates riesgo  etica  6. vacio
                                   7. oportunidad
              + sintesis al final  8. riesgo
                                   9. debates
                                   10. etica
                                   11. sintesis
```

**11 submodos disponibles** — ver `architecture.md` sección 7 para descripción completa.

### 1.4 Necesito datos para mi investigación

```
        /discover data
              │
              ▼
        explorer + explorer-critic
              │
              ▼
        Evaluación de fuentes:
        • Acceso (público/restringido)
        • Cobertura (tiempo, geografía)
        • Calidad (peer-review, autoridad)
        • Compatibilidad con tu diseño
              │
              ▼
        student-profile.md actualiza
        evidencia E2.1 (data dimension)
```

### 1.5 Necesito diseñar mi metodología

```
              /strategize
                    │
                    ▼
            strategist + strategist-critic
                    │
        ¿Es estudio de tesis?
                    │
            ┌───────┴───────┐
            │               │
            ▼               ▼
        strategy         /strategize pap
        memo             (pre-analysis plan)
            │
            ▼
        Si modo student:
        Antes de /analyze, ejecuta
        /tools pre-register
        (documenta hipótesis ANTES)
```

### 1.6 Necesito hacer análisis de datos

```
        /tools pre-register [análisis]   ← OBLIGATORIO modo student
              │
              ▼
        Documenta predicciones:
        • Sign esperado del efecto
        • Magnitud esperada
        • Significancia esperada
        • Reasoning teórico
              │
              ▼
        /analyze
              │
              ▼
        coder + data-engineer + coder-critic
              │
              ▼
        Compara resultados vs predicciones
        (actualiza pre-registration document)
              │
              ▼
        Si hay desviaciones:
        /tools debug results
```

### 1.7 Necesito escribir secciones del paper

```
        ¿Qué sección?
              │
   ┌──────────┼──────────┬──────────┐
   │          │          │          │
   ▼          ▼          ▼          ▼
intro     methods     results    conclusion
   │          │          │          │
   └──────────┴────┬─────┴──────────┘
                   │
                   ▼
              /write [section]
                   │
                   ▼
              writer + writer-critic
                   │
                   ▼
              Si tu nivel D5 = Principiante:
              Recibirás Modeling con ejemplos
              Si Intermedio:
              Recibirás Coaching con plantilla
              Si Avanzado:
              Recibirás solo la instrucción
```

### 1.8 Necesito preparar una presentación

```
              /talk
                │
        ¿Qué formato?
                │
   ┌────────────┼────────────┬────────────┐
   │            │            │            │
   ▼            ▼            ▼            ▼
job-market  seminar      short        lightning
(40-50)     (25-35)      (10-15)      (3-5 slides)
   │            │            │            │
   └────────────┴─────┬──────┴────────────┘
                      │
                      ▼
              storyteller + storyteller-critic
```

### 1.9 Algo no funciona (LaTeX, scripts, datos, resultados)

```
                /tools debug
                      │
              ¿Qué tipo de problema?
                      │
        ┌─────────────┼─────────────┬─────────────┐
        │             │             │             │
        ▼             ▼             ▼             ▼
      latex         script         data         results
   (compilación) (R/Stata/Py)  (limpieza/    (sign raro,
                                merge)        magnitud)
        │             │             │             │
        └─────────────┴──────┬──────┴─────────────┘
                             │
                             ▼
                    Protocolo 4 fases:
                    1. Investigar causa raíz
                    2. Analizar patrón
                    3. Hipótesis y prueba
                    4. Implementar fix
```

**IRON LAW:** No hay fix sin investigación de causa raíz primero.

### 1.10 Quiero verificar que mi trabajo está completo

```
              /tools verify
                    │
            ¿Qué verificar?
                    │
   ┌────────┬───────┼───────┬────────┬────────┐
   │        │       │       │        │        │
   ▼        ▼       ▼       ▼        ▼        ▼
compile  script   bib    score   replication  all
(LaTeX) (Rscript)               (full re-run)
```

### 1.11 Quiero ver mi propio progreso

```
              /tools progress
                    │
                    ▼
        Dashboard estudiante:
        • Mapa TPACK (D1-D6)
        • Pipeline status
        • Evidencias ECD
        • Quality gates
        • Fading progress
        • ICAP summary
        • Próximos pasos
```

---

## 2. Para el Docente: Supervisión y Evaluación

**Modo:** `teacher` (configurado en `clo-author/CLAUDE.md`)

### 2.1 Quiero ver el progreso de mis estudiantes

```
        /tools progress --teacher
                │
                ▼
        Dashboard textual:
        • Alertas (inactividad, stalled, decline)
        • Comparativo entre estudiantes
        • Mapa TPACK por estudiante
        • Patrones ICAP
        • Calidad pedagógica del sistema
```

### 2.2 Quiero un dashboard visual para presentar

```
        /tools progress --teacher --visual
                │
                ▼
        canvas-design genera PDF con:
        • Radar de competencias
        • Trayectoria de scores
        • Distribución ICAP
        • Matriz ECD
        • Badges de alertas
```

### 2.3 Un estudiante está atascado, no entiendo qué pasa

```
        /tools progress --teacher --investigate [estudiante]
                │
                ▼
        error-detective ejecuta:
        1. Phase 1: Data Landscape Analysis
        2. Phase 2: Root Cause (Five Whys)
        3. Phase 3: Cross-dimension correlation
        4. Phase 4: Intervention design
                │
                ▼
        Reporte con:
        • Patrón identificado (de los 7 documentados)
        • Causa raíz
        • Cascada cross-dimensión
        • Recomendaciones específicas
```

### 2.4 Quiero hacer peer review de un trabajo

```
        /review --peer [journal]
                │
                ▼
        editor + domain-referee + methods-referee
                │
                ▼
        Decisión editorial:
        Accept / Minor / Major Revisions / Reject
                │
                ▼
        Si R&R:
        /revise [report]  → routing por tipo de comentario
```

### 2.5 El estudiante está listo para enviar a journal

```
        /submit
            │
        ¿Qué fase?
            │
   ┌────────┼────────┬────────┐
   │        │        │        │
   ▼        ▼        ▼        ▼
target  package   audit   final
(jrnl)  (replic.) (10     (score >=95
                  checks) + all >=80)
```

---

## 3. Para Diseño Técnico: Skills Auxiliares

### 3.1 Cuándo usar `rag-engineer` (en `.claude/skills/` raíz)

```
        ¿Necesitas implementar/mejorar
        el sistema RAG que alimenta /discover lit?
                    │
            ┌───────┴───────┐
            │               │
           NO              SÍ
            │               │
            ▼               ▼
        NO USES        USA rag-engineer
        rag-engineer   PARA:
        directamente   • Diseñar embeddings
                       • Optimizar retrieval
                       • Configurar chunking
                       • Evaluar similarity metrics
                       • Conectar con Scopus/WoS/ERIC/Redalyc/SciELO
```

**Cuándo NO usar rag-engineer:**
- Para hacer una búsqueda simple → usa `/discover lit`
- Para escribir el paper → usa `/write`
- Para análisis cualitativo de literatura → usa `/discover lit estado`

### 3.2 Cuándo usar `research-engineer` (en `.claude/skills/` raíz)

```
        ¿Tu tarea requiere rigor matemático
        ESTRICTO o validación formal?
                    │
            ┌───────┴───────┐
            │               │
           NO              SÍ
            │               │
            ▼               ▼
        NO USES        USA research-engineer
        research-      PARA:
        engineer       • Implementar algoritmos críticos
                       • Validación matemática formal
                       • Verificar bounds teóricos
                       • Implementaciones de alto rendimiento
                       • Cuando 0% alucinación es no-negociable
```

**Cuándo NO usar research-engineer:**
- Para pipeline de investigación normal → usa los agentes del clo-author
- Para escribir secciones del paper → usa `/write`
- Para revisar literatura → usa `/discover lit`

### 3.3 Cuándo usar `academic-research-skills` (ARS)

```
        ¿Eres estudiante de la Maestría
        Innovación Educativa siguiendo el ecosistema TPACK?
                    │
            ┌───────┴───────┐
            │               │
           SÍ              NO
            │               │
            ▼               ▼
        Usa el          ARS es ALTERNATIVO
        ecosistema      Útil si:
        TPACK           • Quieres integrity gates contra
        (clo-author)      Lu et al. (2026) failure modes
                        • Necesitas calibración FNR/FPR
        ARS NO          • Eres investigador avanzado
        REEMPLAZA         externo al programa
        clo-author      • Quieres modo Socrático específico
```

**Decisión clave:** ARS y clo-author NO son intercambiables. clo-author es el ecosistema validado del proyecto; ARS es un pipeline complementario para investigadores que ya dominan su workflow.

### 3.4 Cuándo usar `skill-creator` (en `.claude/skills/` raíz)

```
        ¿Necesitas extender el ecosistema
        con una nueva funcionalidad?
                    │
            ┌───────┴───────┐
            │               │
           NO              SÍ
            │               │
            ▼               ▼
        NO USES        ¿La funcionalidad
        skill-creator  está en dominio académico?
                              │
                      ┌───────┴───────┐
                      │               │
                     NO              SÍ
                      │               │
                      ▼               ▼
                skill-creator    USA skill-creator
                EDICIÓN          PARA:
                ESTUDIANTE       • Crear nueva skill
                NO PERMITE       • Mapearla a TPACK
                FUERA DE         • Definir su evidencia ECD
                INVESTIGACIÓN    • Documentar fundamento teórico
```

**Restricción importante:** skill-creator está en edición estudiante — solo permite crear skills relacionadas con investigación y academia. No es un creador de skills general.

### 3.5 Cuándo usar `canvas-design` (en `clo-author/.claude/skills/`)

```
        ¿Necesitas generar un PDF/PNG
        con diseño profesional?
                    │
            ┌───────┴───────┐
            │               │
           NO              SÍ
            │               │
            ▼               ▼
        NO USES        Usa canvas-design VIA:
        canvas-design  • /tools progress --teacher --visual
        directamente   • Cualquier comando que genere
                         dashboards visuales
                       • NO para generar tablas LaTeX
                         (eso es del writer)
```

---

## 4. Para Tareas Específicas: Routing por Necesidad

### 4.1 "Necesito una referencia bibliográfica"

```
                ¿Para qué?
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
   Citar en       Buscar      Validar que
   el paper       sobre un    una cita es
   ya escrita     tema        real
        │           │           │
        ▼           ▼           ▼
   El writer    /discover    /tools verify bib
   maneja la    lit estado   (cross-reference
   citación     o /discover  contra
                lit marco    Bibliography_base.bib)
```

### 4.2 "Tengo un error en mi código de R/Python/Stata"

```
                ¿El error es...?
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
   Sintaxis     Lógica/      Datos
   básica       resultados   inesperados
   (typo)       raros
        │           │           │
        ▼           ▼           ▼
   Arregla     /tools debug  /tools debug
   directo     script        data
                │             │
                └──────┬──────┘
                       │
                       ▼
                Si después de 3 fixes
                no resuelve:
                ESCALA al strategist-critic
                (puede ser problema de
                estrategia, no de código)
```

### 4.3 "No sé qué método usar para mi pregunta"

```
        Modo student?
            │
    ┌───────┴───────┐
    │               │
   SÍ              NO
    │               │
    ▼               ▼
/strategize    /strategize
+ MODELING     directo
(estrategia
+ ejemplo
con tema
diferente)
    │
    ▼
strategist propone
2-3 opciones con
trade-offs
    │
    ▼
TÚ eliges y justificas
(Coaching)
```

### 4.4 "Necesito presentar mi tesis pronto"

```
        ¿Cuánto tiempo tienes?
                │
    ┌───────────┼───────────┐
    │           │           │
    ▼           ▼           ▼
> 2 semanas  1-2 semanas  < 1 semana
    │           │           │
    ▼           ▼           ▼
/talk       /talk seminar  /talk short
job-market  (25-35)        (10-15)
(40-50)
    │           │           │
    └───────────┴───────────┘
                │
                ▼
        + storyteller-critic
        + canvas-design para visuales
```

### 4.5 "Mi profesor me dio comentarios sobre mi avance"

```
        ¿Eres docente o estudiante?
                │
        ┌───────┴───────┐
        │               │
   ESTUDIANTE          DOCENTE
        │               │
        ▼               ▼
   Léelos con          /revise [report]
   atención.           (clasifica
   Si modo student     comentarios)
   y son del docente:
   - NUEVO ANÁLISIS  → /analyze
   - CLARIFICACIÓN   → /write
   - DESACUERDO      → discute con docente
   - MENOR           → /write
```

---

## 5. Para Extender o Crear Componentes

### 5.1 "Quiero agregar un nuevo agente especializado"

```
1. Identifica:
   - ¿Qué intersección TPACK aporta? (CK/PK/TK/PCK/TCK/TPK/AI-TPACK)
   - ¿Qué competencia ECD desarrolla? (C1-C6 o nueva)
   - ¿Qué dimensión diagnóstica impacta? (D1-D6 o nueva)
   - ¿Quién es su crítico pareado?

2. Crea archivo en clo-author/.claude/agents/[nombre].md
3. Agrega sección "Modo Tutor (TPACK)" si opera en modo student
4. Registra par worker-critic en clo-author/.claude/rules/agents.md
5. Documenta en architecture.md (sección 2)
6. Si introduce framework nuevo: theoretical-foundations.md
```

### 5.2 "Quiero agregar una nueva fase al pipeline"

```
1. Modifica dependency graph en orchestrator.md
2. Agrega comando en /tools o como skill independiente
3. Mapea a competencia ECD (existente o nueva)
4. Si crea nueva: edita tpack-competency-model.md
5. Si modo student: define scaffolding por nivel
6. Documenta en architecture.md sección 5
```

### 5.3 "Quiero agregar una nueva dimensión diagnóstica"

```
1. Edita tpack-diagnostic-rubric.md (agrega D7+)
2. Diseña preguntas adaptativas con Guided Inquiry
3. Define indicadores observables por nivel
4. Mapea agentes que impactan esta dimensión
5. Actualiza student-profile.md template
6. Documenta justificación teórica en theoretical-foundations.md
```

### 5.4 "Quiero documentar una decisión de diseño"

```
        ¿Qué tipo de decisión?
                │
   ┌────────────┼────────────┬────────────┐
   │            │            │            │
   ▼            ▼            ▼            ▼
Operativa   Arquitec-     Teórica     Específica
(día a día) tural        (fundamen-   de fase
            (compo-      to)         (research
            nentes)                  spec)
   │            │            │            │
   ▼            ▼            ▼            ▼
CLAUDE.md  architec-    theoretical-  research_spec_
(raíz)     ture.md      foundations   ecosistema_ia
                        .md           .md
```

---

## 6. Anti-Patrones de Routing

### 6.1 NO uses estos componentes para esto:

| Componente | NO usar para | Usa en su lugar |
|---|---|---|
| `tutor-pedagogico` | Generar artefactos de investigación | Los agentes worker (librarian, strategist, etc.) |
| `tutor-pedagogico-critic` | Dar feedback al estudiante | Los agentes critic correspondientes |
| `error-detective` | Bugs técnicos (LaTeX, scripts) | `/tools debug` |
| `/tools debug` | Dificultades de aprendizaje | `/tools progress --teacher --investigate` |
| `rag-engineer` | Hacer una búsqueda concreta | `/discover lit [submodo]` |
| `research-engineer` | Pipeline normal de investigación | Agentes del clo-author |
| `skill-creator` | Crear skills no académicas | Skill-creator solo permite skills de investigación |
| `canvas-design` | Tablas LaTeX | El writer maneja tablas |
| `ARS` | Reemplazar clo-author | Son complementarios, no intercambiables |
| `/review --peer` (modo student) | Auto-evaluar tu trabajo | Solo modo teacher tiene peer review |
| `/submit` (modo student) | Enviar a journal | Funcionalidad exclusiva docente |

### 6.2 Errores comunes de routing

**"Voy a usar `/analyze` sin pre-registro porque ya sé qué resultado quiero"**
→ Modo student requiere `/tools pre-register` ANTES. Si ya sabes el resultado, documéntalo como predicción.

**"Voy a saltar el diagnóstico inicial porque ya sé en qué nivel estoy"**
→ El diagnóstico ES un momento de aprendizaje. No saltarlo.

**"Voy a usar `/tools debug` para entender por qué mis resultados son raros"**
→ Si los resultados son raros y NO hay error técnico, usa `/tools debug results`. Si los resultados están BIEN pero NO esperabas eso, es interpretación → usa `/strategize` o consulta strategist-critic.

**"Voy a usar canvas-design para crear figuras del paper"**
→ Las figuras del paper las genera el data-engineer en formato publication-ready (.pdf/.png para LaTeX). canvas-design es para dashboards docentes.

**"Voy a usar `/discover lit estado` y luego ya está la revisión"**
→ Una sola pasada es insuficiente. Usa la secuencia recomendada (estado → marco → metodologia → bibliometria → contexto → vacio → oportunidad → riesgo → debates → etica → sintesis).

---

## 7. Casos de Uso Combinados

### 7.1 "Empiezo mi tesis desde cero"

```
1. Saluda al ecosistema → diagnóstico inicial automático
2. /discover interview [tu tema] → research spec
3. /discover lit (secuencia 11 submodos)
4. /discover data → evaluación de fuentes
5. /strategize → diseño metodológico
6. /tools pre-register [análisis principal]
7. /analyze → ejecución del análisis
8. /write intro → /write methods → /write results → /write conclusion
9. /tools verify all
10. /talk seminar → presentación
11. (Modo teacher) /review --peer → simulación peer review
12. /revise (si R&R)
13. (Modo teacher) /submit
```

### 7.2 "Mi docente me pidió mejorar la sección de literatura"

```
1. /tools progress → ver mi nivel D2 actual
2. /discover lit [submodo específico] (ej: marco si falta marco teórico)
3. librarian-critic me da feedback con 5 capas
4. tutor-pedagogico-critic verifica la calidad pedagógica
5. ICAP checkpoint: explico qué cambié y por qué
6. Si nivel D2 sube → student-profile.md se actualiza
```

### 7.3 "Mi script de R no corre y no entiendo por qué"

```
1. /tools debug script
2. Phase 1: Investigación de causa raíz
   - Leer error completo del traceback
   - Reproducir con set.seed()
   - git diff (¿qué cambió?)
   - Trazar flujo de datos
3. Phase 2: Patrón
   - Comparar con scripts que sí funcionan
4. Phase 3: Hipótesis única + test minimal
5. Phase 4: Fix + verify + dispatch coder-critic
```

### 7.4 "Quiero saber si mi avance está listo para mostrar al docente"

```
1. /tools verify all → confirma que todo compila/corre
2. /tools progress → revisar mis evidencias ECD
3. Si todas evidencias DEMONSTRATED y score >= 80:
   → listo para mostrar
4. Si alguna PARTIAL:
   → identificar qué falta y completar
5. Si modo teacher activo en docente:
   El docente verá tu progreso vía /tools progress --teacher
```

### 7.5 "Soy docente. Tengo 8 estudiantes y quiero ver quién está atascado"

```
1. /tools progress --teacher
   → Dashboard con alertas por estudiante
2. Identifica los estudiantes con HIGH risk
3. Para cada uno: /tools progress --teacher --investigate [nombre]
   → error-detective genera reporte diagnóstico
4. Implementa intervenciones recomendadas
5. /tools progress --teacher --visual
   → PDF para presentar en reunión de comité
```

---

## 8. Tabla Maestra: Comando → Cuándo Usarlo

| Comando | Cuándo | Modo | Componente principal |
|---|---|---|---|
| `/discover interview` | Tienes solo un tema o pregunta vaga | student/teacher | tutor-pedagogico (en student) |
| `/discover lit [submodo]` | Necesitas literatura específica | student/teacher | librarian + librarian-critic |
| `/discover data` | Necesitas evaluar fuentes de datos | student/teacher | explorer + explorer-critic |
| `/strategize` | Diseñar estrategia empírica | student/teacher | strategist + strategist-critic |
| `/strategize pap` | Pre-analysis plan formal | teacher | strategist |
| `/analyze` | Ejecutar análisis de datos | student/teacher | coder + data-engineer |
| `/write [section]` | Redactar sección del paper | student/teacher | writer + writer-critic |
| `/talk [format]` | Crear presentación | student/teacher | storyteller + storyteller-critic |
| `/review` | Auto-revisión de calidad | student/teacher | critics correspondientes |
| `/review --peer` | Simulación peer review | **teacher only** | editor + referees |
| `/review --peer --r2` | R&R round 2 | teacher only | editor |
| `/revise` | Procesar comentarios de referees | teacher only | router de comentarios |
| `/submit target` | Recomendaciones de journal | teacher only | submission pipeline |
| `/submit package` | Replication package | teacher only | submission pipeline |
| `/submit final` | Gate final >=95 | teacher only | submission pipeline |
| `/tools commit` | Git commit con score | both | git |
| `/tools compile` | Compilar LaTeX 3-pass | both | LaTeX toolchain |
| `/tools validate-bib` | Verificar citas vs bib | both | bibliography validator |
| `/tools journal` | Regenerar timeline | both | research_journal |
| `/tools context` | Estado del contexto | both | context manager |
| `/tools deploy` | Publicar guía Quarto | both | Quarto |
| `/tools learn` | Extraer aprendizajes | both | memory extractor |
| `/tools upgrade` | Actualizar clo-author | both | upgrade tool |
| `/tools debug [tipo]` | Investigar problema técnico | both | systematic debugging |
| `/tools verify [target]` | Verificar con evidencia fresca | both | verification gate |
| `/tools pre-register` | Documentar predicciones | both (obligatorio en student) | hypothesis tracker |
| `/tools progress` | Mi progreso | student | dashboard |
| `/tools progress --teacher` | Dashboard supervisión | **teacher** | learning analytics |
| `/tools progress --teacher --visual` | PDF visual | teacher | canvas-design |
| `/tools progress --teacher --investigate` | Diagnóstico aprendizaje | teacher | error-detective |
| `/new-project [topic]` | Pipeline completo orquestado | both | new-project skill |

---

## 9. Cuando Dudes

```
        ¿No sabes qué usar?
                │
                ▼
        Pregúntale a Claude:
        "Estoy intentando [X]. ¿Qué componente debo usar?"
                │
                ▼
        Claude consulta este documento
        y te enruta al componente correcto
```

**Principio final:** este documento es el árbol de decisión maestro. Si encuentras un caso no cubierto, repórtalo para extender el documento.

---

## Documentos Relacionados

- [CLAUDE.md](CLAUDE.md) — Identidad operativa
- [README.md](README.md) — Cara pública
- [architecture.md](architecture.md) — Cómo se conectan los componentes técnicamente
- [theoretical-foundations.md](theoretical-foundations.md) — Por qué cada componente existe
- [clo-author/CLAUDE.md](clo-author/CLAUDE.md) — Configuración del pipeline
