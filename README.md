# Fundamentos de DevOps · AIDJR Gen 05 (Clase 11)

Repositorio de práctica para la sesión final de **Fundamentos de DevOps** del bootcamp **AIDJR Gen 05**.

Sitio publicado (CD con GitHub Pages): **https://remr11.github.io/devops-fundamentos-aidjr05/**

---

## ¿Qué contiene este proyecto?

Una aplicación web sencilla (HTML + CSS + JavaScript sin librerías externas) que muestra el ciclo de DevOps en 7 etapas y calcula tu progreso en vivo, acompañada de:

- **Pruebas automáticas** con Node.js nativo (`node:test`).
- **Script de build** (`scripts/build.mjs`) que genera la carpeta estática `dist/`.
- **Pipeline de CI** (`.github/workflows/ci.yml`) que corre pruebas y build en cada `push` y `pull_request` a `main`.
- **Pipeline de CD** (`.github/workflows/deploy-pages.yml`) que despliega `./dist` en **GitHub Pages** cada vez que se actualiza `main`.

## Estructura del repositorio

```text
.
├── .github/workflows/
│   ├── ci.yml                  # Integración continua: npm test + npm run build
│   └── deploy-pages.yml        # Despliegue continuo a GitHub Pages
├── public/                     # Código fuente de la app web
│   ├── index.html
│   ├── styles.css
│   ├── main.js
│   └── logic.js                # Lógica pura (testeable en Node y en navegador)
├── scripts/
│   └── build.mjs               # Copia public/ a dist/ y genera build-info.json
├── test/
│   └── logic.test.js           # Pruebas unitarias con node:test
├── practica/
│   ├── 01-primer-check-ci.md
│   ├── 02-despliegue-pages.md
│   └── 03-variables-y-secretos.md
├── .env.example                # Plantilla segura de variables locales
├── .gitignore                  # Ignora .env, dist/ y node_modules/
└── package.json
```

## Cómo ejecutarlo en tu computadora

Requiere **Node.js 20 o superior** (recomendado Node 24 LTS) y **Git**.

```bash
# 1. Ejecutar las pruebas automáticas
npm test

# 2. Construir la carpeta dist/
npm run build

# 3. (Opcional) Ver el sitio en tu navegador local
npm run preview
```

## Activar GitHub Pages en tu fork

Para que el workflow `.github/workflows/deploy-pages.yml` funcione al hacer fork o crear tu propio repo:

1. Entra a **Settings → Pages** en GitHub.
2. En **Build and deployment → Source**, selecciona **GitHub Actions**.
3. Haz push a `main` o ejecuta el workflow manualmente desde la pestaña **Actions**.

## Ejercicios de la clase

1. [Ejercicio 1 · Ver tu primer check de CI (rojo ❌ y verde ✅)](./practica/01-primer-check-ci.md)
2. [Ejercicio 2 · Publicar tu sitio automáticamente con GitHub Pages (CD)](./practica/02-despliegue-pages.md)
3. [Ejercicio 3 · Variables, `.env` y GitHub Secrets (lo esencial)](./practica/03-variables-y-secretos.md)

## Para investigar después (cuando domines estos fundamentos)

- **Fijar Actions por commit SHA** (en vez de `@v7`, usar el hash de 40 caracteres para evitar ataques a la cadena de suministro).
- **Dependabot** para recibir Pull Requests automáticos cuando tus dependencias tengan actualizaciones o parches de seguridad.
- **Docker** para empaquetar tu app con su entorno y evitar el clásico *"en mi máquina funciona"*.
