# Environments and Git workflow

- Pull requests target `dev`. Promotion: `dev` → `rec` → `main`; `main` (the default branch) is production.
- Branches: `dev` (integration), `rec` (pre-production), `main` (production).
- Infrastructure and runner configurations are managed outside the repository in DevOps documentation.
