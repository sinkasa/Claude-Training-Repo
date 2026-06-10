# Claude-Training-Repo

A single-page investment strategy / financial advisory landing page built with plain HTML, CSS, and JavaScript — no frameworks, build tools, or dependencies.

🔗 **Live site:** Deployed automatically via GitHub Pages on every push to `main`.

## Overview

`index.html` is a fully self-contained marketing/landing page for an investment advisory service ("Build a Smarter Investment Strategy for Long-Term Wealth Growth"). It includes:

- A hero section with headline, CTAs, and trust badges
- A "Why Us" benefits grid
- A 4-step process timeline
- Client testimonials
- A free checklist lead magnet
- An enquiry/contact form
- An FAQ accordion
- A final call-to-action banner and footer

## Tech Stack

- **HTML** — semantic markup, organized as sequential `<section>` elements inside `<main>`
- **CSS** — embedded in a `<style>` block, themed via CSS custom properties (`:root` variables)
- **JavaScript** — embedded in a single `<script>` block at the bottom of the page (no modules, no build step)
- **Form handling** — [FormSubmit](https://formsubmit.co/) (no backend required)

## Project Structure

```
.
├── index.html              # The entire site (HTML + CSS + JS)
├── .github/
│   └── workflows/           # GitHub Actions workflow for GitHub Pages deployment
├── CLAUDE.md                 # Guidance notes for Claude Code when editing this repo
└── README.md
```

## Page Sections

| # | Section ID      | Description                                              |
|---|------------------|-----------------------------------------------------------|
| 1 | `#hero`          | Headline, CTA buttons, trust badges                       |
| 2 | `#why-us`        | Six benefit cards                                         |
| 3 | `#process`       | Four-step timeline (desktop) / stacked cards (mobile)     |
| 4 | `#testimonials`  | Three testimonial cards                                   |
| 5 | `#lead-magnet`   | Free checklist offer, scrolls to `#enquiry`               |
| 6 | `#enquiry`       | Lead form (FormSubmit integration)                        |
| 7 | `#faq`           | Accordion FAQ                                             |
| 8 | `#final-cta`     | Closing conversion banner                                 |
| 9 | footer           | Contact info, social links, disclaimer                    |

## Styling

All theme colors, spacing, and layout tokens are defined as CSS custom properties in `:root`:

- `--primary`, `--secondary`, `--accent`
- `--background`, `--text`, `--light-bg`
- `--max-width`, `--transition`

To restyle the site, update these variables rather than hardcoding new values throughout the stylesheet.

Responsive breakpoints:

- `1023px` — switches the process timeline layout
- `768px` — mobile navigation
- `480px` — form column stacking

## JavaScript Features

- Sticky navbar on scroll
- Mobile menu toggle
- Smooth-scroll for in-page anchor links
- Scroll-triggered fade-in animations via `IntersectionObserver`
- FAQ accordion with animated expand/collapse
- Client-side form validation (name, email, phone) on blur/input/submit, with inline success/error messages
- Dynamic footer copyright year

## Lead Form / FormSubmit Setup

The enquiry form submits directly to [FormSubmit](https://formsubmit.co/) — there is no backend or server required.

1. The form's `action` attribute points to `https://formsubmit.co/<your-email>` (see `index.html`, near the `#enquiry` section).
2. The first submission triggers a one-time confirmation email to that address — you must confirm it before FormSubmit will deliver subsequent submissions.
3. Hidden fields (`_subject`, `_captcha`, `_template`) configure the email subject, disable the captcha, and set the email template.

## Local Development

There is no build step, package manager, or dev server.

```bash
open index.html
```

Or simply double-click `index.html` to open it in your browser. Edit the file and refresh to see changes.

## Deployment

This repo deploys automatically to **GitHub Pages** via the workflow in `.github/workflows/`:

- Triggers on every push to `main` (or manually via `workflow_dispatch`)
- Uploads the repository root as a Pages artifact and deploys it

To enable Pages for this repo (one-time setup): go to **Settings → Pages** and set the source to **GitHub Actions**.

## Constraints / Conventions

- Keep everything in the single `index.html` file — no frameworks, build tools, or external libraries (no React/Vue/Angular/Bootstrap/Tailwind/jQuery).
- No backend — form submissions are handled entirely by FormSubmit.
- Use the existing `:root` CSS variables for theming instead of hardcoding new colors.

See `CLAUDE.md` for more detailed guidance on the codebase architecture.
