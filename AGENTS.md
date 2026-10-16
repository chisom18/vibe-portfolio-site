# Project Guide for AI Agents and Contributors

This repository contains Elikwu Chisom's static personal portfolio, built with Astro and plain CSS. Keep changes simple, readable, accessible, and consistent with the existing black, white, and vivid red visual identity. Do not introduce a backend, database, newsletter provider, analytics, or unnecessary dependencies without an explicit request.

## Running Locally on Windows

The Astro development server uses port `4321`, configured in `astro.config.mjs`. VS Code's Chrome launch configuration in `.vscode/launch.json` points at the same port.

1. Open this project folder (`C:\Users\USER\vibe`) in VS Code.
2. Open **Terminal > New Terminal**.
3. In the terminal, run:

   ```powershell
   cd C:\Users\USER\vibe
   npm.cmd install
   npm.cmd run dev
   ```

   Dependency installation is normally needed only after first setup or a dependency change. For later sessions, start with `npm.cmd run dev`.
4. Wait for Astro to print its local address, then open `http://localhost:4321` in a browser.
5. Keep the VS Code terminal and development server running while viewing the local site. Closing the terminal, closing VS Code, or pressing `Ctrl+C` stops the server. The browser will then report that localhost refused to connect.
6. To resume after the server has stopped, open a terminal and run `npm.cmd run dev` again.

The `npm.cmd` spelling is intentional for PowerShell users: it calls npm's Windows command wrapper and avoids PowerShell blocking `npm.ps1` under restrictive script-execution policies. There is no need to change the PowerShell execution policy just to run this project.

## Node.js Troubleshooting

Node.js LTS and npm must be installed. In a fresh VS Code terminal, check them with:

```powershell
node -v
npm.cmd -v
```

If `node` is not recognized:

- Install the current Node.js LTS release from the official site at <https://nodejs.org/>. The Windows installer includes npm and normally adds Node to PATH.
- Finish the installer, close and reopen VS Code (or at least open a new terminal), and run the version checks again. Existing terminals do not automatically receive PATH changes made after they opened.
- If the installer reports success but a new terminal still cannot find Node, check that `C:\Program Files\nodejs` exists and is included in the Windows PATH. Reopen VS Code after changing PATH.
- `winget install --id OpenJS.NodeJS.LTS -e --source winget` is an optional installation route. If winget reports a source error, use the official Node.js website installer instead.

If `npm` reports that `npm.ps1` cannot be loaded because script execution is disabled, use `npm.cmd` in the commands in this guide. Do not concatenate or paste commands together; enter one command at a time and press Enter.

## Commands

Run these from the project root:

```powershell
npm.cmd install
npm.cmd run dev
npm.cmd run build
npm.cmd run preview
```

- `npm.cmd install` installs the dependencies listed in `package-lock.json` and `package.json`.
- `npm.cmd run dev` starts the local development server at `http://localhost:4321` and remains active until stopped.
- `npm.cmd run build` creates the static production site in `dist/`.
- `npm.cmd run preview` serves the built site locally; build first, and keep this terminal running while previewing.

If the browser says localhost refused to connect, first check that the server command is still running in a terminal and that the address is exactly `http://localhost:4321`. Restart `npm.cmd run dev` if the terminal has closed or returned to the PowerShell prompt.

## Project Structure and Content

- `src/pages/index.astro` — home page and featured-project data
- `src/pages/about.astro` — about page content
- `src/pages/projects.astro` — project gallery and project data
- `src/components/` — shared navigation, footer, newsletter form, and project card
- `src/layouts/BaseLayout.astro` — shared document metadata and page shell
- `src/styles/global.css` — global design tokens, typography, responsive layout, and focus styles
- `public/images/` — replaceable local placeholder project visuals
- `public/favicon.svg` — favicon placeholder
- `astro.config.mjs` — static output, site URL placeholder, and development server settings
- `netlify.toml` — Netlify build command and publish directory
- `.vscode/launch.json` — Chrome debugger URL; keep it aligned with Astro's configured port (`4321`)

Use clearly marked placeholders until real biography, project, or social-link content is supplied. Do not invent personal history, clients, credentials, testimonials, awards, or results. The `site` value in `astro.config.mjs` is a placeholder and should be updated when a real domain is selected.

## Newsletter Form

`src/components/NewsletterForm.astro` is a reusable, frontend-only placeholder. It performs basic email validation, prevents a normal page reload, and displays an honest message that signup is not connected. It must not store or transmit email addresses. Do not claim that anyone has subscribed. Connect a provider only when explicitly requested and then document the resulting data flow.

## Build and Deployment

Before considering code changes complete, run the production build when Node.js is available:

```powershell
npm.cmd run build
```

The site is configured for static deployment on Netlify. The current settings are build command `npm run build` and publish directory `dist` in `netlify.toml`. After pushing the repository to GitHub, import it in Netlify and use those settings; a Netlify-provided free subdomain can be used until a custom domain is chosen.

## Editing Guidelines

- Prefer Astro components, semantic HTML, and plain CSS already used by the project.
- Keep content editable in the page or project data rather than duplicating layout markup.
- Keep forms keyboard accessible, labels descriptive, focus visible, and responsive behavior intact.
- Avoid adding client-side JavaScript unless necessary; do not add a newsletter integration without explicit authorization.
- Preserve user changes and avoid unrelated cleanup.
