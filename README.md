# morsheded.github.io

Personal site — https://morsheded.github.io

Single static page, no build step and no framework. Edit `index.html`, push to `main`,
Pages redeploys automatically.

## Before it's finished

Replace the two placeholders in `index.html`:

- `REPLACE_EMAIL` — contact address (appears twice: the `mailto:` and the visible link text)
- `REPLACE_LINKEDIN` — LinkedIn profile slug

## How it works

| Piece | Notes |
|---|---|
| Particle field | three.js `Points` with a custom GLSL shader. 40k points on desktop, 14k on phones. Three formations (sphere, wave, helix) are stored as vertex attributes and the shader lerps between them from a single `uMorph` uniform. |
| Scroll choreography | GSAP ScrollTrigger scrubs `uMorph`, the camera z, the scrim opacity and a `uFade` uniform that drops the field back so body copy stays readable. |
| Smooth scroll | Lenis, wired into the GSAP ticker so ScrollTrigger stays in sync. |
| Kinetic headline | Split per character, each word masked with `overflow:hidden` so the reveal works no matter where lines wrap. |
| Cursor | Dot tracks the pointer directly, ring lerps behind it. Hidden on coarse pointers. |

`prefers-reduced-motion` renders one static frame, skips Lenis and every reveal, and
stops the render loop entirely.

## Custom domain

Add a `CNAME` file containing the bare domain, then point a CNAME record at `morsheded.github.io`.
