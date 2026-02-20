# hrishikeshsaraiya.com

Personal website for Hrishikesh Saraiya. Built with Astro 5, Tailwind CSS 4, and MDX.

## Dev commands

```bash
npm run dev      # Start dev server → http://localhost:4321
npm run build    # Production build (check for errors before committing)
npm run preview  # Preview production build locally
```

## Stack

- **Framework**: Astro 5 (static output)
- **Styling**: Tailwind CSS 4 via `@tailwindcss/vite` — no `tailwind.config.js`, config lives in `src/styles/global.css` using `@theme` and `@layer`
- **Blog**: MDX content collections — posts in `src/content/blog/*.mdx`
- **Fonts**: Inter (body), JetBrains Mono (code/labels) — loaded from Google Fonts in `BaseLayout.astro`

## Project structure

```
src/
  components/     # One file per section: Hero, About, Experience, Projects, BlogPreview, Nav, Footer, ThemeToggle, BlogCard
  layouts/        # BaseLayout.astro (all pages), BlogLayout.astro (blog posts)
  pages/          # index.astro, blog/index.astro, blog/[slug].astro
  content/blog/   # MDX blog posts (filename = URL slug)
  styles/         # global.css — all CSS vars, theme, utilities, prose styles
```

## Content locations

All content is data-driven — edit the arrays at the top of each component:
- **Hero typewriter roles** → `Hero.astro` `roles` array in `<script>`
- **Skills, bio, stats** → `About.astro`
- **Work history** → `Experience.astro` `jobs` array
- **Projects** → `Projects.astro` `projects` array
- **Social links** → `Footer.astro` `socials` array
- **Blog posts** → `src/content/blog/*.mdx` (frontmatter: title, description, pubDate, tags, draft)

## Styling conventions

- CSS custom properties (`--bg`, `--text`, `--accent`, etc.) are set on `:root` and `.dark` in `global.css`
- Dark mode is toggled via `dark` class on `<html>`, persisted in `localStorage`
- **Do not use bare Tailwind color utilities** (`bg-indigo-500` etc.) — use the custom utility classes defined in `@layer utilities` in `global.css` (`bg-accent`, `text-accent`, `bg-site`, `bg-secondary`, `border-site`, `text-muted`) or inline `style="color: var(--accent)"`
- Scroll-reveal: add class `reveal` to any element; the Intersection Observer in `BaseLayout.astro` handles the rest
- 3D tilt on project cards: add `data-tilt` attribute

## Commit style

- Short imperative subject line
- No co-author lines
