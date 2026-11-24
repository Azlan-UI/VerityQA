# Contributing to VerityQA

Repository: https://github.com/Azlan-UI/VerityQA.git
Default branch: `main`

## Team ownership

| Member | GitHub | Commit identity | Owned area | Branch |
| --- | --- | --- | --- | --- |
| Anshara Zahoor | `Anshara01` | Anshara Zahoor \<ansharazahoor9@gmail.com\> | `client/**` (React frontend, routing, components, layouts, Context API, API client, validation, responsive UI) | `feature/frontend` |
| Muhammad Hasnat | `hasnat-456` | Muhammad Hasnat \<hasnatmuhammad718@gmail.com\> | `server/src/database/**` and each feature module's `entities/` folder, migrations, seeds, ERD/database docs | `feature/database` |
| Azlan Zafar | `Azlan-UI` | Azlan Zafar \<azlant231@gmail.com\> | `server/src/modules/**` (excluding entity files), controllers, services, DTOs, guards, jobs, backend integrations, REST API | `feature/backend` |

Shared root files, cross-module configuration, `server/src/common/**`, `server/src/config/**`, and CI require coordination among all three owners and must not be attributed arbitrarily.

## Git workflow

1. `main` is stable. After the initial bootstrap, never commit directly to it.
2. Work only on your ownership branch: `feature/frontend`, `feature/database`, `feature/backend`.
3. Before switching branches, run `git status --short` and confirm the working tree is clean.
4. Commit after a logically complete, verified unit of work — not once at the end of the project.
5. Open a pull request from your ownership branch to `main`; another member must review it.
6. Integration order: database foundations → backend implementation → frontend implementation.
7. Rebase/merge `main` into your branch before opening a PR; resolve conflicts only in files you own, coordinating on shared files.
8. Never force-push or delete `main`. Preserve merge commits so member authorship is retained.

## Commit authorship

Use each member's real name and verified email with per-command Git configuration. Never change global Git identity.

```powershell
git -c user.name="Anshara Zahoor" -c user.email="ansharazahoor9@gmail.com" commit -m "feat(frontend): implement protected application routing"
git -c user.name="Muhammad Hasnat" -c user.email="hasnatmuhammad718@gmail.com" commit -m "feat(database): add user and project entities"
git -c user.name="Azlan Zafar" -c user.email="azlant231@gmail.com" commit -m "feat(backend): implement authentication endpoints"
```

Only use a member's identity for work they reviewed and accepted. No empty commits, artificial contribution commits, backdating, or identity changes after the fact.

## Commit messages

Conventional prefixes: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`. Include a scope where useful, e.g. `feat(database)`, `fix(backend)`, `feat(frontend)`.

Examples:
- `feat(database): implement user and project entities`
- `feat(backend): implement authentication endpoints`
- `feat(frontend): integrate project dashboard APIs`
- `fix(backend): correct project ownership authorization`

## Collaboration rules

- Backend needing a new entity or schema change coordinates with the database owner; do not create conflicting entity definitions.
- Frontend needing a new API endpoint coordinates with the backend owner and follows the documented contract.
- Shared/root files require coordination and explicit approval from affected owners.
- Keep commits scoped to the owning area; do not mix changes across branches.

## Testing before commit

Run the checks appropriate to the change (lint, typecheck, unit tests, e2e/API tests, migration up/down once tooling exists). Do not commit broken work. Document exact commands here when the project scaffold is established.

## Security

Never commit `.env`, tokens, passwords, personal access tokens, private SSH keys, or secrets. `.gitignore` excludes these; use `.env.example` for non-sensitive templates. No personal credentials belong in documentation.

## Authentication for pushes

No SSH identities are configured, so use HTTPS with Git Credential Manager. Force the correct account with a username-qualified URL, for example:

```powershell
git push https://Anshara01@github.com/Azlan-UI/VerityQA.git feature/frontend
```

Each member must authenticate as themselves; do not pretend a push was authenticated as another account.
