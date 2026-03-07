# System Patterns

## Architecture
- Static site generator (Hugo)
- Single-page deployments to GitHub Pages
- No database required
- Content-driven architecture

## Key Technical Decisions

### Hugo Module vs Submodule
- Using Hugo module import for Terminal theme (github.com/panr/hugo-theme-terminal/v4)
- Theme lives in themes/terminal/ directory (git submodule)

### Multi-language Setup
- Two content directories: content/en-us/ and content/pt-br/
- Language selector built into Terminal theme
- Separate menus per language

### Deployment
- GitHub Actions workflow (hugo.yaml)
- Runs on every push to main branch
- Uses actions/deploy-pages for GitHub Pages deployment
- BaseURL automatically set via ${{ steps.pages.outputs.base_url }}

## Component Relationships
- hugo.toml: Main configuration (params, languages, menus)
- content/: Markdown content files
- layouts/: Custom templates (overrides theme)
- static/: Static assets (images, custom CSS)
- public/: Generated output (gitignored)

## Critical Files
- hugo.toml: Configuration source of truth
- .github/workflows/hugo.yaml: Deployment pipeline
- themes/terminal/: Theme files (should not modify directly)
