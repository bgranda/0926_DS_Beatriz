# Recursos y enlaces — "Cuando el profe no está"

Todos gratuitos. Ordenados por la situación en la que los vas a usar. Los 3 primeros son
los que más usaréis el primer mes: **gitexplorer, ohshitgit y Pro Git en español**.

## Según lo que te esté pasando

| Situación | Enlace |
|---|---|
| "Quiero hacer X, ¿qué comando es?" | [gitexplorer.com](https://gitexplorer.com/) — buscas por lo que quieres conseguir y te dice el comando |
| "La he pifiado, ¿cómo lo arreglo?" | [ohshitgit.com](https://ohshitgit.com/) (recetario de pifias→arreglo) y el cap. 3.4 de [Pro Git en español](https://git-scm.com/book/es/v2) |
| "¿Qué significa este error?" | Empieza por [docs.github.com → About merge conflicts](https://docs.github.com/articles/about-merge-conflicts); y el buscador de issues de github.com (el 90 % de los errores ya están preguntados ahí) |
| "Quiero practicar ramas sin riesgo" | [learngitbranching.js.org en español](https://learngitbranching.js.org/?locale=es_ES) — simulador visual con niveles |
| "Quiero un curso paso a paso" | [GitHub Skills](https://skills.github.com/) — cursos oficiales que crean repos de práctica reales (Hello World, Branching, Merge conflicts, Fork & PR...) |
| "Quiero entender un concepto a fondo" | [Pro Git en español](https://git-scm.com/book/es/v2): cap. 1 (qué es Git), 2 (fundamentos), 3 (ramas), 7.3–7.4 (rebase, reset) |
| "Necesito la chuleta oficial en PDF" | [github-git-cheat-sheet](https://training.github.com/downloads/github-git-cheat-sheet/) |
| "Voy a abrir mi primer PR en un proyecto real" | [freeCodeCamp: cómo hacer tu primer Pull Request](https://www.freecodecamp.org/news/how-to-make-your-first-pull-request-on-github-3/) y [docs.github → Syncing a fork](https://docs.github.com/articles/syncing-a-fork) |
| "Busco mi primer proyecto open source" | [goodfirstissue.dev](https://goodfirstissue.dev/) y [firsttimersonly.com](https://www.firsttimersonly.com/) |

## Micro-habilidad que vale oro: cómo buscar un error de Git

Nadie os enseña esto y os ahorrará horas:

1. Copia **solo la primera línea** del error (la que empieza por `error:`, `fatal:` o `remote:`).
2. Búscala en Google **entre comillas** + la palabra `git`. Ejemplo:
   `"fatal: refusing to merge unrelated histories" git`
3. Mira los 3 primeros resultados: Stack Overflow, GitHub Community o docs.github.com.
4. Antes de ejecutar NINGÚN comando copiado de internet: comprueba que habla de TU versión de
   Git y que no incluye `--force` ni `reset --hard` sin que sepas qué hacen.
   Regla: si no entiendes el arreglo, pregunta primero.

## Lecturas avanzadas (para después del taller)

- **git-flow y la rama `develop`**: [A successful Git branching model (nvie.com)](https://nvie.com/posts/a-successful-git-branching-model/).
  Es EL artículo que popularizó usar `develop` + `main`. En el bootcamp usamos el flujo simple
  (solo `main` + ramas + PR); este es para cuando un proyecto os lo pida.
- **Conventional Commits**: [conventionalcommits.org](https://www.conventionalcommits.org/es/v1.0.0/)
  — evolución de nuestra convención `add/fix/docs` al estándar de la industria (`feat:`, `fix:`...).
- **Rebase explicado bien**: cap. 3.6 y 7.4 de Pro Git (en español). Recordad la regla del
  taller: rebase NO en ramas compartidas.
- **Git LFS** (datos grandes versionados): [git-lfs.com](https://git-lfs.com/).

## Los 3 tipos de "copia" (resumen definitivo)

| | ¿Dónde vive? | ¿Historial? | ¿Cuándo se usa? |
|---|---|---|---|
| **clone** | En tu ordenador | Completo | Tienes permisos en el repo |
| **fork** | En tu cuenta de GitHub | Completo | NO tienes permisos (contribuir) |
| **ZIP** | En tu ordenador | NINGUNO | Nunca. No lo uses |
