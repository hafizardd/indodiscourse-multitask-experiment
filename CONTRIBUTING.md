# Contributing

## Branches

Create a short-lived branch from `main`:

- `feat/<topic>` for a capability.
- `fix/<topic>` for a correction.
- `exp/<topic>` for an experiment run or configuration change.
- `docs/<topic>` for documentation.
- `chore/<topic>` for repository maintenance.

Do not push directly to `main`. Open a Pull Request and wait for the repository
checks to pass. Keep each PR focused; squash-merge it and delete the branch.

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

## Pull Requests

Fill in the PR template. Include the dataset and model revisions, experiment
configuration, checks run, and any result artifacts. Do not commit raw data,
personal credentials, `.env` files, model checkpoints, or generated result
directories.

For changes to the experiment protocol, explain how the change relates to the
proposal and whether it changes the interpretation of the comparison.
