# My Jekyll Blog

A professional blog built with Jekyll and the Minimal Mistakes theme.

## Quick Start

### Prerequisites

- Ruby 2.7 or higher
- Bundler
- Git

### Local Development

1. **Install dependencies**:
   ```bash
   bundle install
   ```

2. **Run locally**:
   ```bash
   bundle exec jekyll serve
   ```

3. **View your site**:
   Open your browser to `http://localhost:4000`

### Deploy to GitHub Pages

1. **Create a new repository** on GitHub named `yourusername.github.io`

2. **Initialize git and push**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/yourusername.github.io.git
   git push -u origin main
   ```

3. **Enable GitHub Pages**:
   - Go to your repository settings
   - Navigate to "Pages" section
   - Select "main" branch as source
   - Click Save

4. **Your site will be live** at `https://yourusername.github.io` in a few minutes!

## Customization

### Update Site Information

Edit `_config.yml` to customize:
- Site title and description
- Your name and bio
- Social media links
- Theme skin color

### Add New Posts

Create a new file in `_posts/` with the format:
```
YYYY-MM-DD-title.md
```

Example post structure:
```markdown
---
title: "Your Post Title"
date: 2026-02-13
categories:
  - Category1
  - Category2
tags:
  - tag1
  - tag2
---

Your content here...
```

### Change Theme

Edit the `minimal_mistakes_skin` in `_config.yml`. Options:
- `air`
- `aqua`
- `contrast`
- `dark`
- `dirt`
- `neon`
- `mint`
- `plum`
- `sunrise`

## Project Structure

```
my-jekyll-blog/
├── _config.yml          # Main configuration
├── _data/
│   └── navigation.yml   # Navigation menu
├── _pages/              # Static pages
│   ├── about.md
│   ├── categories.md
│   └── tags.md
├── _posts/              # Blog posts
│   └── YYYY-MM-DD-title.md
├── assets/
│   └── images/          # Images for posts
├── Gemfile              # Ruby dependencies
└── index.md             # Homepage
```

## Writing Tips

### Add Images

Place images in `assets/images/` and reference them:
```markdown
![Alt text](/assets/images/your-image.jpg)
```

### Code Highlighting

Use fenced code blocks with language specification:
````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

### Table of Contents

Add to your post's front matter:
```yaml
toc: true
toc_label: "Contents"
toc_icon: "list"
```

## Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Minimal Mistakes Documentation](https://mmistakes.github.io/minimal-mistakes/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)

## License

This blog template is free to use and modify for your own projects.

---

Happy blogging! 🎉
