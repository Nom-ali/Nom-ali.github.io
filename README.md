# Rana Nauman — Unity Game Developer Portfolio

A lightweight, buildless portfolio for Android, iOS, PC, and WebGL, prepared for GitHub Pages. No package installation or build step is required. The hero playground uses native Canvas and is clearly labeled as portfolio UI; it is not presented as a released Unity game.

## Publish on GitHub Pages

1. Create a public repository named `Nom-ali.github.io` on the Nom-ali account. If it already exists, inspect its contents before changing anything.
2. Upload the root project files to branch `main`.
3. Open repository **Settings → Pages → Build and deployment → Source → Deploy from a branch**. Select branch **main**, folder **/(root)**, and save.
4. After the Pages deployment succeeds, the site is hosted at `https://nom-ali.github.io/`.

The downloadable source package also includes an optional GitHub Actions workflow if you prefer an explicit deployment pipeline; select GitHub Actions as the Pages source when using it.

A project repository also works: relative assets support `https://nom-ali.github.io/repository-name/` without changes. The `.openai` file is only for development preview and is not included in the deployment artifact. No Sites hosting is configured.

## Add real content

Edit `content.js`. The projects, experience, and repository lists are intentionally empty, because the brief did not provide verified examples. The public name and contact email come from the connected GitHub profile. Review the email before publishing if you prefer another address.

Each project accepts:

- A unique `id`, `title`, `description`, and `platforms` array. Supported labels: `Android`, `iOS`, `PC`, `WebGL`. One game may use several labels.
- `featured: true` sorts a game ahead of other games.
- `cover`, `screenshots` (image paths under `assets/` or HTTPS URLs).
- `trailerUrl` (HTTPS MP4/WebM for a video player, or another HTTPS video page for an external trailer link).
- `features` and `contributions` arrays of strings. Include only accurate descriptions of your own work.
- `links.android` (Google Play app URL with an id), `links.ios` (App Store app URL), `links.pc`, `links.webgl`, and `links.repository`.
- `embedUrl` (HTTPS Unity WebGL index page on a separately hosted service that allows embedding).

Only links supplied in the data are rendered. Google Play and App Store links are checked for the expected URL format. Verify destination existence and that each URL belongs to the relevant game before adding it. Missing media is handled with a visible fallback. Remote media hosts must permit access.

Set `resumeUrl` to `assets/resume.pdf` or an HTTPS URL. The resume button is hidden while this value is empty. Set `about` to replace the default introduction. Experience entries take `role`, `organization`, `period`, and `description`. Repository entries take `name`, `description`, `url`, and `language`. No visitor requests to the GitHub API are made.

The skills section uses only the focus areas requested in the brief, without proficiency ratings, years, or unverified libraries. Edit it to reflect actual skills before publishing.

## Unity WebGL hosting

Keep game builds outside this portfolio when practical, so visiting the site does not download them. The iframe is created only after the visitor presses Play and is removed on close. Loading and fallback UI, a timeout, retry, fullscreen, and an external-open link are included. HTTPS is required. The game host must allow framing; `X-Frame-Options` and CSP `frame-ancestors` restrictions can block it. Compressed Unity builds need correct `Content-Type` and `Content-Encoding` headers. Threaded builds may need cross-origin isolation, so host those separately and prefer opening in a new tab when embedding is incompatible.

Cross-origin iframe `load` means the page loaded, not that Unity initialized. Browsers cannot reliably expose blocked framing or internal Unity errors to the parent. The player includes a delayed recovery overlay, and optional bridge events allow the game page to report true readiness and errors. See `unity-bridge.md`.

Some mobile devices may not support a particular Unity build or fullscreen. A working desktop build does not guarantee mobile compatibility. Test each actual build on target devices before listing it as playable.

## Local development

Serve the root directory over HTTP, for example `python3 -m http.server 8000`, then open localhost:8000. No npm packages are required. Google Fonts are optional remote requests; local system fonts remain available if they fail. All other default artwork is native SVG, CSS, or Canvas. Motion follows the OS preference and has an explicit pause control. The site has no analytics, fake activity counters, contact backend, or tracking cookies.
