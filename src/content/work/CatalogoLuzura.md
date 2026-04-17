---
title: Catalogo Luzura
publishDate: 2019-12-01 00:00:00
img: /assets/Catalogo.png
img_alt: An Image of a virtual shop called Luzura
description: |
  Catálogo digital institucional estático, generado en HTML + CSS + JS puro,  
  diseñado para presentar productos textiles profesionales de la marca Dotaciones Luzura.
tags:
  - Dev
---

# 📋 Catálogo Dotaciones Luzura — Documentación Técnica

> Catálogo digital institucional estático, generado en HTML + CSS + JS puro,  
> diseñado para presentar productos textiles profesionales de la marca **Dotaciones Luzura**.

---

## 📁 Estructura del Proyecto

```
dotaciones-luzura/
├── catalogo_luzura.html        # Archivo principal del catálogo
├── /assets/                    # (recomendado al escalar)
│   └── /images/                # Imágenes de productos
│       ├── Bata_Carolina.png
│       ├── Bata_Joseane.png
│       ├── Bata_Masculina.png
│       ├── Bata_Paola.png
│       ├── gorro.png
│       ├── 3_batas_femeninas.png
│       ├── Basico.png
│       ├── Pijama_2.png
│       ├── Pijama_3.png
│       ├── Pijama_Basica.png
│       └── Pijama.png
└── README_catalogo_luzura.md   # Este documento
```

> **Nota:** En la versión actual, el HTML referencia las imágenes desde su ruta de origen local. Al desplegar en producción, mover todas las imágenes a `/assets/images/` y actualizar los `src` correspondientes.

---

## 🧱 Arquitectura del HTML

El catálogo es un **archivo HTML único autocontenido** (`catalogo_luzura.html`). No depende de frameworks externos. Toda la lógica de estilos y comportamiento está embebida en el mismo archivo bajo las etiquetas `<style>` y `<script>`.

### Secciones principales del documento

```
<body>
 ├── <section class="cover">          → Portada de marca
 ├── <nav>                            → Navegación sticky con scroll suave
 └── <main>
      ├── section#batas-femeninas     → Sección 01
      ├── section#batas-masculinas    → Sección 02
      ├── section#pijamas             → Sección 03
      └── section#accesorios          → Sección 04
```

---

## 🎨 Sistema de Diseño (CSS Variables)

Todas las decisiones de color están centralizadas en la declaración `:root`. Cambiar un color aquí lo propaga automáticamente a toda la página.

```css
:root {
  --gold:        #C9A96E;   /* Dorado institucional — acentos y etiquetas */
  --gold-light:  #E8D5A3;   /* Dorado suave — subtítulos en portada */
  --cream:       #FAF8F4;   /* Fondo general de la página */
  --ink:         #1A1714;   /* Negro cálido — tipografía principal y portada */
  --muted:       #7A7068;   /* Gris cálido — descripciones secundarias */
  --line:        #E2DDD6;   /* Línea divisora — bordes sutiles */
  --white:       #FFFFFF;   /* Fondo de tarjetas */
  --section-gap: 100px;     /* Espaciado vertical entre secciones */
}
```

### Tipografía

Se cargan dos familias desde **Google Fonts**:

| Variable de uso | Fuente | Peso | Aplicación |
|---|---|---|---|
| Display / Títulos | `Cormorant Garamond` | 300, 400, 500, 600 | Nombre de marca, títulos de sección, nombres de producto |
| Cuerpo / UI | `Jost` | 200, 300, 400, 500 | Navegación, etiquetas, descripciones, texto general |

```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@200;300;400;500&display=swap" rel="stylesheet">
```

---

## 🖥️ Componentes

### 1. Portada (`.cover`)

Pantalla completa de entrada a la marca. Ocupa el 100% del viewport (`min-height: 100vh`).

**Elementos:**

- Fondo negro carbón (`--ink`)
- Dos gradientes radiales superpuestos en dorado para dar profundidad sutil
- Marco decorativo doble con `::before` y `::after` (pseudo-elementos absolutos)
- Nombre de marca en `Cormorant Garamond` peso 300, tamaño fluido con `clamp()`
- Subtítulo en cursiva dorado claro
- Animación de entrada `fadeUp` (keyframe CSS, 1.2s)

```css
/* Fórmula de tamaño fluido responsivo */
font-size: clamp(52px, 8vw, 96px);
/* min: 52px | preferido: 8% del viewport | max: 96px */
```

---

### 2. Navegación (`<nav>`)

Barra sticky que aparece al hacer scroll pasada la portada.

**Características:**

- `position: sticky; top: 0` — se adhiere al tope de la pantalla al desplazarse
- `backdrop-filter: blur(12px)` — efecto vidrio esmerilado sobre el contenido
- Fondo semi-transparente: `rgba(250,248,244,0.95)`
- Links con `letter-spacing: 0.3em` y hover en dorado
- Oculto en móvil (`display: none` en breakpoint `≤768px`)

**Links de ancla** (scroll suave vía `scroll-behavior: smooth` en `html`):

| Texto | Ancla destino |
|---|---|
| Batas Fem. | `#batas-femeninas` |
| Batas Masc. | `#batas-masculinas` |
| Pijamas | `#pijamas` |
| Accesorios | `#accesorios` |

---

### 3. Encabezado de Sección (`.section-header`)

Cada sección comienza con un encabezado de dos columnas:

```
[ Número grande decorativo ]  [ Etiqueta pequeña en dorado ]
                               [ Título de sección ]
```

- El número (`01`–`04`) usa `Cormorant Garamond` a 80px en color `--line` (muy tenue), cumple función decorativa, no informativa
- El título usa `clamp(28px, 4vw, 44px)` para escala fluida

---

### 4. Grilla de Productos (`.product-grid`)

Sistema de grid CSS responsivo con `auto-fill` y `minmax()`:

```css
/* Grid estándar */
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 2px;
}

/* Grid destacado (columnas más anchas) */
.product-grid.featured {
  grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
}
```

**Comportamiento responsivo automático:**

- En pantallas anchas: 3 columnas
- En pantallas medianas: 2 columnas
- En móvil (`≤768px`): 1 columna forzada

---

### 5. Tarjeta de Producto (`.product-card`)

Componente central del catálogo. Estructura interna:

```
.product-card
 ├── .card-image-wrap
 │    ├── <img>               → Imagen del producto
 │    ├── .card-overlay        → Overlay oscuro con texto (aparece en hover)
 │    └── .card-badge          → Etiqueta opcional (ej: "Destacado", "Unisex")
 └── .card-body
      ├── .card-category       → Categoría en dorado, mayúsculas
      ├── .card-name           → Nombre del producto (Cormorant Garamond)
      └── .card-desc           → Descripción técnica visual
```

**Interacciones:**

| Evento | Efecto |
|---|---|
| Hover en card | `translateY(-4px)` + sombra profunda |
| Hover en imagen | `scale(1.04)` con `transition: 0.6s` |
| Hover en card | Overlay oscuro con opacidad 0→1 |

**Variante panorámica** (`.product-card.panoramic`):

- `grid-column: span 2` — ocupa dos columnas
- `aspect-ratio: 16/7` — formato apaisado para imágenes colección

---

### 6. Divisor Decorativo (`.divider`)

Separador visual entre secciones. Compuesto por:

- Línea horizontal (`--line`)
- Dos rombos dorados en los extremos (cuadrado rotado 45°)

```css
.divider-gem {
  width: 8px;
  height: 8px;
  background: var(--gold);
  transform: rotate(45deg);
}
```

---

### 7. Animaciones de Entrada

**Portada:** `@keyframes fadeUp` aplicado al `.cover-inner`

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

**Secciones y tarjetas:** animación por **Intersection Observer** (JavaScript)

Todo elemento con clase `.anim-in` comienza invisible (`opacity: 0; transform: translateY(20px)`). Cuando el viewport lo alcanza, se agrega la clase `.visible` que activa la transición CSS.

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.08, rootMargin: '0px 0px -40px 0px' });
```

**Efecto escalonado (stagger):** cada elemento recibe un `transition-delay` basado en su posición en el grupo:

```javascript
el.style.transitionDelay = `${(i % 4) * 80}ms`;
// 0ms, 80ms, 160ms, 240ms → repite cada 4 elementos
```

---

## 🗂️ Catálogo de Productos

### Sección 01 — Batas Femeninas

| ID | Nombre | Descripción Visual | Tipo de Card |
|---|---|---|---|
| `bata-carolina` | Bata Carolina | Menta, cierre dorado, cuello mao, hombros abullonados | Estándar (featured) |
| `bata-joseane` | Bata Joseane | Blanca, espalda cruzada, botón dorado, solapa elegante | Estándar (featured) |
| `bata-paola` | Bata Paola | Blanca, botones dorados, semi-entallada, cuello solapa | Estándar (featured) |
| `3-batas-fem` | Colección Batas Femeninas | Rosa/blancas, 3 modelos en una imagen | Panorámica |

### Sección 02 — Batas Masculinas

| ID | Nombre | Descripción Visual | Tipo de Card |
|---|---|---|---|
| `bata-masculina` | Bata Masculina Bicolor | Negro + azul marino, cierre, cuello mao, mangas raglan | Panorámica |

### Sección 03 — Pijamas Clínicos

| ID | Nombre | Descripción Visual | Tipo de Card |
|---|---|---|---|
| `pijama-basica` | Pijama Básica | Azul marino unisex, V-neck, pantalón cargo recto | Estándar |
| `pijama-azul` | Pijama Azul Acero | Azul pizarra, top V + detalles dorados, jogger con cordón | Estándar |
| `pijama-burdeos` | Pijama Burdeos | Rojo burdeos, hombros abullonados, cierre dorado, slim-fit | Estándar |
| `pijama-terracota` | Pijama Terracota | Terracota/salmón, V-zip, solapa plegada, tallas inclusivas | Estándar |
| `set-malva` | Set Básico Malva | Malva rosado, pijama + bata blanca + bata corta | Panorámica |

### Sección 04 — Accesorios

| ID | Nombre | Descripción Visual | Tipo de Card |
|---|---|---|---|
| `gorro` | Gorro Quirúrgico | Azul marino, lazos ajustables, bordado dorado personalizado | Estándar (aspect 4/3) |

---

## 📐 Responsive Breakpoints

| Breakpoint | Comportamiento |
|---|---|
| `> 768px` | Layout completo: nav con links, grillas multicol, cards panorámicas |
| `≤ 768px` | Nav sin links, grillas a 1 col, cards panorámicas se vuelven simples, footer en columna |
| `≤ 480px` | Marco decorativo de portada oculto |

---

## 🔗 Dependencias Externas

| Recurso | URL | Propósito |
|---|---|---|
| Google Fonts | `fonts.googleapis.com` | Tipografías `Cormorant Garamond` y `Jost` |

**Sin dependencias de JavaScript externas.** Todo el JS es vanilla (< 15 líneas).

---

## 🚀 Guía de Despliegue

### Opción 1 — Despliegue estático simple

1. Copiar `catalogo_luzura.html` a cualquier servidor o hosting estático
2. Subir todas las imágenes al mismo directorio o a `/assets/images/`
3. Actualizar los atributos `src` de cada `<img>` para reflejar las nuevas rutas
4. Abrir en navegador — no requiere backend

```bash
# Ejemplo con servidor local en Python
python -m http.server 8080
# → http://localhost:8080/catalogo_luzura.html
```

### Opción 2 — Integración en ecommerce / CMS

El catálogo está diseñado para ser **fácilmente conectable** a un sistema dinámico. Ver sección de escalabilidad abajo.

---

## 🧩 Escalabilidad y Arquitectura Futura

### Conversión a componentes (React / Vue)

Cada `.product-card` puede convertirse en un componente reutilizable recibiendo props:

```jsx
// React — ejemplo de componente ProductCard
function ProductCard({ image, category, name, description, badge, panoramic }) {
  return (
    <div className={`product-card ${panoramic ? 'panoramic' : ''}`}>
      <div className="card-image-wrap">
        <img src={image} alt={name} />
        {badge && <span className="card-badge">{badge}</span>}
      </div>
      <div className="card-body">
        <p className="card-category">{category}</p>
        <h3 className="card-name">{name}</h3>
        <p className="card-desc">{description}</p>
      </div>
    </div>
  );
}
```

### Esquema de datos JSON (para API o CMS)

Estructura recomendada para conectar el catálogo a un backend:

```json
{
  "brand": "Dotaciones Luzura",
  "catalog_version": "1.0.0",
  "categories": [
    {
      "id": "batas-femeninas",
      "label": "Colección Profesional",
      "title": "Batas Femeninas",
      "section_number": "01",
      "products": [
        {
          "id": "bata-carolina",
          "name": "Bata Carolina",
          "category": "Bata Médica / Estética",
          "description": "Bata larga en tono menta con cierre dorado frontal...",
          "images": [
            {
              "url": "/assets/images/Bata_Carolina.png",
              "alt": "Bata Carolina",
              "view": "multiple"
            }
          ],
          "badge": "Destacado",
          "card_type": "standard",
          "tags": ["bata", "femenina", "medica", "estetica", "menta", "zipper"]
        }
      ]
    }
  ]
}
```

### Personalización futura recomendada

| Feature | Implementación sugerida |
|---|---|
| Filtrado por categoría | JS: toggle de clases `hidden` en tarjetas |
| Búsqueda de productos | JS: filter sobre array de productos en JSON |
| Galería de imágenes por producto | Modal con múltiples vistas (frontal/lateral/detalle) |
| Formulario de cotización | Form HTML + integración con WhatsApp API o email |
| Multiidioma | i18n con objeto de traducciones en JS |
| Precios dinámicos | Conexión a API REST con autenticación |
| Carrito de pedido | Estado local con `localStorage` o Redux |

---

## ✏️ Guía de Personalización Rápida

### Cambiar colores de la marca

Editar las variables en `:root` dentro del `<style>`:

```css
:root {
  --gold: #C9A96E;   /* ← Cambiar por el color dorado deseado */
  --ink: #1A1714;    /* ← Cambiar por el color oscuro principal */
  --cream: #FAF8F4;  /* ← Cambiar por el fondo general */
}
```

### Agregar un producto nuevo

Copiar el bloque de tarjeta dentro del `<div class="product-grid">` correspondiente:

```html
<div class="product-card anim-in">
  <div class="card-image-wrap">
    <img src="ruta/a/imagen.png" alt="Nombre del producto">
    <div class="card-overlay"><span class="card-overlay-text">Vista Completa</span></div>
    <!-- Opcional: -->
    <div class="card-badge">Nuevo</div>
  </div>
  <div class="card-body">
    <p class="card-category">Categoría del producto</p>
    <h3 class="card-name">Nombre del Producto</h3>
    <p class="card-desc">Descripción técnica y visual del producto.</p>
  </div>
</div>
```

### Agregar una sección nueva

```html
<!-- Divisor antes de la nueva sección -->
<div class="divider">
  <div class="divider-gem"></div>
  <div class="divider-line"></div>
  <div class="divider-gem"></div>
</div>

<!-- Nueva sección -->
<section class="section anim-in" id="nueva-categoria">
  <div class="section-header">
    <div class="section-number">05</div>
    <div class="section-info">
      <p class="section-label">Subcategoría</p>
      <h2 class="section-title">Nombre de<br>Categoría</h2>
    </div>
  </div>
  <div class="product-grid">
    <!-- product-cards aquí -->
  </div>
</section>
```

Agregar también el link en la navegación:

```html
<li><a href="#nueva-categoria">Nueva Cat.</a></li>
```

---

## 🧪 Compatibilidad

| Navegador | Soporte |
|---|---|
| Chrome 90+ | ✅ Completo |
| Firefox 88+ | ✅ Completo |
| Safari 14+ | ✅ Completo |
| Edge 90+ | ✅ Completo |
| IE 11 | ❌ No soportado (`grid`, `clamp()`, `backdrop-filter`) |

**Características CSS modernas utilizadas:**

- `CSS Grid` con `auto-fill` + `minmax()`
- `clamp()` para tipografía fluida
- `backdrop-filter: blur()`
- `aspect-ratio`
- `Intersection Observer API` (JS)
- CSS Custom Properties (`var()`)

---

## 📌 Convenciones de Código

- **Clases CSS:** kebab-case (`.product-card`, `.card-image-wrap`)
- **IDs de sección:** kebab-case descriptivo (`#batas-femeninas`)
- **Imágenes:** nombres con `_` y PascalCase por modelo (`Bata_Carolina.png`)
- **Comentarios CSS:** bloques separados con `/* ── NOMBRE ── */`
- **Comentarios HTML:** secciones marcadas con `<!-- ═══ SECCIÓN ═══ -->`
- **Variables CSS:** agrupadas en `:root`, nombres semánticos no literales (`--ink` no `--black`)

---

## 👤 Autoría y Contexto

| Campo | Valor |
|---|---|
| Marca | Dotaciones Luzura |
| Tipo de proyecto | Catálogo institucional digital |
| Tecnología | HTML5 + CSS3 + Vanilla JS |
| Versión | 1.0.0 |
| Idioma | Español |
| Propósito futuro | Integración con ecommerce / tienda online |
