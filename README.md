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

## 🚀 ¡Sigamos con el siguiente paso!

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

---

## ✅ Fundamentos y Flujo Básico (Mini Repaso)

- [ ] Revisión del flujo: `staging → commit → push`
- [ ] Uso correcto de `.gitignore` y archivos de configuración
- [ ] Mini ejercicio:
    - Crear nuevo repo local
    - Crear archivo
    - Hacer `git add` + `commit`



- [ ] **Fundamentos y flujo básico**
  - [ ] Repaso rápido de staging → commit → push
  - [ ] Uso de `.gitignore` y archivos de configuración
  - [ ] Mini-ejercicio guiado: crear un repo y tu primer commit

- [ ] **Configuración avanzada y atajos**
  - [ ] Definir aliases (`git config --global alias.co checkout`, etc.)
  - [ ] Personalizar colores y editor por defecto
  - [ ] Atajos útiles: `git shortlog`, `git describe`, `git diff --staged`

- [ ] **Gestión de ramas**
  - [ ] Estrategias: ramas _feature_, _hotfix_ y _release_
  - [ ] Demostración de flujo con ramas: crear, cambiar, fusionar

- [ ] **Merge vs. rebase profundo (20 min)**
  - [ ] ¿Cuándo usar `git merge` y cuándo `git rebase`?
  - [ ] Ventajas y peligros de rebase en equipo
  - [ ] Ejercicios prácticos de ambos

- [ ] **Reescritura y recuperación de historial (30 min)**
  - [ ] `git squash` y `git rebase -i` para historial limpio
  - [ ] Deshacer cambios: `reset`, `revert`, `checkout`/`restore`
  - [ ] Recuperación avanzada: `git reflog` y `git bisect`

- [ ] **Colaboración y automatización (30 min)**
  - [ ] Comparativa de flujos: GitHub Flow, Git Flow, Trunk-based
  - [ ] Buenas prácticas de Pull Requests: nombres de ramas, descripciones, revisiones
  - [ ] Git Hooks básicos (pre-commit, commit-msg) y herramientas (Husky, lint-staged)
  - [ ] Introducción a GitHub Actions para CI/CD