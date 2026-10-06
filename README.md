# The Curiosity Engine — Sudhanshu Bhale

A playable pixel-art physics universe and AI engineering portfolio. Built with static HTML, CSS, JavaScript, and Canvas. No installation, build step, credentials, backend, or tracking.

## Preview

From this directory:

```sh
python3 -m http.server 8765 --bind 127.0.0.1 --directory dist
```

Open http://127.0.0.1:8765/. A preview server is already running from the current chat.

## Explore

- An original pixel-art island with clickable destinations and a photo-based explorer avatar.
- Newton's live orbit on the homepage, with an adjustable version inside the scientist atlas.
- 24 scientist discoveries with animations, explanations, adjustable parameters, pause, and reset.
- Four games: Newton's projectile landings, Faraday's induction challenge, Maxwell's wave matching, and Feynman's photon-pattern detective game.
- A four-stamp discovery passport saved in localStorage in the visitor's browser. No server or account.
- Scientist search, a free-form physics playground, notes, and a small command terminal.
- Draggable desktop windows with minimize, restore, maximize, close, and keyboard controls; responsive phone layouts.
- Rtifact experience, two curated quant case studies, LinkedIn/GitHub contact links, and an about view with a generated pixel portrait.

## Scientists

Newton, Galileo, Kepler, Hooke, Coulomb, Ampère, Faraday, Maxwell, Hertz, Huygens, Young, Doppler, Einstein, Planck, Bohr, Curie, Rutherford, Schrödinger, Feynman, Noether, Bose, Raman, Boltzmann, and Dirac.

These are educational visualizations with simplified scale, time, and colors. The site distinguishes qualitative illustrations, normalized models, and historical models from literal physical trajectories. The photon game samples an idealized far-field intensity distribution. It does not model an entire experimental apparatus.

## Content and artwork

- Professional title, Rtifact start date (November 2025), responsibilities, current work, location, and education come from the user's supplied LinkedIn screenshots.
- The Polymarket arbitrage and BTC market-research project details and technical skills come from the user's supplied resume screenshot.
- The user confirmed 100 percentile in Physics in the March 2021 JEE Main attempt.
- No job metrics, performance results, repository links for the quant projects, or live trading integrations were invented.
- The old GitHub repository catalogue was removed at the user's request.
- The homepage title and physics notes are original copy, not quotations attributed to scientists.
- Three original assets were made with built-in image generation: the island, a portrait adapted from the pink-shirt photo, and an explorer adapted from the gym photo. Prompts are in `image-prompts.md`. The explorer includes a genuine transparent background.

## Source layout

- `dist/index.html`: world layout, hotspots, metadata, dock
- `dist/style.css`: pixel theme, windows, responsive layouts
- `dist/app.js`: base window manager, orbit, terminal, quant case studies, free lab
- `dist/universe.js`: scientist atlas, 24 visualizations, four games, passport, experience, photo-based profile
- `dist/projects.js`: curated quant project data
- `dist/assets/`: original generated artwork

Google Fonts supplies DM Sans, IBM Plex Mono, and Silkscreen, with system fallbacks. All app logic and images are served locally. The layout works without font downloads.

## Controls

Click a map destination or dock icon. Range controls support keyboard arrows. Escape closes the foremost window. Alt+1 opens selected work, Alt+2 the free lab, and Alt+3 the terminal.

Terminal commands: `help`, `whoami`, `ls`, `open <app>`, `physics`, `github`, and `clear`. Apps include `games`, `atlas`, `projects`, `experience`, `lab`, `notes`, `about`, and `contact`.

A feature-detected WebMCP tool, `open_physics_discovery`, opens a scientist and optionally configures a validated parameter; it cannot award stamps. The website works in browsers without WebMCP.

## Validation

- JavaScript syntax checks passed.
- All 24 scientist views opened in the browser without console errors.
- Desktop and mobile layouts were visually inspected, with all local images loaded and no horizontal overflow in checked views.
- Real browser checks covered a successful projectile landing, induction input, photon generation, calculator arithmetic, window controls, and terminal commands.
- Isolated tests executing the actual game source passed all four complete win paths, wrong/premature answers, passport persistence, and pause behavior without changing the user's browser progress.
- WebMCP registration, a valid parameter change, and intentional rejection of an out-of-range parameter were checked. Invalid input preserved the current valid state.

## Publishing

Cloudflare Workers Static Assets is configured in `wrangler.jsonc`. No public deployment or hosted account has been created.

### GitHub auto-deployment

1. Put the contents of this directory in a GitHub repository (with `package.json`, `wrangler.jsonc`, and `dist/` at the repository root). Do not upload `node_modules/`.
2. In Cloudflare, open Workers & Pages, create an application, and import the GitHub repository.
3. Use Worker name `curious-sudhanshu`, production branch `main`, repository root directory, no build command, and deploy command `npm run deploy`.
4. Deploy. Cloudflare supplies the public workers.dev address. Subsequent pushes to the connected production branch deploy updates automatically.

### Local deployment commands

```sh
npm ci
npm run check:deploy
npx wrangler login
npm run deploy
```

The dry run validates deployment configuration without publishing. Login and deployment use your Cloudflare account. The site itself remains plain static files and needs no runtime secrets or backend.

Deployment validation: Wrangler 4.147.0 completed `npm run check:deploy` successfully. npm audit reports a high-severity sharp/librsvg advisory inherited through the local Miniflare development tooling. Those packages are not shipped with the static site; do not use the local image-processing tooling on untrusted SVGs. The upstream advisory is https://github.com/advisories/GHSA-wq5f-xc86-pv6w.
