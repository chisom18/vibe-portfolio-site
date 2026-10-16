# Elikwu Chisom Portfolio

A minimal personal portfolio built with Astro and plain CSS.

## Local development

1. Install dependencies: `npm install`
2. Start the dev server: `npm run dev`
3. Open the local URL shown in the terminal.

## Production build

1. Run: `npm run build`
2. Preview locally: `npm run preview`

## Netlify deployment

1. Push this project to a GitHub repository.
2. Log in to Netlify and choose Add new site > Import from Git.
3. Select the repository and keep the build settings as:
   - Build command: `npm run build`
   - Publish directory: `dist`
4. Deploy the site.
5. If needed, set a free subdomain from Netlify.

## Updating content

Main editable files:

- `src/pages/index.astro` — homepage content and featured projects
- `src/pages/about.astro` — about page content
- `src/pages/projects.astro` — project gallery content
- `src/components/NewsletterForm.astro` — newsletter form behavior and messages
- `src/components/Navigation.astro` — navigation structure
- `src/components/Footer.astro` — footer links and placeholder social links
- `src/styles/global.css` — all visual styles and layout rules

## Newsletter form status

The email form is intentionally placeholder-only. It validates input locally and displays a message explaining that registration is not connected yet. It does not store or submit email addresses anywhere.

The form can be connected to a future newsletter provider without redesigning the page structure.
