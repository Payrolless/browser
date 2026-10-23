# Clean-room rules

We rebuild what Arc did for its users. We never reuse how Arc did it. Each contribution follows these rules, and a review rejects any change that breaks them.

## Allowed sources

- Using Arc as a normal user and describing what it does on screen.
- Public material: Arc's help centre, release notes, keyboard shortcut lists, press coverage, public talks and blog posts by The Browser Company.
- Facts published by Arc itself in its application metadata (for example, the Chromium version it embeds or the AppleScript commands it exposes), stated as facts and not reproduced as files.
- File formats a user's own Arc data is stored in, read only to import that user's data into this browser (interoperability).
- Chromium, its documentation, and other open-source browsers under compatible licences, with attribution.

## Forbidden

- Copying, translating or paraphrasing Arc source code, decompiled code, pseudocode or disassembly.
- Shipping or redrawing Arc assets: icons, logos, sounds, animations, videos, fonts licensed to Arc, illustrations, onboarding copy.
- Using the names "Arc" or "The Browser Company" as a product name, a domain or a feature brand.
- Committing anything extracted from an Arc installer or binary.

## Specifications come first

A feature is built from a behaviour description in [feature-spec.md](feature-spec.md), written from the allowed sources. The person or agent who implements a feature works from that description, not from Arc's internals.
