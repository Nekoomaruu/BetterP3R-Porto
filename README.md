# Nekomaru Portfolio (Persona 3 Reload style)

This is a fork of [Aiosssss/porto-persona3](https://github.com/Aiosssss/porto-persona3), a pixel-perfect recreation of the Persona 3 Reload pause menu built with plain HTML, CSS, and JavaScript. No frameworks, no build step.

The original is a great piece of UI work. This fork keeps the same visual style and interaction design, but reworks the content to be my own portfolio and fixes a few things that bothered me in the original version, mainly page weight and mobile support.

## What this fork changes

- **Content**: all text, projects, skills, and contact info now reflect my own background instead of the original author's.
- **Mobile support**: the original blocked anything under 1024px with a "not supported" screen. This fork adds an actual responsive layout for phones instead of refusing to render.
- **Smaller file size**: fixed a video naming bug that broke four background videos, and flagged the fonts (which make up most of the page weight) for further optimization.

See `CHANGELOG.md` for the full list of changes with more detail.

## Structure

```
index.html        Markup for all four sections (menu, project, skills, about, contact)
css/style.css     All styling, including the new mobile breakpoint at the bottom
js/main.js        Page logic, animations, audio, and the content data arrays
assets/           Background videos, profile photo, favicon
fonts/            Six Rodin/Skip Std OTF fonts used across the UI
sfx/              Menu navigation sound effects
```

Project, skill, and contact content is not hardcoded in the HTML. It lives in a few arrays near the top of `js/main.js`:

- `options` the four main menu cards (Project, Skills, About, Contact) and their summary modal content
- `slinkData` the numbered project list on the Project page
- `skillTabsList` / `skillGroupsData` the skill categories and bars on the Skills page

Editing those arrays is enough to change the portfolio content without touching the HTML or CSS.

## Running it locally

No build step needed. Any static file server works:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

## Known limitations

- Fonts are still in OTF format (about 22MB combined). Converting them to WOFF2 would cut that significantly. See the note in `CHANGELOG.md` for how to do this yourself.
- Background videos autoplay and loop continuously, including on mobile. This is a deliberate choice to keep the visual style, but it does mean mobile data usage is higher than a typical static portfolio.
- The site is demo content. Social links (LinkedIn, Ko-fi, Trakteer) are left as placeholders since this isn't a live deployment.

## Credits

Original concept, layout, and animation work by [Aiosssss](https://github.com/Aiosssss). This fork only changes the content and adds mobile support plus a few optimizations on top of that foundation.
