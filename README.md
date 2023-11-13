# pages-turbo-workspace-action
> easily deploy sites in a Turbo-powered monorepo with build-scripts to Cloudflare Pages

See the [example](./.github/workflows/example.yml).

## Usage
```yml
steps:
  - name: Checkout repository
    uses: actions/checkout@v3

  - name: Deploy
    uses: trufflehq/pages-turbo-workspace-action@v1
    with:
      # The script to build your site (default: `build`) (joins with `yarn workspace $workspace_name`)
      build_script: build
      # Cloudflare Account ID
      cloudflare_account_id: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
      # Cloudflare API Token
      cloudflare_api_token: ${{ secrets.CLOUDFLARE_PAGES_API_KEY }}
      # The directory of static assets to upload (default: `dist`)
      directory: dist
      # GitHub Token
      github_token: ${{ secrets.GITHUB_TOKEN }}
      # Optional: The script to run before building your site
      prebuild_script: yarn turbo 
      # Optional: The branch to deploy to production
      production_branch: ${{ github.event.repository.default_branch }}
      # The name of the Cloudflare Pages project
      project_name: my-project-name
      # The name of the yarn workspace being deployed
      workspace_name: web
```

<!-- build-script:
    description: "The script to build your site (default: `build`) (joins with `yarn workspace $workspace-name`)"
    required: false
    default: "build"
  cloudflare-account-id:
    description: "Cloudflare Account ID"
    required: true
  cloudflare-api-token:
    description: "Cloudflare API Token"
    required: true
  directory:
    description: "The directory of static assets to upload (default: `dist`)"
    required: true
    default: "dist"
  github-token:
    description: "GitHub Token"
    required: true
  prebuild-script:
    description: "The script to run before building your site"
    required: false
  production-branch:
    description: "The branch to deploy to production"
    required: true
    default: "master"
  project-name:
    description: "The name of the Cloudflare Pages project"
    required: true
  workspace-name:
    description: "The name of the yarn workspace being deployed"
    required: true
  deploy-to-branch:
    description: "The Cloudflare Pages branch to deploy to"
    required: false -->

## Arguments
| Name | Description | Required | Default |
| --- | --- | --- | --- |
| `build_script` | The script to build your site (default: `build`) (joins with `yarn workspace $workspace_name`) | `false` | `build` |
| `cloudflare_account_id` | Cloudflare Account ID | `true` |  |
| `cloudflare_api_token` | Cloudflare API Token | `true` |  |
| `directory` | The directory of static assets to upload (default: `dist`) | `true` | `dist` |
| `github_token` | GitHub Token | `true` |  |
| `prebuild_script` | The script to run before building your site | `false` |  |
| `production_branch` | The branch to deploy to production | `true` | `master` |
| `project_name` | The name of the Cloudflare Pages project | `true` |  |
| `workspace_name` | The name of the yarn workspace being deployed | `true` |  |
| `deploy_to_branch` | The Cloudflare Pages branch to deploy to | `false` |  |
