---
tags:
  - devops
  - platzi
  - CI-CD
  - infraestructura
---

# 01 — Introducción a DevOps

---

## 🔄 ¿Qué es DevOps?

DevOps es una **cultura y conjunto de prácticas** que une el desarrollo de software (Dev) con las operaciones de TI (Ops), con el objetivo de acortar el ciclo de vida del desarrollo y entregar software de alta calidad continuamente.

---

## 🏗️ Los 8 Pilares de DevOps (Infinito)

```
Plan → Code → Build → Test → Release → Deploy → Operate → Monitor
  ←←←←←←←←←←← Retroalimentación continua ←←←←←←←←←←←←
```

---

## ⚙️ Herramientas Clave

| Fase | Herramientas |
|---|---|
| **Control de versiones** | Git, GitHub, GitLab |
| **CI/CD** | GitHub Actions, Jenkins, CircleCI |
| **Contenedores** | Docker, Podman |
| **Orquestación** | Kubernetes (K8s) |
| **Infraestructura como código** | Terraform, Ansible |
| **Monitoreo** | Prometheus, Grafana, Datadog |
| **Cloud** | AWS, GCP, Azure |

---

## 🐳 Docker — Comandos Básicos

```bash
docker build -t mi-app .          # construir imagen
docker run -p 3000:3000 mi-app   # correr contenedor
docker ps                         # contenedores activos
docker images                     # imágenes locales
docker stop <id>                  # detener
docker rm <id>                    # eliminar contenedor
docker rmi <imagen>               # eliminar imagen
docker-compose up -d              # docker compose en background
```

---

## 🔄 GitHub Actions — CI/CD Básico

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm install
      - run: npm test
      - run: npm run build
```

---

## 🔗 Siguiente
- [[02 - Redes Informáticas e Internet]]
