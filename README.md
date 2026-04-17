# 🚀 My Portfolio

> Un portfolio web moderno y responsivo construido con **Astro**, que muestra mis proyectos, habilidades y experiencia como desarrollador Frontend.

[![Astro](https://img.shields.io/badge/Astro-6.1.7-purple?style=flat-square&logo=astro)](https://astro.build)
[![Node.js](https://img.shields.io/badge/Node.js-v22.12.0+-green?style=flat-square&logo=node.js)](https://nodejs.org)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

---

## 📋 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Características](#características)
- [Tecnologías](#tecnologías)
- [Requisitos Previos](#requisitos-previos)
- [Instalación](#instalación)
- [Scripts Disponibles](#scripts-disponibles)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Guía de Desarrollo](#guía-de-desarrollo)
- [Proyectos Destacados](#proyectos-destacados)
- [Deployment](#deployment)
- [Aprendizajes y Recursos](#aprendizajes-y-recursos)
- [Contribución](#contribución)
- [Licencia](#licencia)

---

## 📝 Descripción General

Este es mi portfolio personal construido como parte del curso **"JavaScript para Frontend"** de Platzi. Es una aplicación web estática y optimizada que sirve como vitrina de mis proyectos, habilidades técnicas y experiencia como desarrollador.

El sitio está construido con **Astro**, un framework moderno que permite crear sitios web extremadamente rápidos con generación de contenido estático.

---

## ✨ Características

- 🎨 **Diseño Moderno y Responsivo**: Interfaz atractiva que se adapta a cualquier dispositivo
- ⚡ **Rendimiento Optimizado**: Generado como contenido estático para carga ultrarrápida
- 🌙 **Tema Oscuro/Claro**: Toggle para cambiar entre temas según preferencia del usuario
- 📱 **Mobile First**: Optimizado primero para dispositivos móviles
- 🎯 **SEO Optimizado**: Metadatos y estructura adecuada para motores de búsqueda
- 📄 **Contenido Dinámico**: Proyectos gestionados como markdown para fácil mantenimiento
- ♿ **Accesibilidad**: Cumplimiento con estándares WCAG
- 🚀 **Despliegue Rápido**: Lista para deployment en múltiples plataformas

---

## 🛠️ Tecnologías

### Framework Principal

- **[Astro 6.1.7](https://astro.build/)** - Framework para crear sitios web ultrarrápidos

### Lenguajes

- **TypeScript** - Tipado estático y mejor DX
- **JavaScript (ES6+)** - Lógica del cliente
- **Markdown** - Para contenido de proyectos

### Estilos

- **CSS3** - Estilos personalizados
- **Responsive Design** - Mobile-first approach

### Herramientas de Desarrollo

- **Prettier** - Formateador de código automático
- **prettier-plugin-astro** - Plugin de Prettier para archivos Astro

### Requisitos de Entorno

- **Node.js** >= 22.12.0
- **npm** o **yarn** para gestor de paquetes

---

## 📦 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

- **Node.js** versión 22.12.0 o superior ([Descargar](https://nodejs.org))
- **npm** (incluido con Node.js) o **yarn**

Verifica la instalación:

```bash
node --version  # v22.12.0+
npm --version   # 10.0.0+
```

---

## 🚀 Instalación

### 1. Clonar o Descargar el Repositorio

```bash
# Si tienes acceso al repositorio
git clone https://github.com/tu-usuario/mi-portfolio.git
cd my-website
```

### 2. Instalar Dependencias

```bash
npm install
```

Esto instalará:

- `astro` - Framework principal
- `prettier` - Herramienta de formateo de código
- `prettier-plugin-astro` - Plugin para Astro

### 3. Verificar la Instalación

```bash
npm run astro -- --version
```

---

## 📜 Scripts Disponibles

Todos los comandos se ejecutan desde la raíz del proyecto en la terminal:

| Comando                   | Descripción                                                   |
| ------------------------- | ------------------------------------------------------------- |
| `npm run dev`             | Inicia el servidor de desarrollo en `http://localhost:4321`   |
| `npm run build`           | Construye el sitio para producción en el directorio `./dist/` |
| `npm run preview`         | Vista previa del build de producción localmente               |
| `npm run format`          | Formatea automáticamente todo el código con Prettier          |
| `npm run format:check`    | Verifica si el código cumple con el formato de Prettier       |
| `npm run astro`           | Acceso directo a comandos de Astro CLI                        |
| `npm run astro -- --help` | Obtén ayuda sobre comandos disponibles de Astro               |

### Ejemplos de Uso

```bash
# Desarrollar localmente
npm run dev

# Compilar para producción
npm run build && npm run preview

# Formatear todo el código
npm run format

# Ver formatos no cumplidos
npm run format:check
```

---

## 📁 Estructura del Proyecto

```
my-website/
├── public/                          # Archivos estáticos públicos
│   └── assets/
│       └── backgrounds/             # Fondos e imágenes estáticas
├── src/
│   ├── components/                  # Componentes Astro reutilizables
│   │   ├── CallToAction.astro       # Llamada a acción
│   │   ├── ContactCTA.astro         # CTA de contacto
│   │   ├── Footer.astro             # Pie de página
│   │   ├── Grid.astro               # Componente de grid
│   │   ├── Hero.astro               # Sección hero principal
│   │   ├── Icon.astro               # Componente de iconos
│   │   ├── IconPaths.ts             # Datos de iconos
│   │   ├── MainHead.astro           # Cabecera HTML y meta tags
│   │   ├── Nav.astro                # Navegación
│   │   ├── Pill.astro               # Badge/Pill componente
│   │   ├── PortfolioPreview.astro   # Preview de proyecto
│   │   ├── Skills.astro             # Sección de habilidades
│   │   └── ThemeToggle.astro        # Toggle tema oscuro/claro
│   ├── content/
│   │   └── work/                    # Proyectos en markdown
│   │       ├── API REST MOVIE DB.md # Proyecto 1
│   │       ├── CatalogoLuzura.md    # Proyecto 2
│   │       └── nested/              # Proyectos adicionales
│   ├── images/
│   │   └── backgrounds/             # Imágenes para componentes
│   ├── layouts/
│   │   └── BaseLayout.astro         # Layout base para todas las páginas
│   ├── pages/                       # Páginas (cada archivo = ruta)
│   │   ├── index.astro              # Página de inicio (/)
│   │   ├── about.astro              # Página about (/about)
│   │   ├── work.astro               # Listado de proyectos (/work)
│   │   ├── 404.astro                # Página de error 404
│   │   └── work/
│   │       └── [...slug].astro      # Rutas dinámicas para proyectos
│   ├── styles/
│   │   └── global.css               # Estilos globales
│   └── content.config.ts            # Configuración de colecciones de contenido
├── astro.config.mjs                 # Configuración de Astro
├── tsconfig.json                    # Configuración de TypeScript
├── package.json                     # Dependencias y scripts
├── package-lock.json                # Lock file de npm
└── README.md                        # Este archivo
```

### Explicación de Directorios Clave

- **`src/components/`** - Componentes Astro reutilizables que se usan en varias páginas
- **`src/content/work/`** - Archivos Markdown con información de proyectos (es el CMS sin base de datos)
- **`src/layouts/`** - Plantillas que envuelven el contenido de las páginas
- **`src/pages/`** - Archivo que es ruta automática (Astro file-based routing)
- **`public/`** - Archivos que se copian tal cual al build final sin procesar

---

## 💻 Guía de Desarrollo

### Ejecutar en Modo Desarrollo

```bash
npm run dev
```

El servidor inicia en `http://localhost:4321` y se recarga automáticamente cuando guardas cambios.

### Crear un Nuevo Proyecto

1. Crea un archivo `.md` en `src/content/work/`:

```markdown
---
title: Mi Nuevo Proyecto
publishDate: 2026-04-17
img: /assets/proyecto.png
img_alt: Descripción de la imagen
description: Breve descripción del proyecto
tags:
  - tecnología1
  - tecnología2
---

# Mi Nuevo Proyecto

Descripción detallada del proyecto...
```

2. Los proyectos se mostrarán automáticamente en la página de trabajos

### Modificar Componentes

Los componentes están en `src/components/`. Cada archivo `.astro` es un componente:

- Edita el template en la sección `<template>`
- Añade estilos en etiquetas `<style>`
- Define lógica en el frontmatter (arriba del archivo)

### Personalizaciones Comunes

**Cambiar colores/estilos:** Edita `src/styles/global.css`

**Modificar navegación:** Edita `src/components/Nav.astro`

**Cambiar footer:** Edita `src/components/Footer.astro`

**Añadir nueva página:** Crea un archivo `.astro` en `src/pages/`

---

## 🎯 Proyectos Destacados

### 1. 🎬 API REST Movie DB

**Tecnologías:** Vanilla JavaScript, Tailwind CSS v4, TMDB API

Una aplicación minimalista y responsiva que consume la API de The Movie Database. Permite buscar películas, ver tendencias y detalles de cada film. Proyecto práctico del curso de API REST en Platzi.

**Características:**

- Búsqueda en tiempo real
- Películas en tendencia
- Información detallada de películas
- Diseño responsivo

### 2. 📚 Catálogo Luzura

**Tecnologías:** Frontend moderno, JavaScript

Proyecto que forma parte del aprendizaje en Platzi, demostrando habilidades en desarrollo Frontend.

---

## 🌐 Deployment

Este sitio está optimizado para ser desplegado en múltiples plataformas:

### Netlify (Recomendado)

```bash
# 1. Build el proyecto
npm run build

# 2. Conecta tu repo en Netlify y despliega
# Netlify detectará automáticamente que es un proyecto Astro
```

### Vercel

```bash
# Vercel también soporta Astro nativamente
# Solo conecta tu repositorio en vercel.com
```

### GitHub Pages

```bash
# Actualiza astro.config.mjs:
export default defineConfig({
  site: 'https://tuusuario.github.io',
  base: '/mi-portfolio',
});

npm run build
```

### Servidor Propio

```bash
npm run build
# Sube el contenido de ./dist/ a tu servidor
```

---

## 📚 Aprendizajes y Recursos

### Conceptos Aprendidos

- ✅ Framework Astro y su arquitectura
- ✅ Generación de sitios estáticos (SSG)
- ✅ File-based routing en Astro
- ✅ Componentes Astro
- ✅ TypeScript en proyectos Frontend
- ✅ Colecciones de contenido (Content Collections)
- ✅ Optimización de rendimiento web
- ✅ Responsive design y mobile-first
- ✅ Temas oscuro/claro (Dark Mode)

### Recursos Útiles

- 📖 [Documentación Oficial de Astro](https://docs.astro.build)
- 📖 [Curso JavaScript para Frontend - Platzi](https://platzi.com)
- 🎨 [Documentación de Tailwind CSS](https://tailwindcss.com)
- ⚡ [Web Vitals](https://web.dev/vitals/)
- 🎯 [Astro Best Practices](https://docs.astro.build/en/guides/best-practices/)

### Mejoras Futuras

- [ ] Blog integrado con comentarios
- [ ] Formulario de contacto funcional
- [ ] Integración con CMS (Sanity, Contentful)
- [ ] Soporte para i18n (múltiples idiomas)
- [ ] Integración con redes sociales
- [ ] Analytics avanzado
- [ ] PWA (Progressive Web App)

---

## 👥 Contribución

Si encuentras bugs o tienes sugerencias, siéntete libre de:

1. Abrir un **Issue**
2. Hacer un **Pull Request**
3. Contactarme directamente

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Ver [LICENSE](LICENSE) para más detalles.

---

## 🙋 Contacto

- 📧 Email: [tu-email@ejemplo.com]
- 🔗 LinkedIn: [tu-perfil]
- 🐙 GitHub: [tu-usuario]
- 🌐 Portafolio: https://tu-dominio.com

---

## 🎉 Agradecimientos

- [Astro](https://astro.build) por el increíble framework
- [Platzi](https://platzi.com) por la educación de calidad
- [Comunidad de Astro](https://astro.build/chat) por el soporte

---

**Última actualización:** Abril 2026
