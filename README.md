# npm update workflow (reusable)

Run `npm update` and create pull request.

## Usage

### Create Personal access tokens (classic)
Then, set a token in the repository's secrets as `ACTION_TOKEN`

`GITHUB_TOKEN` can't trigger other actions. If you want to run tests after pull request, you need a token.

### Create `.github/workflows/npm-update.yml`

```yaml
name: npm update

on:
  schedule:
    - cron: '0 0 * * *' #UTC

jobs:
  composer:
    uses: kawax/npm-workflow/.github/workflows/update.yml@v1
    secrets:
      token: ${{ secrets.ACTION_TOKEN }}
```

## Inputs
| name           | description                                  | default                                                 |
|----------------|----------------------------------------------|---------------------------------------------------------|
| node           | node version (same as setup-node)            | latest                                                  |
| git-name       | git name                                     | `github-actions[bot]`                                   |
| git-email      | git email                                    | `41898282+github-actions[bot]@users.noreply.github.com` |
| npm-path       | working directory                            | `./`                                                    |
| branch         | git branch (Always works on a single branch) | npm-update                                              |
| title          | Pull request title                           | npm update                                              |
| commit-message | commit message                               | npm update                                              |

```yaml
jobs:
  composer:
    uses: kawax/npm-workflow/.github/workflows/update.yml@v1
    secrets:
      token: ${{ secrets.ACTION_TOKEN }}
    with:
      node: latest
      git-name: github-actions[bot]
      git-email: 41898282+github-actions[bot]@users.noreply.github.com
      npm-path: ./npm
      branch: npm-update
      title: npm update
      commit-message: npm update
```

## LICENCE
MIT
