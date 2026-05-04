# Agente IA para Investigación

> **Ecosistema tecnopedagógico AI-TPACK** para formación investigativa en posgrado.
> Diseñado y validado bajo la tríada **estudiante — tutor IA — docente**.

[![License: CC BY-NC 4.0](https://img.shields.io/badge/license-CC%20BY--NC%204.0-lightgrey)](https://creativecommons.org/licenses/by-nc/4.0/)
[![Status](https://img.shields.io/badge/status-pilot--ready-blue)](#estado-de-la-investigación)
[![TPACK](https://img.shields.io/badge/framework-AI--TPACK-purple)](#por-qué-este-proyecto-es-distinto)
[![Institution](https://img.shields.io/badge/institution-Polit%C3%A9cnico%20Grancolombiano-orange)](https://www.poli.edu.co)

---

## El Problema que Resolvemos

La masificación del posgrado generó un círculo vicioso en la Maestría en Innovación Educativa del Politécnico Grancolombiano: **sobrecarga docente → retroalimentación insuficiente → avances fragmentados → más correcciones repetitivas → afectación de tasas de graduación y calidad investigativa**.

La literatura confirma el patrón en Latinoamérica: la relación estudiante-asesor excede la capacidad efectiva de acompañamiento (De Kleijn et al., 2012; Pyhältö et al., 2015), las competencias de escritura académica no se desarrollan sistemáticamente (Carlino, 2013; Moreno et al., 2024), y existe un vacío en la integración pedagógica de IA en formación investigativa (OECD, 2021; UNESCO, 2021).

**Nuestra hipótesis:** un ecosistema de formación investigativa mediado por IA, diseñado desde AI-TPACK y articulado con la tríada estudiante-IA-docente, mejora la calidad de los avances y reduce la carga de correcciones repetitivas comparado con el modelo tradicional.

---

## Por Qué Este Proyecto es Distinto

Existen herramientas de IA para investigación. Lo que **no existe** es un sistema que integre los tres elementos —pedagogía, IA, acompañamiento investigativo— bajo un marco teórico coherente, validado empíricamente, en contexto latinoamericano de posgrado.

Este proyecto se distingue en **cuatro frentes simultáneos**:

| Frente | Otros sistemas | Este ecosistema |
|---|---|---|
| **Rol de la IA** | La IA es herramienta que el estudiante "usa" | La IA es **tercer actor pedagógico** con funciones formativas propias en cada intersección TPACK |
| **Tipo de feedback** | Evaluativo: "tu score es 75" | **Formativo de 5 capas:** Hattie+Shute + Nicol + Cognitive Apprenticeship + ECD + ICAP |
| **Adaptación al estudiante** | Mismo output para todos | **Diagnóstico inicial científico** + 3 niveles de scaffolding por dimensión TPACK |
| **Apoyo al docente** | No existe o es genérico | **Dashboard de aprendizaje + diagnóstico de dificultades** con base en Learning Analytics y Cognitive Apprenticeship |

---

## La Sinergia: Cómo Trabajan Juntos los Componentes

El proyecto NO es una colección de herramientas. Es un ecosistema donde cada componente cumple una función específica en la tríada, fundamentado en **Brodo (2006)**, **Chang & Güetl (2007)**, **Pata (2011)** y **Gómez Valderrama**:

```
                     ┌─────────────────────────────────────────┐
                     │         TRÍADA AI-TPACK                  │
                     │                                          │
                     │   ESTUDIANTE  ←→  TUTOR IA  ←→  DOCENTE │
                     │   (formación)    (3er actor)   (asesor)  │
                     └────────────────────┬─────────────────────┘
                                          │
                          ┌───────────────┴───────────────┐
                          │                               │
                          ▼                               ▼
             ┌────────────────────────┐    ┌──────────────────────────┐
             │   NÚCLEO: clo-author   │    │   ÓRGANOS DE SOPORTE     │
             │   (pipeline TPACK)     │    │   (.claude/skills/)      │
             ├────────────────────────┤    ├──────────────────────────┤
             │ • 20 agentes con TPACK │    │ • rag-engineer           │
             │ • tutor-pedagogico     │    │   (literatura rigurosa)  │
             │ • error-detective      │    │ • research-engineer      │
             │ • 5 capas pedagógicas  │    │   (rigor científico)     │
             │ • 6 dim. diagnósticas  │    │ • academic-research-skills│
             │ • Modo student/teacher │    │   (pipeline complemento) │
             │ • /tools (10 subcmds)  │    │ • skill-creator          │
             │ • canvas-design        │    │   (extensibilidad)       │
             └────────────────────────┘    └──────────────────────────┘
                          │                               │
                          └───────────────┬───────────────┘
                                          │
                                          ▼
                          ┌─────────────────────────────────────┐
                          │   VALIDACIÓN EMPÍRICA               │
                          │   • Encuesta percepción ✓           │
                          │   • Juicio de expertos ✓            │
                          │   • Prueba piloto (15-20 est.) ⏳   │
                          └─────────────────────────────────────┘
```

### Cómo cada componente sirve al objetivo central

| Componente | Tipo (Chang & Güetl) | Rol en la tríada | Dimensión TPACK que activa |
|---|---|---|---|
| **clo-author (núcleo)** | Parte viva — tutor + crítico + pedagogo | Tutor IA: 8 fases formativas, 3 niveles, 5 capas | AI-TPACK (intersección total) |
| **rag-engineer** | Parte no viva — infraestructura RAG | Soporte al `/discover lit` con 11 submodos sobre Scopus, WoS, ERIC, Redalyc, SciELO | TCK (Tecnología + Contenido) |
| **research-engineer** | Parte viva — validador de rigor | Garantiza zero-hallucination y rigor científico en outputs | CK + TK |
| **academic-research-skills (ARS)** | Parte viva — pipeline alterno | Pipeline alternativo para investigadores avanzados con integrity gates | PCK + TPK |
| **skill-creator** | Parte viva — diseñador instruccional | Permite extender el ecosistema con nuevas funcionalidades formativas | TPK |
| **canvas-design** | Parte no viva — herramienta visual | Genera dashboards visuales para el docente (PDF/PNG) | TK + TPK |

**Principio:** ningún componente opera en aislamiento. clo-author orquesta el proceso formativo; los demás alimentan, validan o extienden lo que clo-author produce.

---

## La Experiencia del Estudiante (Modo `student`)

```
1. PRIMERA SESIÓN
   tutor-pedagogico ejecuta diagnóstico inicial (6-8 preguntas adaptativas)
   ↓
   Genera student-profile.md con tu nivel en 6 dimensiones TPACK:
   • D1: Formulación de problemas (CK)
   • D2: Dominio de literatura (TCK)
   • D3: Diseño metodológico (PCK)
   • D4: Competencia analítica (TPK)
   • D5: Escritura académica (PCK)
   • D6: Comunicación científica (TPK)

2. DURANTE EL TRABAJO DE GRADO
   Para cada fase (literatura → estrategia → análisis → escritura → presentación):
   
   ANTES:    tutor-pedagogico te brinda según tu nivel:
             • Principiante → Modeling (te muestra ejemplo, narra decisiones)
             • Intermedio  → Coaching (te guía mientras ejecutas)
             • Avanzado    → Fading (te da la instrucción y revisa al final)
   
   DURANTE:  El agente correspondiente trabaja contigo (librarian, strategist, coder, writer...)
             Te pide autoevaluación antes de enviar al crítico
   
   FEEDBACK: El crítico te da retroalimentación formativa de 5 capas:
             • Feed Up: ¿hacia dónde vas?
             • Feed Back: ¿cómo vas? (fortalezas + máximo 3 brechas con consecuencias)
             • Feed Forward: ¿qué sigue? (acción concreta + ejemplo si eres principiante)
   
   CHECKPOINT: tutor-pedagogico verifica tu comprensión (nivel ICAP mínimo según tu nivel):
               • Activo (Principiante): explicas qué cambiaste y por qué
               • Constructivo (Intermedio): justificas tus decisiones, anticipas objeciones
               • Interactivo (Avanzado): debates con el crítico, defiendes tu trabajo
   
   FADING:   Si demuestras evidencias ECD + score + ICAP suficientes, subes de nivel
             en esa dimensión específica (no global)

3. ACUMULACIÓN
   Cada interacción se registra en student-profile.md
   El docente ve tu progreso en tiempo real vía /tools progress --teacher
```

---

## La Experiencia del Docente (Modo `teacher`)

```
1. CONFIGURACIÓN
   El docente recibe el ecosistema completo + 5 funcionalidades exclusivas
   con base científica para supervisión

2. SUPERVISIÓN COTIDIANA
   /tools progress --teacher
   ↓ Genera dashboard textual con:
     • Alertas de supervisión (inactividad, fases estancadas, scores declinantes)
     • Progreso comparativo entre estudiantes
     • Mapa de competencias TPACK por estudiante
     • Patrones ICAP de interacción
     • Calidad pedagógica del sistema (score /20)

3. DASHBOARD VISUAL
   /tools progress --teacher --visual
   ↓ Genera PDF diseñado con canvas-design:
     • Radar de competencias por dimensión
     • Trayectoria de scores en el tiempo
     • Distribución ICAP
     • Matriz de evidencias ECD
     • Badges de alertas

4. DIAGNÓSTICO PROFUNDO
   /tools progress --teacher --investigate [estudiante]
   ↓ Despacha error-detective:
     • Five Whys para dificultades de aprendizaje
     • Correlación cross-dimensión
     • Identificación de patrones (diagnostic mismatch, scaffolding gap, passive learning, etc.)
     • Recomendaciones específicas de intervención

5. FUNCIONALIDADES DOCENTES EXCLUSIVAS (con fundamento científico)
   • Dashboard de seguimiento — Learning Analytics (Siemens & Long, 2011)
   • Comparación de versiones — Evaluación formativa (Hattie & Timperley, 2007; Carlino, 2013)
   • Retroalimentación asistida — Scaffolding (Vygotsky, 1978; VanLehn, 2011)
   • Rúbrica automatizada — Rúbricas analíticas (Jonsson & Svingby, 2007; Biggs, 2011)
   • Reporte de uso — Self-Regulated Learning (Zimmerman, 2002; Gašević et al., 2015)

6. LO QUE EL DOCENTE NUNCA DELEGA
   • Validación final de rúbricas automatizadas
   • Decisiones formativas críticas (cambio de tema, escalación, R&R)
   • Evaluación final del trabajo de grado
```

---

## Inicio Rápido

### Si eres **estudiante**

1. Asegúrate de que tu instalación tenga `mode: student` en `clo-author/CLAUDE.md`
2. Abre Claude Code en el directorio del proyecto
3. Saluda al `tutor-pedagogico` — iniciará el diagnóstico automáticamente
4. Después del diagnóstico, ejecuta `/discover interview [tu tema]` para empezar
5. Sigue la secuencia: `discover → strategize → analyze → write → talk`

### Si eres **docente**

1. Cambia a `mode: teacher` en `clo-author/CLAUDE.md`
2. Configura los proyectos de tus estudiantes (uno por subdirectorio)
3. Ejecuta `/tools progress --teacher` para tu dashboard
4. Para PDF visual: `/tools progress --teacher --visual`
5. Para diagnóstico profundo: `/tools progress --teacher --investigate [estudiante]`

### Si eres **investigador validando el ecosistema**

1. Lee [research_spec_ecosistema_ia.md](clo-author/quality_reports/research_spec_ecosistema_ia.md) para la especificación completa
2. Lee [theoretical-foundations.md](theoretical-foundations.md) para los frameworks
3. Lee [architecture.md](architecture.md) para entender cómo se integran los componentes
4. La prueba piloto está documentada en la spec: 15-20 estudiantes, 1 año, modalidad virtual

---

## Estado de la Investigación

| Fase | Estado | Resultado |
|---|---|---|
| Encuesta de percepción docente (pregrado y posgrado) | ✓ Completada | Resultados positivos |
| Validación por juicio de expertos | ✓ Completada | Instrumento Likert validado |
| **Prueba piloto** (15-20 estudiantes Maestría Innovación Educativa) | ⏳ Pendiente | Diseño Design-Based Research, 1 año |
| Análisis y publicación | ⏳ Pendiente | Posterior a piloto |

**Tipo de estudio:** Diseño y validación (no cuasi-experimental). El objetivo es validar pertinencia y funcionalidad del ecosistema, no inferir efectos causales (Reeves, 2006; McKenney & Reeves, 2012).

---

## Fundamentación Académica

Este proyecto NO es un proyecto de software con justificación posterior. Cada decisión arquitectónica está fundamentada en literatura educativa revisada por pares:

- **Marco teórico central:** AI-TPACK (extensión de Mishra & Koehler, 2006) — la IA como tercer actor pedagógico, no como reemplazo del componente tecnológico
- **Modelo de feedback:** Hattie & Timperley (2007) + Shute (2008)
- **Autorregulación:** Nicol & Macfarlane-Dick (2006); Zimmerman (2002)
- **Andamiaje:** Cognitive Apprenticeship (Collins, Brown & Newman, 1989) + Guided Inquiry (Kuhlthau et al., 2007) + Vygotsky (1978)
- **Evaluación:** Evidence-Centered Design (Mislevy, Steinberg & Almond, 2003); rúbricas analíticas (Jonsson & Svingby, 2007)
- **Diseño de interacción:** ICAP (Chi & Wylie, 2014)
- **Learning Analytics:** Siemens & Long (2011); Ferguson (2012); Gašević et al. (2015)
- **Tutoría inteligente:** VanLehn (2011)
- **Ecosistemas de aprendizaje:** Brodo (2006); Chang & Güetl (2007); Pata (2011); Gómez Valderrama
- **Alfabetización académica latinoamericana:** Carlino (2013); Kamler & Thomson (2014); Moreno et al. (2024)

Documentación completa en [theoretical-foundations.md](theoretical-foundations.md).

---

## Contribución Esperada

La investigación llena un vacío identificado: **la integración articulada entre pedagogía, herramientas de IA y procesos de acompañamiento investigativo como ecosistema**. Mientras existen estudios sobre cada componente por separado, no se ha documentado ni validado un sistema que los integre bajo un marco teórico coherente (AI-TPACK) en contexto de posgrado, particularmente en Latinoamérica.

---

## Origen y Créditos

Este ecosistema combina y extiende:

- **clo-author** (Hugo Sant'Anna, UAB) — base del pipeline de investigación con worker-critic pairs. Adaptado profundamente para AI-TPACK, redicheñando 18 agentes y agregando 2 nuevos (tutor-pedagogico + tutor-pedagogico-critic)
- **academic-research-skills** (Imbad0202) — referencia para integrity gates y human-in-the-loop philosophy
- **superpowers** (obra) — patrones de systematic-debugging, verification-before-completion y TDD adaptados como `/tools` subcommands para el contexto académico
- **claude-code-templates** — error-detective y canvas-design integrados al modo docente

**Investigador principal y diseño AI-TPACK:** Daniel Eduardo Villalba de Oro, Monica Andrea Mantilla Contreras Politécnico Grancolombiano.

---

## Repositorios

- **Núcleo TPACK:** https://github.com/profedeoro/AI-academicresearchtutorTPACK
- **Documentación de diseño:** Ver `clo-author/quality_reports/specs/` y `clo-author/quality_reports/plans/`

---

## Licencia

CC BY-NC 4.0 — uso académico no comercial. Para licencias comerciales, contactar al investigador principal.

---

> **La IA enseña, el estudiante aprende, el docente supervisa.**
> Si el estudiante no puede explicar lo que produjo, no lo aprendió.
> Si el docente no validó la rúbrica, no es evaluación final.
> Si el feedback no cumple las 5 capas, no es formativo.
