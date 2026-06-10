# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a single-page investment strategy / financial advisory landing page: `index.html`. It is a static, self-contained file with embedded CSS (in `<style>`) and vanilla JavaScript (in `<script>`) — there is no build step, package manager, bundler, or test suite.

## Constraints

- Everything must stay in the single `index.html` file (HTML, CSS, and JS embedded). Do not introduce frameworks, build tools, or external libraries (no React/Vue/Angular/Bootstrap/Tailwind/jQuery).
- No backend — the enquiry form posts directly to FormSubmit (`https://formsubmit.co/<email>`).

## Running / Previewing

There is no dev server or build command. Open `index.html` directly in a browser to preview changes.

## Architecture

The page is organized as nine sequential `<section>` elements inside `<main>`, each with its own id used for nav/anchor links and scroll targets:

1. `#hero` — headline, CTA buttons, trust badges
2. `#why-us` — six benefit cards
3. `#process` — four-step timeline (desktop) / stacked cards (mobile)
4. `#testimonials` — three testimonial cards
5. `#lead-magnet` — free checklist offer, CTA scrolls to `#enquiry`
6. `#enquiry` — lead form (FormSubmit integration, hidden `_subject`/`_captcha`/`_template` fields)
7. `#faq` — accordion FAQ
8. `#final-cta` — closing conversion banner
9. footer — contact info, social links, disclaimer

CSS:
- All theme colors/spacing live in `:root` CSS variables (`--primary`, `--secondary`, `--accent`, `--background`, `--text`, `--light-bg`, `--max-width`, `--transition`) — change these rather than hardcoding new colors.
- Responsive breakpoints at `1023px`, `768px`, and `480px` handle the timeline layout switch, mobile nav, and form column stacking.

JavaScript (single `<script>` block at the bottom, no modules):
- Sticky navbar on scroll, mobile menu toggle, smooth-scroll for in-page anchors.
- `IntersectionObserver` drives `.fade-in` → `.visible` scroll animations.
- FAQ accordion toggles `.active` and animates `max-height`.
- Form validation for name/email/phone runs on blur/input and on submit (shows `.form-status` success/error messages); valid submissions proceed to FormSubmit.
- Footer copyright year is set dynamically via `currentYear`.

## Notes

- The enquiry form's FormSubmit `action` email address (`index.html` ~line 1212) is the lead delivery destination — FormSubmit requires a one-time confirmation email to that address before submissions are delivered.
