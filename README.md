# Portfolio Web — Gerardo Caycho

Portafolio personal construido con **Astro 5** y **Tailwind CSS 3**. Página única, estática, en español, con tema oscuro (paleta `stone` + acento rojo) y tipografía **Space Grotesk**.

## 🚀 Instalación y uso

### Prerrequisitos

- Node.js 18 o superior
- pnpm (gestor de paquetes del proyecto; `pnpm-lock.yaml`)

### Pasos

```bash
git clone git@github.com:withoutnicks/my-portfolio-web.git
cd my-portfolio-web

pnpm install
pnpm dev
```

### Scripts disponibles

| Comando        | Descripción                                                            |
| -------------- | ---------------------------------------------------------------------- |
| `pnpm dev`     | Servidor de desarrollo en `localhost:4321`                             |
| `pnpm build`   | Type check (`astro check`) + build de producción (`astro build`)       |
| `pnpm preview` | Previsualiza el build de producción                                    |
| `pnpm astro`   | CLI de Astro (comandos arbitrarios)                                    |

---

## 🧱 Estructura

```
src/
  components/        # Secciones y componentes de la página
    AstroIcon.astro, Badge.astro, Button.astro, Contact.astro,
    About.astro, Footer.astro, Header.astro, Hero.astro,
    LinkButton.astro, Projects.astro, Skills.astro, Studies.astro,
    SubtitleSection.astro
    icons/           # Íconos SVG inline (acción + tecnologías), en Astro
  layouts/
    Layout.astro     # Chrome de la página: Header/Footer, globals.css,
                     # fuente Space Grotesk, meta/OG
  pages/
    index.astro      # Ruta única
  styles/
    globals.css      # Directivas @tailwind + clases @layer components
public/
  cv_gcaycho.pdf, favicon.svg, profile.webp, poster/  # Assets estáticos
```

---

## 📐 Convenciones

- **Una ruta**: `src/pages/index.astro` compone `Layout` + secciones Hero, About, Projects, Studies, Skills, Contact.
- **Secciones con `id`** (`#sobre-mi`, `#proyectos`, `#educacion`, `#habilidades`, `#contacto`): enlazan con la navegación del Header.
- **Datos de proyectos**: array declarado en el frontmatter de `Projects.astro` (`name`, `description`, `stack: string[]`, `links: {text, href}[]`, `bannerUrl`).
- **Cliente**: un solo script (`<script>` de Astro, bundled) en `Hero.astro` para copiar el email al portapapeles. Sin React ni hidratación.
- **Estilos**: la configuración base de Tailwind viene de `@astrojs/tailwind` con `applyBaseStyles: false`; las directivas `@tailwind` viven en `globals.css`.
- **Clases de componente** en `globals.css` (`@layer components`): `.link`, `.btn`, `.btn-primary`, `.badge`.
- **Tema oscuro fijo** (`bg-stone-950`): el sitio no alterna temas, por lo que las variantes `dark:` no se usan.
- **Tipografía**: Space Grotesk única (`font-sans`), importada en `Layout.astro` vía `@fontsource-variable/space-grotesk`.

## 📄 Contenido y assets

- El texto de la interfaz está en español (`<html lang="es">`).
- Los estáticos viven en `public/` y se referencian rutas raíz: `/profile.webp`, `/cv_gcaycho.pdf`, `/poster/*.svg`.
- Sin formulario de contacto: la sección Contacto lista solo GitHub y LinkedIn; el email se copia desde el Hero.
