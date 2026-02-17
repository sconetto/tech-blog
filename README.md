# Sconetto's Tech Blog

A personal tech blog built with [Hugo](https://gohugo.io/) using the [Terminal](https://github.com/panr/hugo-theme-terminal) theme. This blog features bilingual support (English and Portuguese) and covers topics related to software engineering, technology, and personal interests.

## Features

- 🌐 **Bilingual Support**: Content available in both English and Portuguese
- 🎨 **Terminal Theme**: Clean, modern design with syntax highlighting
- 📝 **Markdown Support**: Write posts in Markdown with front matter
- 🔍 **SEO Optimized**: Built-in support for meta tags and keywords
- 📱 **Responsive**: Mobile-friendly design
- ⚡ **Fast**: Static site generation for optimal performance

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended version recommended)
- Git

## Getting Started

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd tech-blog
   ```

2. Install dependencies (if using Hugo modules):

   ```bash
   hugo mod get
   ```

3. Start the development server:

   ```bash
   hugo server
   ```

4. Open your browser and navigate to `http://localhost:1313`

## Project Structure

```bash
tech-blog/
├── content/
│   ├── en-us/          # English content
│   │   └── posts/      # English blog posts
│   └── pt-br/          # Portuguese content
│       └── posts/      # Portuguese blog posts
├── static/            # Static assets (images, CSS, etc.)
├── themes/            # Hugo themes
├── hugo.toml          # Hugo configuration
└── README.md          # This file
```

## Creating a New Post

1. Create a new Markdown file in the appropriate language directory:
   - English: `content/en-us/posts/your-post-name.md`
   - Portuguese: `content/pt-br/posts/seu-post-name.md`

2. Add front matter to your post:

   ```markdown
   +++
   title = "Your Post Title"
   date = "2026-01-02T12:00:00+01:00"
   author = "João Pedro Sconetto"
   description = "Post description"
   tags = ["tag1", "tag2"]
   keywords = ["keyword1", "keyword2"]
   +++

   Your post content here...
   ```

3. Use the archetype for a template:

   ```bash
   hugo new posts/your-post-name.md
   ```

## Building for Production

To build the static site:

```bash
hugo
```

The generated files will be in the `public/` directory, ready to be deployed.

## Deployment

The `public/` directory contains the static site that can be deployed to:

- GitHub Pages
- Netlify
- Vercel
- Any static hosting service

## Configuration

Main configuration is in `hugo.toml`. Key settings include:

- Site title and subtitle
- Language configuration
- Theme settings
- Menu items

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**João Pedro Sconetto**

- GitHub: [@sconetto](https://github.com/sconetto)
- LinkedIn: [sconetto](https://www.linkedin.com/in/sconetto)
- Email: [work@sconetto.me](mailto:work@sconetto.me)

## Acknowledgments

- [Hugo](https://gohugo.io/) - Static site generator
- [Terminal Theme](https://github.com/panr/hugo-theme-terminal) - Hugo theme by [panr](https://github.com/panr)
