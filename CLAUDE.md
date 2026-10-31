# Payrolless Browser

An open-source browser built from scratch to recreate the Arc browser workflow (vertical sidebar tabs, Spaces, pinned/today tabs, command bar, split view) under MPL-2.0, following Arc's shutdown announced for 22 December 2026. Targeted at power users needing Arc's UX on top of Chromium without any AI features.

## Status & Layout

Current status: Feasibility and specification phase. No browser source code, package manifests, or build scripts yet.

- `docs/clean-room.md`: Clean-room implementation rules and boundary guidelines
- `docs/feasibility.md`: Feasibility study, architecture choices, costs, and timeline
- `docs/feature-spec.md`: User-observable feature specifications across R1, R2, and R3 releases
- `LICENSE`: Mozilla Public License 2.0 (MPL-2.0)
- `README.md`: Project summary and mission statement

## Architecture (Planned)

Derived from `docs/feasibility.md`:

- Engine: Chromium stable pinned version, maintained via a minimal patch series rebased every 4 weeks.
- User Interface: Chromium internal web UI stack (TypeScript, HTML, CSS) to share code across platforms.
- Core hooks: Minimal C++ patches for window management, sidebar integration, and profile/Space routing.
- Updates: Sparkle framework on macOS; GitHub Releases.
- Target platforms: macOS 13+ on Apple silicon (R1), Windows 10/11 x64 (R2), Linux x64 (R3).

## Commands

No build system, package manifests, or CI workflows exist in the repository yet.
Commands to build, test, lint, or run will be defined once Chromium patch tooling and web UI packages are introduced.

## Domain Rules & Invariants

- Clean-room rules (`docs/clean-room.md`):
  - Never copy, disassemble, or translate Arc source code or binaries.
  - Never commit or extract Arc proprietary assets (icons, fonts, sounds, copy).
  - Never use "Arc" or "The Browser Company" as product or feature branding.
  - Features must be specified as observable behavior in `docs/feature-spec.md` prior to implementation.
- Zero AI (`docs/feature-spec.md`, git commit `1f1a7fe` on 2026-10-23):
  - No AI features, summarizers, or LLM integrations. Page content is never transmitted to any AI model.
- Licensing (`LICENSE`, `README.md`):
  - All project files licensed under MPL-2.0. Underlying Chromium components retain their BSD-style license.
- Release milestones (`docs/feature-spec.md`):
  - R1: Core workflow (sidebar, Spaces, pinned tabs, today tabs auto-archive, command bar, split view, quick window, Arc import).
  - R2: Parity (peek, link routing, picture-in-picture, site styles, ad/tracker blocker, Windows support).
  - R3: Extras (end-to-end encrypted sync, notes, canvas, Linux support, AppleScript).

## Gotchas

- Chromium rebase cost: Never maintain a permanent fork; keep changes isolated as rebasable patches to absorb 4-week upstream Chromium security updates (`docs/feasibility.md`).
- macOS build requirements: Clean macOS Chromium builds require a high-spec dedicated Mac runner with large disk and memory; cannot build on standard developer laptops or free CI runners (`docs/feasibility.md`).
- Account requirement: The browser must remain fully functional without requiring user account creation or login (`docs/feature-spec.md`).

## Environments & Git Workflow

- Branches: `dev` (integration), `rec` (pre-production), `main` (production).
- Infrastructure and runner configurations are managed outside the repository in DevOps documentation.
