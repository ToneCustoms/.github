# Reusable GitHub Actions

ToneCustoms maintains reusable workflows in this organization repository so resource repositories can share the same baseline checks without hosting runners or duplicating workflow code.

## Lua syntax validation

Workflow:
`.github/workflows/lua-validation.yml`

Add a caller workflow to a FiveM resource repository at `.github/workflows/lua-validation.yml`:

```yaml
name: Resource Validation

on:
  push:
  pull_request:

permissions:
  contents: read

jobs:
  lua:
    uses: ToneCustoms/.github/.github/workflows/lua-validation.yml@main
    with:
      lua-version: '5.4'
```

This runs on GitHub-hosted runners. It checks Lua syntax with `luac -p`; it does not prove that FiveM gameplay, framework exports, database queries, NUI behavior, or runtime integrations work in-game.

## Adoption

Each repository must explicitly call the reusable workflow. Adding it here does not automatically run checks in every repository. Pin the reusable workflow to a reviewed tag or commit SHA when a stable shared-workflow release process is established.
