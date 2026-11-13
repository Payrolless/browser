# Architecture (planned)

Derived from `docs/feasibility.md`:

- Engine: Chromium stable pinned version, maintained via a minimal patch series rebased every 4 weeks.
- User Interface: Chromium internal web UI stack (TypeScript, HTML, CSS) to share code across platforms.
- Core hooks: Minimal C++ patches for window management, sidebar integration, and profile/Space routing.
- Updates: Sparkle framework on macOS; GitHub Releases.
- Target platforms: macOS 13+ on Apple silicon (R1), Windows 10/11 x64 (R2), Linux x64 (R3).
