# GEMINI.md

## Project Overview
Kaylon Tech is a professional consultancy website for an independent agency specializing in infrastructure, security, and software engineering. The project is designed as a **single-file SPA** (Single Page Application) for maximum simplicity and portability.

### Core Technologies
- **Frontend:** Vanilla HTML5, CSS3 (Modern features like Custom Properties and Grid), and Vanilla JavaScript.
- **Server:** Caddy (HTTP/2, automatic HTTPS, and static file serving).
- **Deployment:** Docker & Docker Compose.
- **Fonts:** Google Fonts (Fraunces, JetBrains Mono, Manrope).

## Architecture
The project follows a "no-build" philosophy. There are no package managers (npm/yarn), no bundlers (Webpack/Vite), and no framework dependencies.

- `site/index.html`: The entire application—HTML structure, CSS styling, and JavaScript logic (~1500+ lines).
- `site/favicon.svg`: SVG-based favicon.
- `Caddyfile`: Configuration for the Caddy web server.
- `docker-compose.yml`: Defines the local development environment using the official Caddy Docker image.

### Internationalization (i18n)
The site supports Dutch (`nl`) and English (`en`).
- **Storage:** A `translations` JavaScript object in `index.html`.
- **Mechanism:** Elements with `data-key` attributes are updated via the `setLanguage(lang)` function.
- **Persistence:** The user's language preference is saved in `localStorage`.

### Design System
Visual styles are managed through CSS Custom Properties (Design Tokens) defined in `:root`.
- **Primary Colors:** `--bg` (#0b0b0c), `--amber` (#ff9443), `--ink` (#ebe6d7).
- **Typography:** Serif (Fraunces) for headings, Sans (Manrope) for body text, Mono (JetBrains Mono) for technical details.
- **Effects:** Includes a noise texture overlay and scanline effects for a technical aesthetic.

## Building and Running
The project does not require a build step.

### Local Development
Run the site locally using Docker Compose:
```bash
docker-compose up
```
The site will be available at `http://localhost`.

### Manual Serving
Alternatively, you can serve the `site/` directory using any static file server (e.g., `python -m http.server`).

## Development Conventions
- **Single-File Constraint:** Keep all new HTML, CSS, and JS within `site/index.html` unless a transition to a build system is explicitly requested.
- **i18n first:** When adding or modifying text, ensure you update both the `nl` and `en` keys in the `translations` object and use the appropriate `data-key` in the HTML.
- **Design Consistency:** Always use the defined CSS variables (`--amber`, `--ink`, etc.) for styling to maintain the dark-technical theme.
- **Interactive Feedback:** Maintain the "morphing" animation pattern for text changes and interactive elements.

## Known Placeholders
The following values in `site/index.html` currently contain placeholders that need to be filled:
- `KVK · [NUMMER IN TE VULLEN]`
- `BTW · [NUMMER IN TE VULLEN]`
