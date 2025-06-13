---
title: "Clase Final — Práctica Guiada de Git"
date: 2025-06-12
slug: git/clase-final-practica
summary: "Actividad final para reforzar conceptos clave de Git mediante una práctica colaborativa."
tags: [git, práctica, clase-final, ramas, staging]
---


# 🎓 Clase Final — ¡Nuestra Última Práctica! 🎉

> 💭 **Contexto:** Hoy consolidamos todo lo aprendido clonando el repositorio y sentando las bases del proyecto.

- [x] **Estado:** Repositorio clonado ✅

---

> 🚀 ¡Sigamos con el siguiente paso!


# Fundamentos y Flujo Básico (Mini Repaso) 

### 🔹 Paso 2: Crear tu propia branch y hacer commit

> 🎯 **Objetivo:** Trabajar en tu propia rama sin afectar la rama principal.  
> ✨ **Tip:** Usa un nombre descriptivo (por ejemplo, tu nombre o matrícula).

#### 📋 Tareas:
- [x] Crear una nueva rama:
```bash
git checkout -b nombre_del_alumno
```
- [x] Realizar cambios en el proyecto.
- [x] Agregar los cambios al área de staging:
```bash
git add .
```
- [ ] Registrar los cambios:
```bash
git commit -m "Iniciando práctica en branch nombre_del_alumno"
```

---

### 📁 Paso 3: Crear carpetas y archivos base

> 🗂️ Estructura mínima del proyecto

- [x] Crear una carpeta `js/`
- [x] Crea el archivo `js/index.js` y index.html
```bash
mkdir js html
cd js && touch index.js
touch index.html
```

---

### 🧠 Paso 4: Agrega tus archivos

> 📦 Deja listos tus archivos para el commit

- [ ] Agregar todos los archivos nuevos:
```bash
git add .
```

### 🔒 Paso 5: Crear un archivo ignorado

> 🕶️ Buenas prácticas: evitar subir archivos innecesarios

- [ ] Crear un archivo llamado `ignorame.txt`:
```bash
touch ignorame.txt
```
- [ ] Agregarlo a `.gitignore`:
```bash
echo ignorame.txt >> .gitignore
```
- [ ] Confirmar que no se añade a staging:
```bash
git status  # asegúrate de que ignorame.txt no aparece como archivo a commitear
```
### 🔒 Paso 5: Crear un archivo ignorado

> 🕶️ Buenas prácticas: evitar subir archivos innecesarios

- [ ] Crear un archivo llamado `ignorame.txt`:
```bash
touch ignorame.txt
```
- [ ] Agregarlo a `.gitignore`:
```bash
echo (.ignorame.txt  o ignorame.txt)? >> .gitignore
```
- [ ] Confirmar que no se añade a staging:
```bash
git status  # asegúrate de que ignorame.txt no aparece como archivo a commitear
```
<br>
<br>
<br>


# "Git — Configuración Avanzada y Atajos"

## 🧩 Paso 1: Definir Aliases
> ✨ Los *aliases* te permiten escribir comandos más cortos sin perder funcionalidad.

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

✅ Ahora puedes usar:
```bash
git co main      # en lugar de git checkout main
git ci -m "msg"   # en lugar de git commit -m "msg"
```

---

## 🎨 Paso 2: Personalizar colores y editor por defecto

### 🔧 Colores
Activa colores para una mejor lectura:
```bash
git config --global color.ui auto
```

### 📝 Editor por defecto (ej. VS Code)
```bash
git config --global core.editor "code --wait"
```
O con Neovim:
```bash
git config --global core.editor "nvim"
```

---

## 🚀 Paso 3: Atajos útiles

| Comando | Descripción |
|---------|-------------|
| `git shortlog` | Muestra resumen de commits por autor. Ideal para ver contribuciones. |
| `git describe` | Muestra el último tag alcanzable desde HEAD. Útil para versiones. |
| `git diff --staged` | Muestra diferencias de lo que se ha agregado al staging. |

### Ejemplos:
```bash
git shortlog -sn
#   42  Alan Renteria
#    8  Otro Alumno

# Último tag:
git describe --tags

# Ver cambios ya añadidos al staging:
git diff --staged
```

---



# 🌿 Git — Gestión de Ramas

> 🌱 Domina la creación, uso y fusión de ramas con buenas prácticas para proyectos reales.

## 🎯 Objetivo

Comprender cómo utilizar ramas para mantener el código organizado y facilitar el trabajo colaborativo.

---

## 🧭 Estrategias de Ramas

En proyectos colaborativos, es común usar diferentes tipos de ramas para organizar el trabajo:

| Tipo de Rama | Propósito |
|--------------|-----------|
| `feature/`   | Desarrollo de nuevas funcionalidades |
| `hotfix/`    | Correcciones urgentes en producción |
| `release/`   | Preparación de una nueva versión estable |

### Ejemplos:
```bash
git checkout -b feature/nueva-navbar

git checkout -b hotfix/arreglo-login

git checkout -b release/v1.0.0
```

---

## 🔄 Flujo de Trabajo con Ramas

### 📌 Crear una rama nueva
```bash
git checkout -b feature/nombre-del-feature
```

### 🔄 Cambiar entre ramas
```bash
git checkout main
```

### 🔀 Fusionar una rama al main
> Asegúrate de estar en `main` antes de fusionar:
```bash
git checkout main
git merge feature/nombre-del-feature
```

✅ ¡Ahora el código de tu rama está integrado!

---

## 💡 Buenas Prácticas

- Nombra las ramas con prefijos claros: `feature/`, `hotfix/`, `release/`
- Realiza `pull` regularmente para mantener tu rama actualizada
- Usa `pull request` (en plataformas como GitHub) para revisar antes de fusionar

---


# 🧬 Git — Merge vs. Rebase Profundo

> 🔀 Aprende las diferencias clave entre `git merge` y `git rebase`, cuándo usarlos y cómo aplicarlos correctamente en equipo.

## 🎯 Objetivo

Dominar los dos enfoques principales para integrar ramas en Git: `merge` y `rebase`.

---

## 🔁 ¿Cuándo usar `git merge`?

> ✅ **Seguro para equipos y mantiene el historial completo.**

### ✔️ Ventajas:
- Mantiene el historial de ramas
- Fácil de entender en colaboración
- Recomendado para `main`, `release` y trabajo compartido

### 📌 Comando:
```bash
git checkout main
git merge feature/login
```

---

## 🧼 ¿Cuándo usar `git rebase`?

> 🧪 **Ideal para un historial lineal y limpio, pero requiere cuidado.**

### ✔️ Ventajas:
- Historial más limpio
- Facilita `git log` y `blame`

### ⚠️ Peligros:
- **Nunca rebasees ramas que ya se compartieron**
- Puede sobrescribir commits si no se usa correctamente

### 📌 Comando:
```bash
git checkout feature/login
git rebase main
```

---

## 🧪 Ejercicios prácticos

### 🧩 Ejercicio 1: `merge`
```bash
git checkout -b feature/ejemplo-merge
# haz cambios y commit

git checkout main
git merge feature/ejemplo-merge
```

### 🧩 Ejercicio 2: `rebase`
```bash
git checkout -b feature/ejemplo-rebase
# haz cambios y commit

git checkout main
git pull
git checkout feature/ejemplo-rebase
git rebase main
```

---

## 💡 Recomendaciones para equipos

- Usa `merge` en ramas públicas y compartidas.
- Usa `rebase` sólo en ramas locales antes de hacer push.
- Antes de rebasear, guarda tu trabajo (`stash`, commits).


# 🧭 Git — Navegación entre Commits y Ramas

> ✨ En Git, los *commits* son como puntos en el tiempo, y las ramas son caminos que nos permiten avanzar, retroceder y explorar.

## 📌 ¿Por qué navegar?

- Para ver qué cambió en un punto específico.
- Para recuperar una versión anterior.
- Para experimentar sin afectar el trabajo actual.

---

## 🔍 Ver el historial (el mapa del camino)

```bash
git log --oneline
```
```bash
git log --oneline --graph --decorate --all
```

```bash
git config --global alias.historia "!git --no-pager log --oneline --graph --decorate --all"
```

🧠 Esto te muestra los *hashes* (IDs únicos) de cada commit, que usarás para moverte.

---

## 🧭 Navegar con `checkout`

### 🔹 Cambiar de rama:
```bash
git checkout main
```
```bash
git checkout nombre-de-tu-rama
```

### 🔹 Ver el proyecto en un commit anterior (modo lectura):
```bash
git checkout <hash>
```
⚠️ Estás en estado `detached HEAD`. No hagas commits aquí a menos que sepas lo que haces.

### 🔹 Volver a tu rama:
```bash
git checkout alan
```

---

## 🕶️ Explorar sin alterar: `git show`

Ver detalles de un commit sin moverse:
```bash
git show <hash>
```
También puedes usar:
```bash
git diff <hash1> <hash2>
```
Para ver qué cambió entre dos commits.

---

## 🔂 Volver al pasado con `reset`

### 🔸 Mover HEAD a un commit anterior (deshace commits):
```bash
git reset --hard <hash>
```
⚠️ Cuidado: elimina cambios si usas `--hard`.

Alternativa segura:
```bash
git reset --soft <hash>   # conserva tus cambios en staging
```

---

## 🧰 Volver con seguridad: `reflog`

```bash
git reflog
```
Te muestra a dónde has estado, incluso si ya hiciste reset o rebase.

Luego puedes volver con:
```bash
git checkout <hash>
```
O crear una rama desde ahí:
```bash
git branch rescate <hash>
```

---

## 🧪 Otros comandos útiles

### 🔹 Ver ramas:
```bash
git branch
```
```bash
git branch -a  # incluye remotas
```

### 🔹 Ver desde qué commit parte una rama:
```bash
git merge-base main alan
```



# 🕰️ Git — Reescritura y Recuperación de Historial

> 🔧 Domina la edición del historial de commits y las herramientas para recuperarte de errores serios.

## 🎯 Objetivo

Aprender a mantener un historial limpio y saber cómo deshacer o recuperar cambios en casos críticos.

---

## 🧼 Reescritura de Historial con `squash` y `rebase -i`

### ✨ `git rebase -i` (interactivo)
Permite reorganizar, editar o combinar commits recientes:
```bash
git rebase -i HEAD~3
```
- Cambia `pick` por `squash` para combinar commits.
- Cambia el mensaje de commit si es necesario.

✅ Ideal antes de hacer push por primera vez para dejar el historial limpio.

---

## 🧹 Deshacer Cambios: reset, revert, restore

| Comando | ¿Qué hace? | Cuándo usarlo |
|--------|------------|---------------|
| `git reset` | Mueve la rama actual al commit indicado (puede borrar cambios). | Para deshacer commits locales. |
| `git revert` | Crea un nuevo commit que deshace otro commit anterior. | Para deshacer cambios ya publicados. |
| `git restore` | Descarta cambios en archivos del working directory. | Para deshacer archivos modificados sin afectar el historial. |

Ejemplo para deshacer staging:
```bash
git restore --staged archivo.js
```

---

## 🔍 Recuperación Avanzada

### 🔄 `git reflog`: tu historial secreto

```bash
git reflog
```
Muestra todos los movimientos recientes de HEAD, incluso los que ya no aparecen en `git log`.

➡️ Usa `reflog` para encontrar el hash de un estado anterior y recuperarlo:
```bash
git checkout <hash>
```

### 🧩 `git bisect`: encuentra el commit del bug

```bash
git bisect start
```
```bash
git bisect bad      # commit actual tiene el bug
```
```bash
git bisect good <hash>
```
Git hace una búsqueda binaria hasta hallar el commit problemático. Finaliza con:
```bash
git bisect reset
```

---

## 💡 Consejos Finales

- No uses `rebase -i` en commits compartidos
- Combina `reset` + `reflog` para recuperar errores
- Haz squash antes de mergear tu rama a `main`




- [ ] **Colaboración y automatización**
  - [ ] Git Hooks básicos (pre-commit, commit-msg) y herramientas (Husky, lint-staged)
  - [ ] Introducción a GitHub Actions para CI/CD



  git added new feature
