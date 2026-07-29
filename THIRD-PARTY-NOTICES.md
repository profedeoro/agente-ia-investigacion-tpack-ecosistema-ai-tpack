# Avisos de terceros

Este proyecto se publica bajo **Creative Commons Attribution-NonCommercial 4.0
International (CC BY-NC 4.0)** — ver [`LICENSE`](LICENSE). Esa licencia cubre
**únicamente el contenido original de este repositorio** (documentación,
especificaciones, agentes y skills desarrollados para el proyecto).

El proyecto incorpora, además, componentes de terceros distribuidos bajo sus
**propias licencias**, que **no son relicenciados** por la elección de CC
BY-NC 4.0. Se listan a continuación con su origen y su licencia:

## Submódulos

| Componente | Ruta | Origen | Licencia |
|---|---|---|---|
| **clo-author** | `clo-author/` (submódulo git) | [profedeoro/AI-academicresearchtutorTPACK](https://github.com/profedeoro/AI-academicresearchtutorTPACK) | Plantilla base (upstream) bajo **MIT License**, según su propio README ("MIT License. Fork it, customize it, make it yours."). Las personalizaciones específicas de este proyecto dentro del submódulo heredan la licencia declarada en ese repositorio. |
| **academic-research-skills** | `.claude/skills/academic-research-skills/` (submódulo git) | [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | Proyecto de terceros con **licencia propia** (archivo `LICENSE` en el repositorio de origen). No se redistribuye aquí bajo CC BY-NC 4.0; se referencia como submódulo bajo los términos que ese repositorio defina. |

## Skills incluidas directamente en este repositorio

| Componente | Ruta | Licencia |
|---|---|---|
| **rag-engineer** | `.claude/skills/rag-engineer/` | **Apache License 2.0**. Adaptado de `vibeship-spawner-skills`, según se indica en el frontmatter de su `SKILL.md` (`source: vibeship-spawner-skills (Apache 2.0)`). |
| **skill-creator** | `.claude/skills/skill-creator/` | **Apache License 2.0**, según su archivo `LICENSE.txt` incluido en esa carpeta. |
| **canvas-design** | Incluida como skill dentro del submódulo `clo-author/` (no reside en el `.claude/skills/` de este repositorio raíz) | Distribuida con su propio archivo de licencia dentro del repositorio de origen del submódulo. Se documenta aquí por completitud, ya que el ecosistema descrito en `README.md` y `architecture.md` la referencia como componente del proyecto. |

**Nota sobre `research-engineer`:** la skill `.claude/skills/research-engineer/`
no declara una licencia propia distinta en este repositorio; a falta de aviso
explícito, se trata como contenido original del proyecto y queda cubierto por
`LICENSE` (CC BY-NC 4.0).

## Resumen

- **CC BY-NC 4.0** aplica solo a las contribuciones originales de este
  proyecto (documentación de investigación, especificaciones, agentes y
  skills sin licencia propia declarada).
- Cada componente de terceros listado arriba conserva su licencia original.
  Antes de reutilizar, redistribuir o modificar cualquiera de estos
  componentes fuera de este proyecto, consultar la licencia del repositorio
  de origen correspondiente.
- Los submódulos (`clo-author`, `academic-research-skills`) no se clonan por
  defecto en un checkout superficial (`git clone --no-recurse-submodules`);
  su código y su licencia solo están disponibles al inicializarlos
  (`git submodule update --init`).
