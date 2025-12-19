# Personal Website - Kishore R. Anekalla

A modern, responsive personal website built with Hugo, featuring blog posts with embedded data analysis capabilities.

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

## Project Structure

```
kanekalla.github.io/
├── config.toml              # Hugo configuration
├── css/
│   └── modern.css           # Modern CSS with dark mode support
├── posts/
│   ├── data-analysis-example/  # Example R Markdown post
│   │   ├── index.html
│   │   └── index.Rmd
│   └── python-data-analysis/  # Example Python post
│       └── index.html
├── images/                  # Images and assets
├── about/                   # About page
├── projects/                # Projects page
└── contact/                 # Contact page
```

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/) (version 0.57.2 or later)
- [R](https://www.r-project.org/) (for R Markdown posts)
- [RStudio](https://www.rstudio.com/) (optional, for R Markdown editing)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/kanekalla/kanekalla.github.io.git
cd kanekalla.github.io
```

2. Install Hugo (if not already installed):
```bash
# macOS
brew install hugo

# Or download from https://gohugo.io/getting-started/installing/
```

3. Run the development server:
```bash
hugo server
```

4. Open your browser to `http://localhost:1313`

### Building for Production

To build the static site:

```bash
hugo
```

The output will be in the `public/` directory.

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

### GitHub Pages

1. Build the site:
```bash
hugo
```

2. Push the `public/` directory to the `gh-pages` branch, or configure GitHub Pages to build from the main branch.

3. Your site will be available at `https://kanekalla.github.io`

### Custom Domain

1. Add a `CNAME` file in the `static/` directory with your domain name
2. Configure DNS settings with your domain provider
3. GitHub Pages will automatically serve your site from the custom domain

## Technologies Used

- **Hugo**: Static site generator
- **R Markdown**: For reproducible research posts
- **Plotly.js**: Interactive data visualizations
- **Font Awesome**: Icons
- **Google Fonts**: Typography

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [R Markdown Guide](https://rmarkdown.rstudio.com/)
- [Plotly.js Documentation](https://plotly.com/javascript/)

## License

This website is personal and all content is owned by Kishore R. Anekalla.

## Contact

For questions or suggestions, please contact me through the [Contact](/contact/) page.

---

**Note**: This is a work in progress. More features and improvements are coming soon! 🚀

