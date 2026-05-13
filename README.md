# kursio-workflows

Shared reusable GitHub Actions workflows for `kursio-org` repos.

## discord-notify

Posts push and PR embeds to Discord. To enable for a new repo:

1. Add `DISCORD_WEBHOOK_URL` to the repo's Actions secrets.
2. Drop this into `.github/workflows/discord-notify.yml`:

```yaml
name: Discord Notifications

on:
  push:
    branches: [main]
  pull_request:
    types: [opened, synchronize, reopened, closed]

jobs:
  notify:
    uses: kursio-org/kursio-workflows/.github/workflows/discord-notify.yml@v1
    secrets:
      DISCORD_WEBHOOK_URL: ${{ secrets.DISCORD_WEBHOOK_URL }}
```

Pinned to `@v1`. Changes on `main` are not picked up by consumers until the `v1` tag is moved.
