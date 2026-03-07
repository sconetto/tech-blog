# Tech Context

## Development Setup

### Required Tools
- Hugo 0.153.2 (extended version)
- Go 1.25.5
- Node.js 24.12.0
- Dart Sass 1.97.1

### Running Locally
```bash
hugo server
# or with draft content
hugo server -D
```

### Building for Production
```bash
hugo --gc --minify --baseURL "https://blog.sconetto.me/"
```

## Configuration

### hugo.toml Key Settings
- baseurl: "/" (overridden in CI with production URL)
- theme: "terminal"
- contentTypeName: "posts"
- enableGitInfo: true (for last modified dates)

### Languages
- English (en-us): Default, content in content/en-us/
- Portuguese (pt-br): Secondary, content in content/pt-br/

## Dependencies
- hugo-theme-terminal/v4: Via Hugo modules
- No additional npm packages required for basic setup

## Constraints
- Must use extended Hugo for Dart Sass support
- Theme modifications should use partial overrides, not direct edits
- GitHub Pages has built-in Hugo support in Actions

## File Structure
```
tech-blog/
├── .github/workflows/hugo.yaml
├── archetypes/default.md
├── content/
│   ├── en-us/
│   │   ├── about.md
│   │   └── posts/
│   └── pt-br/
│       ├── sobre.md
│       └── posts/
├── hugo.toml
├── layouts/
│   └── partials/
├── static/
│   ├── favicon.png
│   └── terminal.css (optional custom styles)
├── themes/terminal/
└── public/ (generated)
```
