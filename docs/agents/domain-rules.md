# Domain rules and invariants

- Clean-room rules (`docs/clean-room.md`):
  - Never copy, disassemble, decompile, translate or paraphrase Arc source code or binaries.
  - Never commit or extract anything from an Arc installer; never ship or redraw Arc proprietary assets (icons, logos, fonts, sounds, copy).
  - Never use "Arc" or "The Browser Company" as product name, domain, or feature branding.
  - Features must be specified as observable behavior in `docs/feature-spec.md` prior to implementation.
- Zero AI (`docs/feature-spec.md`, git commit `1f1a7fe` on 2026-10-23):
  - No AI features, summarizers, or LLM integrations. Page content is never transmitted to any AI model.
- Licensing (`LICENSE`, `README.md`):
  - All project files licensed under MPL-2.0. Underlying Chromium components retain their BSD-style license.
- Release milestones (`docs/feature-spec.md`):
  - R1: Core workflow (sidebar, Spaces, pinned tabs, today tabs auto-archive, command bar, split view, quick window, Arc import).
  - R2: Parity (peek, link routing, picture-in-picture, site styles, ad/tracker blocker, Windows support).
  - R3: Extras (end-to-end encrypted sync, notes, canvas, Linux support, AppleScript).
