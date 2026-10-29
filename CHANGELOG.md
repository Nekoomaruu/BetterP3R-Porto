# Changelog

All notable changes made in this fork, compared to the upstream [Aiosssss/porto-persona3](https://github.com/Aiosssss/porto-persona3).

## Unreleased

### Fixed

- Four background videos (`bg-intro`, `bg-loop`, `about-bg`, `contact-bg`) referenced filenames that did not match what was actually in the `assets` folder, because the exported files kept a video editor suffix in their name. The videos were silently failing to load. Renamed the files so they match what `index.html` expects.

### Added

- Mobile layout support. The original stylesheet showed a "this website is not supported for your device" message on anything under 1024px wide and skipped all JavaScript initialization below that width. This fork removes that gate and adds a dedicated breakpoint at 480px covering:
  - Main menu (profile header, menu items, HUD controls)
  - Project / S.Link list screen and project cards
  - Skills page (tabs, stat bars)
  - About page (profile card, bio, quote)
  - Contact page (mail list, phone frame)
  - Loading screen
  
  Background videos keep playing and auto-cropping on mobile instead of being disabled, per the intended design direction for this fork.
- `-webkit-overflow-scrolling: touch` on the two scrollable panels (project modal body, skills list) for smoother scrolling on iOS.
- This changelog and an expanded README.

### Changed

- Replaced all portfolio content (name, bio, projects, skills, contact details) with my own. None of the original author's personal information remains in the page content.
- Updated page title, meta description, and canonical URL to reflect the new content.
- Default skill tab changed from the old "Frontend" category to "Backend", matching the reordered skill groups.

### Known issue, not yet fixed

- Fonts are still shipped as OTF (`fonts/*.otf`), which makes up about 22MB of the total page weight, more than all the background videos combined. OTF has no built-in web compression. Converting to WOFF2 would typically cut this by 50 to 70 percent with no visible quality loss.

  This wasn't done in this fork because the sandbox used to prepare these changes has no outbound network access, and WOFF2 conversion needs either an external tool or a Python package (`brotli`) that could not be installed offline.

  To do it yourself: run each file in `fonts/` through a converter such as [Transfonter](https://transfonter.org/) or [CloudConvert](https://cloudconvert.com/otf-to-woff2), replace the files, then update every `@font-face` block at the top of `css/style.css` to point at the `.woff2` file and change `format("opentype")` to `format("woff2")`.

## Upstream

Everything not listed above (layout structure, animation timing, SVG menu shapes, audio system, the overall Persona 3 Reload visual recreation) is unchanged from upstream. Credit for that work belongs to [Aiosssss](https://github.com/Aiosssss).
