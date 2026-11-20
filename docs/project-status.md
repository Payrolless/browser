# Payrolless Browser — project status

## Product

Open-source browser (MPL-2.0) rebuilding the Arc workflow from scratch: vertical sidebar tabs, Spaces, pinned and today tabs, command bar, split view, with no AI features.
Started after Arc's end of life was announced (desktop stops on 22 December 2026). Published by Payrolless, LLC.

## Environments and state

| Environment | Branch | State                                                                                                    |
| ----------- | ------ | -------------------------------------------------------------------------------------------------------- |
| dev         | `dev`  | Documentation only (feasibility, feature spec, clean-room rules, agent docs). 8 commits ahead of `main`. |
| rec         | `rec`  | Pipeline step.                                                                                           |
| prod        | `main` | Documentation only (#6). No code, no build, no release yet.                                              |

- CI: `docs.yml` checks the Markdown changed by a PR with Prettier (GitHub-hosted runner, public repository).

## Open blockers

| Blocker                                                                                            | Owner         | Since      |
| -------------------------------------------------------------------------------------------------- | ------------- | ---------- |
| Development and compilation are on hold until the product owner reopens them; no code before that. | Product owner | 2026-10-23 |
| Build machine for Chromium and macOS/iOS CI (a Mac able to compile Chromium) not decided yet.      | Product owner | 2026-10-23 |
| Final product name not chosen.                                                                     | Product owner | 2026-10-23 |

## Decisions

| Date       | Who           | Decision                                                                                                                                                                                                                                                                       |
| ---------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 2026-10-23 | Product owner | Build an open-source alternative to Arc, from scratch, under Payrolless.                                                                                                                                                                                                       |
| 2026-10-23 | Tech lead     | Chromium stable with a small rebasable patch series, Arc surfaces in Chromium WebUI (TypeScript), thin C++ hooks. Rejected: Electron (extension subset, no Web Store), WebKit (no Chrome extensions), a Firefox fork (Zen already exists), CEF. Detail: `docs/feasibility.md`. |
| 2026-10-23 | Product owner | No AI features: Arc's users are power users (#4).                                                                                                                                                                                                                              |
| 2026-10-23 | Product owner | Clean room: specs are written from observed behaviour only (`docs/clean-room.md`).                                                                                                                                                                                             |

## Contacts (roles)

- Product owner: Payrolless, LLC.
- Development and CI: Payrolless team.

## Links

- Feasibility: `docs/feasibility.md`; feature spec: `docs/feature-spec.md`; clean room: `docs/clean-room.md`

Last updated: 2026-11-20 (source: DevOps memory + git history).
