---
title: "Cómo Deshacer, Recuperar y Depurar en Git"
date: 2025-06-12
slug: git/deshacer-reflog-bisect
summary: "Una guía práctica para manejar errores y encontrar bugs con Git."
tags: [git, debugging, reflog, bisect, reset, revert]
---

# 🧰 Guía Git — Deshacer, Recuperar y Depurar

> Aprende a dominar `reset`, `revert`, `reflog` y `bisect` como un pro 🧠

## 📌 Tabla de Contenidos
- [🧼 Cómo deshacer correctamente](#-cómo-deshacer-correctamente)
- [🕵️‍♂️ git reflog: el héroe oculto](#-git-reflog-el-héroe-oculto)
- [🧩 Debugging con bisect](#-debugging-con-bisect)

---

## 🧼 Cómo deshacer correctamente

| Comando         | Descripción breve | Cuándo usarlo |
|----------------|-------------------|------------------|
| `git reset`    | Mueve la rama a otro commit. Puede borrar historial con `--hard`. | Para reescribir historial local (⚠️ no si ya hiciste push). |
| `git revert`   | Crea un nuevo commit que deshace los cambios de otro. | Para deshacer cambios **sin borrar historial**. Ideal en equipo. |
| `git checkout` | Cambia de rama o revisa otro commit (antes se usaba para restaurar archivos). | Para explorar ramas o commits antiguos. |
| `git restore`  | Restaura archivos del árbol de trabajo o staging. | Para **descartar cambios** sin afectar historial. |

**💡 Tip:**
```bash
git restore --staged archivo.js  # Quita de staging sin perder cambios
```

---

## 🕵️‍♂️ git reflog: el héroe oculto

`git reflog` guarda un historial interno de todo lo que hiciste con tus ramas, incluso lo que `git log` no muestra.

```bash
git reflog  # Ver todos los HEAD anteriores
```

### 🔄 Recuperar un commit perdido
1. Ejecuta `git reflog`.
2. Copia el hash del estado que quieres recuperar.
3. Haz checkout o crea una nueva rama desde ahí:
```bash
git checkout <hash>
# o
git branch recuperado <hash>
```

---

## 🧩 Debugging con bisect

Ideal para encontrar **el commit que introdujo un bug**.

### 🧪 Pasos:
```bash
git bisect start
```
```bash
git bisect bad          # El commit actual tiene el bug
```
```bash
git bisect good <hash> # Este commit sí funcionaba
```

Git seleccionará un commit intermedio. Tú lo pruebas y le dices:
```bash
git bisect good  # si no hay bug
# o
git bisect bad   # si el bug sigue
```

🔍 Git hará una búsqueda binaria para encontrar el commit exacto donde se introdujo el problema.

Cuando termines:
```bash
git bisect reset
```


prueba