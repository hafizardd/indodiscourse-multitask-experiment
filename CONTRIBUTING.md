# Contributing

## Branches

Create a short-lived branch from `main`:

- `feat/<topic>` for a capability.
- `fix/<topic>` for a correction.
- `exp/<topic>` for an experiment run or configuration change.
- `docs/<topic>` for documentation.
- `chore/<topic>` for repository maintenance.

Do not push directly to `main`. Open a Pull Request and wait for the repository
checks to pass. Keep each PR focused and delete its branch after merging.

## Git workflow

Start from the latest `main` and create a short-lived topic branch:

```bash
git switch main
git pull --ff-only origin main
git switch -c feat/your-topic
```

Commit each small, logically complete modification separately. Review the staged
diff before each commit, then push the branch and open a Pull Request:

```bash
git add -p
git diff --cached
git commit -m "feat(data): describe the change"
git push -u origin feat/your-topic
```

Replace `your-topic` and the example commit message with names that describe
the change.

After the required checks pass and review is complete, merge with GitHub's
**Rebase and merge** option. This keeps `main` linear and preserves the focused
commits as separate commits. The repository also permits **Squash and merge**,
which combines a PR's commits into one; use it only when that combined history is
intended. Merge commits are disabled for this repository.

## Commit messages

Use Conventional Commits, in English:

```text
<type>(<scope>): <imperative subject>
```

Use a lowercase subject of at most 72 characters, with no final period. Example
messages:

```text
feat(data): validate the pinned IndoDiscourse snapshot
feat(model): add the shared encoder multitask head
exp(kaggle): add resumable fold and seed runs
docs(data): explain upstream dataset access
```

Use one logical change per commit. Common types are `feat`, `fix`, `docs`,
`data`, `exp`, `refactor`, `test`, and `chore`.

Commit each small, logically complete modification before starting an
independent one. Keep each commit limited to the files needed for that change,
so reviewers can understand its purpose from the diff. A change may touch
multiple files when they form one coherent unit; split independent changes into
separate commits instead of bundling them into one large commit. These commits
are intended to remain separate through **Rebase and merge**.

## Pull Requests

Fill in the PR template. Include the dataset and model revisions, experiment
configuration, checks run, and any result artifacts. Do not commit raw data,
personal credentials, `.env` files, model checkpoints, or generated result
directories.

For changes to the experiment protocol, explain how the change relates to the
proposal and whether it changes the interpretation of the comparison.
