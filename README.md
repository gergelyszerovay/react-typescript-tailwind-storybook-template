# React + Tailwind 4 + Storybook 10 Boilerplate

Minimal starter for building UI components with React 19, Tailwind CSS 4, Vite 8, and Storybook 10.

## Stack

- **React 19** with TypeScript 6
- **Tailwind CSS 4** (via `@tailwindcss/vite` plugin)
- **Vite 8** dev server and bundler
- **Storybook 10** (`@storybook/react-vite`) with addons: a11y, docs, vitest, MCP
- **Vitest** with Playwright browser testing (Storybook addon-vitest integration)
- **ESLint** with React Hooks and Storybook plugins

## Getting started

```sh
pnpm install
```

### Development

```sh
pnpm dev          # Vite dev server on http://localhost:5173
pnpm storybook    # Storybook on http://localhost:6006
```

### Build and lint

```sh
pnpm build
pnpm lint
```

## Project structure

```
├── .storybook/
│   ├── main.ts        # Storybook config with Tailwind vite plugin
│   └── preview.ts     # Global CSS import (src/index.css)
├── src/
│   ├── index.css      # Tailwind entry: @import "tailwindcss", @source, counter
│   ├── assets/        # Image and SVG assets
│   ├── components/    # Component .tsx + .stories.tsx files
│   ├── App.tsx
│   └── main.tsx
├── public/
│   ├── icons.svg      # Shared SVG symbol sprite
│   └── favicon.svg
├── vite.config.ts
├── vitest.config.ts
├── tsconfig.json
└── eslint.config.js
```

## Tailwind 4 counter trick

`src/index.css` contains a counter comment:

```css
@import "tailwindcss";
@source "./**/*.{ts,tsx}";
/* counter: 0 */
```

Storybook's dev server sometimes doesn't pick up new Tailwind utility classes added in `.tsx` files. Bumping the counter forces a CSS rebuild and ensures the new classes are included.
