# Payrolless Browser

An open-source browser built from scratch to offer what the Arc browser offered: tabs in a sidebar, Spaces, pinned and self-archiving tabs, a command bar, split view, quick windows for links, and per-site customisation.

The Browser Company is shutting Arc down on 22 December 2026. Arc was never open source, so nobody can carry its code forward. This project rebuilds the same way of browsing in the open, under a licence that keeps it open.

> Working name. The final product name will be chosen before the first public release.

## Status

Feasibility and specification. No browser code yet.

- [Feasibility study](docs/feasibility.md): engine choice, architecture, effort, costs, risks
- [Feature specification](docs/feature-spec.md): what Arc users rely on, as observable behaviour, with the scope of the first release
- [Clean-room rules](docs/clean-room.md): how we rebuild the features without copying anything from Arc

## What this project is not

- Not affiliated with, endorsed by or connected to The Browser Company or Atlassian. "Arc" is their trademark and is used here only to describe the browser we replace.
- Not a fork, a decompilation or a copy of Arc. Nothing from Arc ships here: no code, assets, icons, fonts or text. See [clean-room rules](docs/clean-room.md).

## Licence

[Mozilla Public License 2.0](LICENSE). Every file stays open: anyone who ships a modified file must publish that file's source. The browser engine underneath, Chromium, keeps its own BSD-style licence.
