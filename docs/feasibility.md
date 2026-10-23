# Feasibility study

Date: 23 October 2026.

## Verdict

Feasible. Everything Arc did can be rebuilt on open-source parts. The interface (sidebar, Spaces, command bar, split view) is the easy part. The hard part is the one that made The Browser Company stop: shipping a Chromium-based browser and keeping it patched against security fixes every few weeks. This study plans for that cost from day one.

## Context

- Arc stopped receiving new features in May 2025. Its maker moved to Dia, an AI browser, and was acquired by Atlassian in 2025.
- On 22 October 2026 the company announced the end of Arc: new accounts closed that day, mobile sign-in and sync stop on 23 November 2026, and the desktop browser stops working on 22 December 2026. The company cites the cost of keeping a browser secure.
- Arc's code was never published. Its users need somewhere to go before 22 December.

## What Arc is made of

From the application's own public metadata (Arc 1.170.0, released 21 October 2026):

- Engine: Chromium 156, embedded through Arc's own closed-source framework.
- Interface: a native macOS application, Apple silicon and Intel, macOS 13 or later.
- Account and sync: Google Firebase.
- Updates: Sparkle, the open-source macOS update framework.
- Scripting: AppleScript commands for windows, Spaces and tabs.

Arc's approach was a native interface on top of a privately embedded Chromium. That gave it its polish, and it is also why each Chromium update was costly for Arc to absorb.

## Existing open-source alternatives

| Project | Engine | Licence | Fit with Arc |
|---|---|---|---|
| Zen | Firefox | MPL-2.0 | Closest today, with workspaces and split view. Firefox extensions only, no Chrome Web Store. |
| Stedding | Chromium 156 | BSD-3-Clause | New (August 2026), Arc-style sidebar and Spaces, beta, one maintainer. Same architecture as recommended here. |
| Helium | Chromium | GPL-3.0 | Privacy-focused, vertical tabs experiment, no Spaces model. |
| Brave | Chromium | MPL-2.0 | Vertical tabs, no Spaces model, crypto and ads features. |

The gap: no mature project combines Chromium (so Chrome extensions and site compatibility work as in Arc) with Arc's full workflow.

## Engine options

| Option | Chrome extensions | Platforms | Security updates | Effort | Verdict |
|---|---|---|---|---|---|
| Chromium with a patch series (the approach of Brave, Stedding, ungoogled-chromium) | Full, including the Web Store | macOS, Windows, Linux | Follow Chromium stable, rebase every 4 weeks | High | **Recommended** |
| Electron shell | A subset of the extension APIs, no Web Store | macOS, Windows, Linux | Lag behind Chromium by weeks | Medium | Rejected: extensions are a switching blocker for Arc users |
| Native WebKit app (Safari's engine) | None from Chrome | macOS only | Follow macOS | Medium | Rejected: no Chrome extensions, no Windows |
| Firefox fork | Firefox extensions only | All | Follow Firefox | High | Rejected: Zen already fills this place |
| Chromium Embedded Framework | Almost none | All | Lag behind Chromium | High | Rejected |

## Recommended architecture

1. **Chromium stable**, pinned to a version, with our changes kept as a small, documented series of patches applied on top. No permanent fork of the Chromium tree.
2. **Interface in Chromium's own web UI technology** (TypeScript, HTML, CSS) for the sidebar, Spaces, command bar and settings. One code base for every platform, written in a language our team already uses.
3. **Thin C++ patches** only where the web UI needs a hook into the browser: removing the horizontal tab strip, the sidebar container, split view layout, the quick window, Space and profile wiring.
4. **Data** in the Chromium profile (Spaces, pinned tabs, folders as a profile-level store), so import, backup and future sync work on one format.
5. **Updates** through Sparkle on macOS and GitHub Releases, signed builds only.
6. **AI features** off by default, through the provider the user configures.

Rebasing a small patch series onto a new Chromium every four weeks is routine work. Keeping a private embedding framework in step, as Arc did, is not.

## Build and release infrastructure

| Need | Why | Option |
|---|---|---|
| macOS build machine | Chromium for macOS builds only on a Mac. The source checkout alone takes tens of gigabytes and a clean build takes hours, so the machine needs a large disk and plenty of memory. GitHub's free macOS runners are too small, and the team laptop (16 GB) must stay free for its owner. | A dedicated Mac mini, M4 Pro, 48 GB, 1 TB, connected as a self-hosted GitHub runner |
| Apple Developer Program | Signing and notarisation, without which macOS blocks the download | Annual membership |
| Windows build (R2) | Windows builds | Cross-build from Linux, or a Windows host, decided at R2 |
| Windows code signing (R2) | SmartScreen warnings otherwise | SignPath Foundation, free for open-source projects |
| Release hosting and update feed | Downloads and automatic updates | GitHub Releases and GitHub Pages, free |
| Security rebase | Chromium ships a stable release every 4 weeks and security fixes in between | A scheduled job opens a rebase branch on each new stable; a build and test run gates the release |

## Cost

| Item | Kind | Amount |
|---|---|---|
| Mac mini M4 Pro, 48 GB, 1 TB | One-off hardware | About 2,300 € (to confirm at purchase) |
| Apple Developer Program | Yearly | 99 USD |
| SignPath Foundation (R2) | Free for open source | 0 |
| GitHub public repository, Actions on our own runner, Releases, Pages | Free | 0 |
| AI features | Paid by each user through their own provider key | 0 |
| Sync server (R3) | Runs on existing servers | 0 extra |

## Effort and timeline

Assumes AI coding agents write most of the code, reviewed by the team, with the Mac build machine in place.

| Step | Content | Duration |
|---|---|---|
| 0. Build chain | Fetch, patch and build Chromium stable on the Mac runner; signed, notarised, auto-updating "hello" build | 2 weeks |
| R1. macOS beta | Sidebar, pinned and today tabs with auto-archive, folders, Spaces with themes and profiles, command bar, split view, quick window, import from Arc and other browsers, Chrome Web Store | 6 to 8 weeks after step 0 |
| R2. Parity | Peek, link routing, picture in picture, media controls, site styles, content blocker, capture, AI features, Windows | 8 to 10 weeks after R1 |
| R3. Extras | Encrypted sync, notes, canvas, Linux, AppleScript | Later |

A beta before 22 December 2026 is possible only if the Mac build machine is running within one week and R1 is cut to sidebar, Spaces, pinned tabs and import from Arc. The realistic R1 date is mid-January 2027. Arc users who leave in December will move to Zen, Stedding or Dia first. The import from Arc must also read Arc data exported before its shutdown, so they can still switch later.

## Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Security update cadence | A browser that falls behind Chromium is dangerous | Small patch series, automated rebase, release blocked when a rebase fails |
| Build time | Slow feedback on C++ changes | Incremental builds and a build cache on the Mac runner; web UI work needs no Chromium rebuild |
| Google services | Google restricts its sync, Safe Browsing and translation keys for third-party Chromium builds | Ship without Google sync; apply for Safe Browsing access; use our own sync |
| Arc trademark and assets | Legal claims | [Clean-room rules](clean-room.md), no Arc name or assets |
| Competition | Zen and Stedding are ahead | Chromium plus Chrome Web Store plus full Arc workflow plus import from Arc is a combination none of them has completed |
| Single maintainer burnout | Project stalls | Public roadmap, contributor guide, patches small enough to review |

## Next steps

1. Buy and connect the Mac build machine; enrol in the Apple Developer Program.
2. Step 0: reproducible Chromium stable build with an empty patch series, signed and notarised.
3. Write the Arc import first, against Arc's on-disk sidebar data, while Arc still runs.
4. R1 features in the order of the specification.
