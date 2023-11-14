# pages-turbo-workspace-action
> easily deploy sites in a Turbo-powered monorepo with build-scripts to Cloudflare Pages

See the [example](./.github/workflows/example.yml).

## Usage
```yml
steps:
  - name: Checkout repository
    uses: actions/checkout@v4

  - name: Deploy
    uses: trufflehq/pages-turbo-workspace-action@v1
    with:
      # The script to build your site (default: `build`) (joins with `yarn workspace $workspace_name`)
      build-script: build
      # Cloudflare Account ID
      cloudflare-account-id: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
      # Cloudflare API Token
      cloudflare-api-token: ${{ secrets.CLOUDFLARE_PAGES_API_KEY }}
      # The directory of static assets to upload (default: `dist`)
      directory: dist
      # GitHub Token
      github-token: ${{ secrets.GITHUB_TOKEN }}
      # Optional: The script to run before building your site
      prebuild-script: yarn turbo 
      # Optional: The branch to deploy to production
      production-branch: ${{ github.event.repository.default_branch }}
      # The name of the Cloudflare Pages project
      project-name: my-project-name
      # The name of the yarn workspace being deployed
      workspace-name: web
```

## Arguments
| Name | Description | Required | Default |
| --- | --- | --- | --- |
| `build-script` | The script to build your site (default: `build`) (joins with `yarn workspace $workspace-name`) | `false` | `build` |
| `cloudflare-account-id` | Cloudflare Account ID | `true` |  |
| `cloudflare-api-token` | Cloudflare API Token | `true` |  |
| `directory` | The directory of static assets to upload (default: `dist`) | `true` | `dist` |
| `github-token` | GitHub Token | `true` |  |
| `prebuild-script` | The script to run before building your site | `false` |  |
| `production-branch` | The branch to deploy to production | `true` | `master` |
| `project-name` | The name of the Cloudflare Pages project | `true` |  |
| `workspace-name` | The name of the yarn workspace being deployed | `true` |  |
| `deploy-to-branch` | The Cloudflare Pages branch to deploy to | `false` |  |
