# Chuleta del Taller de GitHub — 1 página (para alumnos y profesor)

Imprímela, ancladla en el segundo monitor, ponedla en la nevera. Es todo lo que hace falta
el 90 % del tiempo.

## El mapa (memoriza esto; lo demás se busca)

```
 TUS ARCHIVOS       EL CARRITO        TU HISTORIAL          GITHUB
 (working dir) --git add--> (staging) --git commit--> (repo local .git) --git push--> (origin)
      ^                                                               |
      +------------------------- git pull (trae y mezcla) ---------------------------+
```

- **Git** = versionado en TU máquina (funciona sin internet). **GitHub** = servidor + colaboración.
- **clone** = copia un repo remoto a tu ordenador. **fork** = copia un repo a TU cuenta de GitHub.
  **rama** = línea de trabajo paralela dentro del mismo repo.

## Git Bash: supervivencia

| Quiero... | Comando |
|---|---|
| Saber dónde estoy | `pwd` |
| Ver archivos (ocultos incluidos) | `ls` / `ls -la` |
| Entrar / subir / ir a casa | `cd carpeta` / `cd ..` / `cd ~` |
| Crear carpeta / archivo | `mkdir nombre` / `touch archivo.txt` |
| Ver / escribir en un archivo | `cat archivo` / `echo "x" >> archivo` |
| Abrir carpeta en explorador | `start .` (Win) · `open .` (Mac) · `xdg-open .` (Linux) |
| Abrir en VS Code | `code .` |
| Pegar / autocompletar / historial | clic derecho (Shift+Insert) / Tab / flecha ↑ |
| Limpiar pantalla / salir de un lío | `clear` / `Ctrl + C` |

## El ciclo del día (el 90 % de tu vida)

```bash
git switch main && git pull            # 1. SIEMPRE empezar al día
git switch -c feature/mi-cosa          # 2. rama con nombre con sentido
# ... editas ...  git status ... git add ... 
git commit -m "tipo/que_hice"          # 3. pequeño y con mensaje útil
git push -u origin feature/mi-cosa     # 4. primera vez (después, solo git push)
# 5. Web: Compare & pull request -> descripción -> reviewer
# 6. Te comentan -> corriges con NUEVO commit + push (el PR se actualiza SOLO)
# 7. Approve -> Squash merge -> Delete branch
git switch main && git pull            # 8. volver al presente
```

Mensajes de commit (convención bootcamp): `add/` `fix/` `update/` `delete/` `refactor/` `docs/`
`style/` `test/` + qué tocaste. Errores a evitar: `fix/bug` (¿qué bug?), `update` (¿qué?),
`fix/fix_bug` (repetido). El mensaje debe entenderse dentro de 6 meses.

## Comandos de supervivencia

| Quiero... | Comando |
|---|---|
| Ver estado (mi espejo cada 5 min) | `git status` (versión corta: `git status -s`) |
| Ver historial compacto / cambios | `git log --oneline` / `git diff` |
| Ver mis ramas (la * = dónde estoy) | `git branch -a` |
| Ver las ramas remotas que conoce Git | `git branch -r` (`origin/main` = foto del servidor) |
| Ver / renombrar / quitar remotos | `git remote -v` / `git remote rename a b` / `git remote rm a` |
| Crear y cambiar de rama / cambiar | `git switch -c x` / `git switch x` |
| Fusionar la rama x en la que estoy | `git merge x` |
| Borrar rama local / remota | `git branch -d x` / `git push origin --delete x` |
| Meter TODO al carrito / solo un archivo | `git add .` (o `-A` todo el repo) / `git add archivo` |
| Sacar del carrito (sin perder cambios) | `git restore --staged archivo` |
| Descartar cambios sin commitear | `git restore archivo` |
| Dejar de vigilar un archivo (sin borrarlo) | `git rm --cached archivo` |
| Deshacer último commit LOCAL (guarda cambios) | `git reset HEAD~1` (o `HEAD^`, `HEAD~2`, `<hash>`; modos `--soft`/`--mixed`/`--hard`) |
| Deshacer commit YA PUSHEADO (en equipo) | `git revert <hash>` |
| Corregir el último mensaje de commit | `git commit --amend -m "nuevo"` |
| Visitar una foto antigua / volver | `git checkout <hash>` / `git switch -` |
| Bolsillo de cambios a medias | `git stash` ... `git stash pop` |
| Espiar el remoto sin mezclar | `git fetch` |
| Máquina del tiempo de emergencia | `git reflog` |
| Cancelar un merge en curso | `git merge --abort` |

**reset vs revert:** sin pushear → `reset`. Ya compartido → `revert`. `rebase` = tema avanzado,
hoy no se toca. `reset --hard` borra trabajo de verdad: piénsalo dos veces.

## Conflicto de merge: el ritual (no hay más)

```
<<<<<<< HEAD      <- lo que hay en la rama donde estás
versión A
=======
versión B
>>>>>>> otra-rama <- lo que trae la rama que fusionas
```

1. Abre el archivo y DECIDE (una versión, la otra, o mezcla). **Borra las 3 líneas de marcadores.**
2. `git add archivo` → 3. `git commit` → 4. `git push` (el PR se pone verde solo).

En VS Code/GitLens: botones *Accept Current / Incoming / Both*. En la web: botón
*Resolve conflicts*. Rendirse a mitad: `git merge --abort`.

## Los 3 rechazos que verás

- `! [rejected] ... (fetch first)` → hay trabajo nuevo que no has visto: `git pull` y otra vez `push`.
- `GH006: Protected branch update failed` → main está protegida: se entra por rama + PR. Es la ley del equipo.
- `403 / not allowed` → sin permisos: invitación de collaborator sin aceptar (campanita) o repo ajeno (fork + PR).

## Entorno Python con uv (la receta viaja, la cocina no)

```bash
uv venv --python 3.12                # 1. crear la burbuja (.venv)
source .venv/Scripts/activate        # 2. activar (Windows/Git Bash) · Mac/Linux: .venv/bin/activate
uv pip install pandas matplotlib     # 3. instalar DENTRO de la burbuja
uv pip freeze > requirements.txt     # 4. guardar LA RECETA (esto SÍ va a Git)
deactivate                           # salir

# Clonar el repo de otro y levantar su entorno exacto:
git clone <repo> && cd <repo>
uv venv --python 3.12 && source .venv/Scripts/activate
uv pip install -r requirements.txt
```

`.venv/` NUNCA se sube (va en `.gitignore`). Si se coló: `git rm -r --cached .venv` + commit.
Datos (`data/`, `*.csv`), secretos (`.env`) y outputs gigantes: fuera del repo. Clave colada = clave ROTADA.

## Reglas de oro (versión bolsillo)

1. `git pull` antes de empezar y antes de cada push.
2. Nunca trabajar en main. Main protegida desde el día 1.
3. Commits pequeños: `tipo/que-toque`.
4. Lee tu propio diff antes de abrir el PR.
5. Datos, secretos y `.venv`: `.gitignore`.
6. Un PR = una idea; es una conversación viva, no una foto.
7. Conflicto = Git protegiendo el trabajo ajeno. Ritual de 4 pasos.
8. Sin pushear → `reset`; ya pusheado → `revert`; nunca `push --force` en ramas compartidas.
9. `git status` y `git reflog`: casi nada se pierde de verdad.
10. 5 min atascado = preguntar (captura + comando + error).

## Forks (si contribuyes a un repo sin permisos)

```bash
git remote add upstream <url-del-original>   # además de origin (tu fork)
git pull upstream main                       # trae lo nuevo del ORIGINAL
git push origin main                         # y actualiza TU fork
# (o en la web: botón "Sync fork")
```

## Dónde buscar

- `git help <comando>` · Chuleta oficial: https://training.github.com/downloads/github-git-cheat-sheet/
- Buscador "quiero hacer X": https://gitexplorer.com
- Simulador visual de ramas (¡en español!): https://learngitbranching.js.org/?locale=es_ES
- Recetario de pifias: https://ohshitgit.com (en inglés, con alma)
- Libro completo en español: https://git-scm.com/book/es/v2
- **Cómo buscar un error de Git**: copia la PRIMERA línea del error (`error:`/`fatal:`) y
  búscala en Google entre comillas + "git". Si el arreglo lleva `--force` o `--hard`: pregunta antes.
- Todo esto y más, organizado por situaciones: `recursos.md`
- Y cuando todo falle: `git status` + respirar.
