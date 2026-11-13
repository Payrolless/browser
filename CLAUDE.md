# Payrolless Browser

An open-source browser built from scratch to recreate the Arc browser workflow (vertical sidebar tabs, Spaces, pinned/today tabs, command bar, split view) under MPL-2.0, following Arc's shutdown announced for 22 December 2026. Power users get Arc's UX on Chromium with no AI features.

## Stack (planned)

Chromium stable with minimal rebasable patches; UI in Chromium web UI (TypeScript, HTML, CSS); thin C++ hooks. Updates via GitHub Releases (all platforms) and Sparkle on macOS. Details in `docs/feasibility.md`.

## Layout

Feasibility and specification phase. No browser source, package manifests, or build scripts yet.

- `docs/clean-room.md`: clean-room implementation rules and boundary guidelines
- `docs/feasibility.md`: feasibility study, architecture choices, costs, and timeline
- `docs/feature-spec.md`: observable feature specifications for R1, R2, and R3
- `LICENSE` (MPL-2.0), `README.md`
- `.github/workflows/docs.yml` (Markdown check on pull requests)

## Absolute rules

- Clean-room (`docs/clean-room.md`): never copy, disassemble, decompile, translate or paraphrase Arc source code or binaries; never commit or extract anything from an Arc installer; never ship or redraw Arc proprietary assets (icons, logos, fonts, sounds, copy); never use "Arc" or "The Browser Company" as product name, domain, or feature branding; specify observable behaviour in `docs/feature-spec.md` before implementation.
- Zero AI (`docs/feature-spec.md`): no AI features, summarizers, or LLM integrations; page content is never transmitted to any AI model.
- Licensing (`LICENSE`, `README.md`): MPL-2.0 for project files; Chromium components keep their BSD-style licence.
- The browser must work fully without account creation or login (`docs/feature-spec.md`).
- Chromium changes stay rebasable patches, not a permanent fork (`docs/feasibility.md`).

## Git and release flow

Pull requests target `dev`. Promotion: `dev` → `rec` → `main`; `main` (the default branch) is production.

## Commands

No install, build, test, lint, or run targets yet; only the Markdown check below.

Docs check (job `docs` in `.github/workflows/docs.yml`). Set `BASE_REF` to the PR base branch (usually `dev`):

```sh
set -e
: "${BASE_REF:?set BASE_REF to the PR base (e.g. dev)}"
git fetch origin "$BASE_REF"
CHANGED_MD=$(mktemp)
trap 'rm -f "$CHANGED_MD"' EXIT
git diff --name-only -z --diff-filter=ACMR "origin/$BASE_REF" HEAD -- '*.md' > "$CHANGED_MD"
if [ ! -s "$CHANGED_MD" ]; then echo "No changed Markdown file."; exit 0; fi
xargs -0 npx --yes prettier@3.9.6 --no-config --no-error-on-unmatched-pattern --check < "$CHANGED_MD"
```

## Detailed docs

- `docs/agents/architecture.md`: read before engine, UI stack, platform, or update choices.
- `docs/agents/domain-rules.md`: read before features, licensing, branding, or release scope.
- `docs/agents/gotchas.md`: read before Chromium rebases, macOS builds, or account assumptions.
- `docs/agents/git-workflow.md`: read before branch or external infrastructure assumptions.
