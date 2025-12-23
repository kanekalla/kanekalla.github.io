# Personal Website - Kishore R. Anekalla

A modern, lean, and responsive personal website built with Hugo, optimized for GitHub Pages. This site features academic portfolio presentation, blog posts with embedded data analysis capabilities, and showcases research in computational biology, machine learning, and bioinformatics.

## Features

### 🎨 Modern Design
- **Dark/Light Mode Toggle**: Switch between themes with a single click
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Smooth Animations**: Engaging transitions and hover effects
- **Modern Typography**: Clean, readable fonts optimized for web

### 📊 Data Analysis Support
- **R Markdown Integration**: Write blog posts with embedded R code and visualizations
- **Python Support**: Include Python code examples and visualizations
- **Interactive Charts**: Plotly.js for interactive data visualizations
- **Code Highlighting**: Syntax highlighting for code blocks

### 📝 Blog Features
- **Markdown Support**: Write posts in Markdown
- **R Markdown**: Create posts with embedded R code chunks
- **Data Visualization**: Embed interactive charts and plots
- **Categories & Tags**: Organize posts by topic

## Site Architecture

This is a Hugo static site that generates a complete website optimized for GitHub Pages. The repository structure reflects the built output, while the source content would typically be in a `content/` directory (if using a standard Hugo workflow).

### Current Structure

```
kanekalla.github.io/
├── config.toml              # Hugo site configuration
├── css/
│   ├── modern.css           # Custom modern CSS with dark/light theme
│   └── coder.min.*.css      # Theme CSS (hugo-coder)
├── posts/                   # Blog posts directory
│   ├── index.html           # Posts listing page
│   ├── data-analysis-example/
│   ├── python-data-analysis/
│   └── ml-model-evaluation/
├── categories/              # Category pages and taxonomies
├── tags/                    # Tag pages and taxonomies
├── series/                  # Series/tutorial collections
├── images/                  # Static images and assets
│   ├── kishore.jpg         # Profile image
│   └── favicon-*.png        # Site favicons
├── about/                   # About page
├── projects/                # Projects showcase page
├── contact/                 # Contact page
├── cv/                      # CV/Resume files
└── index.html               # Homepage
```

### Key Features

- **Static Site Generation**: Uses Hugo for fast, secure, and scalable static site generation
- **GitHub Pages Optimized**: Configured for seamless deployment to GitHub Pages
- **SEO Optimized**: Includes proper meta tags, sitemap, and structured data
- **RSS Feed**: Automatic RSS feed generation for blog posts
- **Taxonomies**: Organized content with categories, tags, and series
- **Responsive Design**: Mobile-first approach with modern CSS Grid and Flexbox

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/) Extended version (v0.110.0 or later recommended)
  - Extended version is required for SCSS/SASS support if using themes with SCSS
- [Git](https://git-scm.com/) for version control
- [Go](https://golang.org/) (optional, for Hugo installation via Go)

**Optional for advanced features:**
- [R](https://www.r-project.org/) (for R Markdown posts)
- [RStudio](https://www.rstudio.com/) (for R Markdown editing)
- [Node.js](https://nodejs.org/) (for build tooling, if needed)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/kanekalla/kanekalla.github.io.git
cd kanekalla.github.io
```

2. Install Hugo Extended (if not already installed):
```bash
# macOS
brew install hugo

# Linux
snap install hugo

# Windows (via Chocolatey)
choco install hugo-extended

# Or download from https://gohugo.io/getting-started/installing/
```

3. Run the development server with live reload:
```bash
hugo server -D
```
The `-D` flag includes draft content. For production preview, use:
```bash
hugo server
```

4. Open your browser to `http://localhost:1313` to view the site

### Building for Production

To build the static site for deployment:

```bash
# Clean previous build
rm -rf public/

# Build the site
hugo

# The output will be in the `public/` directory
# This directory contains all static files ready for deployment
```

**Build Options:**
- `hugo --minify` - Minifies HTML, CSS, and JavaScript for production
- `hugo --cleanDestinationDir` - Removes files from destination before building
- `hugo --environment production` - Builds with production environment settings

## Writing Blog Posts

### Markdown Posts

Create a new markdown file in `content/posts/`:

```markdown
---
title: "My New Post"
date: 2024-12-18
categories: ["Data Science"]
tags: ["Python", "Analysis"]
---

Your content here...
```

### R Markdown Posts

1. Create a new `.Rmd` file in `content/posts/`:

```r
---
title: "My R Analysis"
date: "2024-12-18"
output:
  html_document:
    toc: true
---

```{r setup}
knitr::opts_chunk$set(echo = TRUE)
```

## Analysis

```{r}
# Your R code here
library(ggplot2)
data <- read.csv("data.csv")
ggplot(data, aes(x = var1, y = var2)) + geom_point()
```
```

2. Render the R Markdown file:
```r
rmarkdown::render("content/posts/my-post/index.Rmd")
```

3. The rendered HTML will be in the same directory.

### Python Posts

For Python-based posts, you can:

1. Use Jupyter notebooks and convert to HTML
2. Embed Python code examples with syntax highlighting
3. Use Plotly.js for interactive visualizations (see examples)

## Customization

### Theme Colors

Edit `css/modern.css` to customize colors:

```css
:root {
  --primary-color: #2563eb;
  --secondary-color: #7c3aed;
  --accent-color: #06b6d4;
  /* ... */
}
```

### Site Configuration

Edit `config.toml` to update:
- Site title and description
- Social media links
- Navigation menu
- Theme settings

## Data Analysis Examples

### Example 1: Gene Expression Analysis

Located at `/posts/data-analysis-example/`, this post demonstrates:
- R Markdown integration
- Interactive Plotly visualizations
- Statistical analysis
- Data tables

### Example 2: Python Data Analysis

Located at `/posts/python-data-analysis/`, this post shows:
- Python code examples
- Time series visualization
- Correlation analysis
- Distribution plots

## Deployment

### GitHub Pages (Recommended)

This site is optimized for GitHub Pages deployment. There are two main approaches:

#### Option 1: GitHub Actions (Automated)

1. Create `.github/workflows/hugo.yml`:
```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

defaults:
  runs-on: ubuntu-latest
steps:
  - uses: actions/checkout@v4
  - uses: actions/setup-pages@v4
  - uses: peaceiris/actions-hugo@v2
    with:
      hugo-version: 'latest'
      extended: true
  - name: Build
    run: hugo --minify
  - name: Upload artifact
    uses: actions/upload-pages-artifact@v3
    with:
      path: ./public
  - name: Deploy to GitHub Pages
    id: deployment
    uses: actions/deploy-pages@v4
```

2. Configure GitHub Pages in repository settings to use GitHub Actions

#### Option 2: Manual Deployment (Legacy)

1. Build the site:
```bash
hugo --minify
```

2. Push the `public/` directory to the `gh-pages` branch:
```bash
git subtree push --prefix public origin gh-pages
```

3. Your site will be available at `https://kanekalla.github.io`

### Custom Domain

1. Add a `CNAME` file in the `static/` directory (or `public/` after build) with your domain name:
   ```
   yourdomain.com
   ```

2. Configure DNS settings with your domain provider:
   - Add a CNAME record pointing to `kanekalla.github.io`
   - Or add A records pointing to GitHub Pages IPs

3. Enable custom domain in GitHub Pages settings
4. GitHub Pages will automatically serve your site from the custom domain

## Technologies & Stack

### Core Framework
- **Hugo**: Modern static site generator written in Go
  - Version: Latest Extended (recommended)
  - Theme: hugo-coder (modified)
- **Markdown**: Content authoring (Goldmark renderer)

### Frontend
- **CSS3**: Custom modern CSS with CSS variables for theming
- **JavaScript**: Vanilla JS for theme toggle and interactions
- **Font Awesome 6.4.0**: Icon library
- **Google Fonts**: Inter & Fira Code typography

### Content Features
- **R Markdown**: For reproducible research posts with embedded R code
- **Python Integration**: Support for Python code examples
- **Plotly.js**: Interactive data visualizations
- **KaTeX**: Math rendering (if enabled)
- **Syntax Highlighting**: Chroma-based code highlighting

### Performance & SEO
- **Static Site**: Pre-generated HTML for optimal performance
- **Minification**: CSS/JS minification support
- **Sitemap**: Automatic XML sitemap generation
- **RSS Feed**: Automatic RSS feed for blog posts

## Configuration

### Site Settings

Edit `config.toml` to customize:
- Site title, description, and metadata
- Social media links and icons
- Navigation menu structure
- Content taxonomies (categories, tags, series)
- Markup settings (syntax highlighting, math rendering)
- Build and output configuration

### Theme Customization

The site uses a modified version of the hugo-coder theme with custom CSS:
- `css/modern.css`: Main stylesheet with dark/light theme support
- CSS variables for easy color customization
- Responsive breakpoints for mobile, tablet, and desktop

### Content Management

- **Posts**: Created in `content/posts/` (or corresponding structure)
- **Pages**: About, Projects, Contact pages
- **Taxonomies**: Automatic generation of category, tag, and series pages
- **Front Matter**: YAML/TOML metadata for each content piece

## Development Workflow

1. **Content Creation**: Write posts in Markdown or R Markdown
2. **Local Preview**: Run `hugo server -D` to preview changes
3. **Build**: Run `hugo --minify` to generate production files
4. **Deploy**: Push to GitHub (automated via Actions) or manually to gh-pages

## Performance Optimizations

- Static HTML generation (no server-side processing)
- CSS minification and optimization
- Image optimization recommendations
- Efficient asset loading
- Minimal JavaScript footprint

## Resources & Documentation

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Hugo Coder Theme](https://github.com/luizdepra/hugo-coder)
- [R Markdown Guide](https://rmarkdown.rstudio.com/)
- [Plotly.js Documentation](https://plotly.com/javascript/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

## License

This website is personal and all content is owned by Kishore R. Anekalla. The code structure and configuration are available for reference and learning purposes.

## Contact & Support

- **Website**: [https://kanekalla.github.io](https://kanekalla.github.io)
- **Contact Page**: [/contact/](/contact/)
- **GitHub**: [@kanekalla](https://github.com/kanekalla)
- **Email**: Available through contact page

---

**Last Updated**: December 2024 | Built with Hugo and optimized for GitHub Pages 🚀

