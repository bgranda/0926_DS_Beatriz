# Repo de clase — Taller de GitHub (promo 0926)

Este es el repositorio de práctica de la actividad **"Trabajo en equipo: tres rondas"**.
Aquí no se rompe nada de verdad: es un campo de entrenamiento. Todos sois colaboradores
(collaborators) de este repo.

## Reglas del juego

1. **Nadie trabaja directamente en `main`** salvo que el ejercicio lo diga expresamente (ronda 3).
2. Todo cambio entra por **rama + Pull Request**. A partir de la ronda 3, `main` estará protegida
   y el propio servidor lo obligará.
3. Cada PR lo revisa **otra persona** antes de fusionarse.
4. Tu rama de la ronda 1 se llama **`alumno/<tu-nombre>`**. Después, nombre con sentido
   (`feature/...`, `docs/...`, `fix/...`).
5. Si llevas **5 minutos atascado**: levanta la mano 

## Estructura del repo

```
.
├── README.md          <- este archivo (reglas del juego)
├── lema.md            <- el lema oficial de la promo (se edita en la ronda 2)
├── normas.md          <- normas del equipo
├── ranking.md         <- puntuación de "La Carrera de PRs" (la lleva el profe)
├── miembros/          <- una ficha por persona (ronda 1)
└── .github/           <- plantilla de PR (se rellena sola al abrir tu PR)
```

## Cómo añadir tu ficha (ronda 1)

1. Crea tu rama: `git switch -c alumno/<tu-nombre>`
2. Crea el archivo `miembros/<tu-nombre>.md` con este contenido:

```markdown
# Nombre y apellidos

- Usuario GitHub: @...
- Superpoder DS: (lo que mejor se te da: limpiar datos, visualizar, SQL, preguntar...)
- Meta del trimestre: ...
- Norma que propondría para el equipo: ...
```

3. `git add miembros/<tu-nombre>.md` → `git commit -m "add/ficha_<tu-nombre>"` →
   `git push -u origin alumno/<tu-nombre>`
4. Abre el PR en la web, pide revisión a tu pareja y, cuando te apruebe, **Squash merge**.

**Importante:** en la ronda 1 solo toques TU archivo. Por eso no hay conflictos: cada uno
trabaja en lo suyo. Eso, en un equipo real, evita el 80 % de los problemas.

## La Carrera de PRs (competición del día)

- **+1 punto** por cada PR fusionado correctamente.
- **+2 puntos extra** a los 3 primeros PRs fusionados de la ronda 1 (limpios y sin ayuda).
- **+1 punto** si tu pareja te aprueba el PR sin pedirte ningún cambio (diff limpio).
- **+3 puntos** a la dupla de la ronda 2 que resuelva el conflicto con el ritual completo.

## Créditos

Ejercicio adaptado de dinámicas de colaboración usadas en bootcamps de Data Science
(UC Davis STA 199, Salesforce Trailhead "Git and GitHub Basics", NCEAS, GitHub Skills)
y del taller de ramas de Alejandro Reyes para The Bridge Full Stack.
