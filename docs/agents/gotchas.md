# Gotchas

- Chromium rebase cost: Never maintain a permanent fork; keep changes isolated as rebasable patches to absorb 4-week upstream Chromium security updates (`docs/feasibility.md`).
- macOS build requirements: Clean macOS Chromium builds need a dedicated Mac runner with a large disk and plenty of memory: GitHub's free macOS runners are too small and the team laptop (16 GB) must stay free for its owner (`docs/feasibility.md`).
- Account requirement: The browser must remain fully functional without requiring user account creation or login (`docs/feature-spec.md`).
