# Complete Jekyll Blog Setup Guide

## What You've Got

A professional Jekyll blog similar to Graham Watts' website with:
- **Minimal Mistakes theme** - Clean, professional design
- **Ready-to-use pages** - Home, About, Categories, Tags, Archives
- **Example blog posts** - Sample content to get you started
- **GitHub Pages ready** - Easy deployment
- **SEO optimized** - Built-in SEO tags
- **Responsive design** - Works on all devices

## Setup Instructions

### Option 1: Deploy to GitHub Pages (Recommended - Free!)

1. **Install Git** (if not already installed)
   - Windows: Download from https://git-scm.com/
   - Mac: `brew install git` or download from https://git-scm.com/
   - Linux: `sudo apt-get install git` or `sudo yum install git`

2. **Create a GitHub account** at https://github.com (if you don't have one)

3. **Create a new repository**:
   - Name it: `yourusername.github.io` (replace `yourusername` with your actual GitHub username)
   - Make it public
   - Don't initialize with README

4. **Upload your blog**:
   ```bash
   cd my-jekyll-blog
   git init
   git add .
   git commit -m "Initial blog setup"
   git branch -M main
   git remote add origin https://github.com/yourusername/yourusername.github.io.git
   git push -u origin main
   ```

5. **Wait 2-3 minutes**, then visit: `https://yourusername.github.io`

That's it! Your blog is live!

### Option 2: Run Locally First (For Testing)

1. **Install Ruby**:
   - **Windows**: Download from https://rubyinstaller.org/ (use Ruby+Devkit version)
   - **Mac**: Ruby comes pre-installed, or use: `brew install ruby`
   - **Linux**: `sudo apt-get install ruby-full build-essential zlib1g-dev`

2. **Install Bundler**:
   ```bash
   gem install bundler
   ```

3. **Install dependencies**:
   ```bash
   cd my-jekyll-blog
   bundle install
   ```

4. **Run the site locally**:
   ```bash
   bundle exec jekyll serve
   ```

5. **View your site** at: `http://localhost:4000`

## Customization Guide

### 1. Update Site Information

Edit `_config.yml`:

```yaml
# Change these values
title: "Your Blog Name"
name: "Your Full Name"
description: "Your blog description"
url: "https://yourusername.github.io"

# Update author info
author:
  name: "Your Name"
  bio: "Your bio here"
  location: "Your City, Country"
```

**Important**: After changing `_config.yml`, you must restart the Jekyll server!

### 2. Update Social Links

In `_config.yml`, find the `author.links` section:

```yaml
author:
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:youremail@example.com"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/yourusername"
    # Add more or remove as needed
```

### 3. Change Theme Color

In `_config.yml`, change the skin:

```yaml
minimal_mistakes_skin: "dark"  # Try: air, aqua, contrast, dark, dirt, neon, mint, plum, sunrise
```

### 4. Add Your First Post

Create a new file in `_posts/` named: `2026-02-13-my-first-post.md`

```markdown
---
title: "My First Blog Post"
date: 2026-02-13
categories:
  - General
tags:
  - hello
  - first-post
---

This is my first blog post! Welcome to my new blog.

## Why I Started This Blog

I wanted to share my knowledge about...

## What You'll Find Here

- Technical tutorials
- Project showcases
- Tips and tricks

Thanks for reading!
```

### 5. Add Images

1. Place images in `assets/images/`
2. Reference them in posts:
   ```markdown
   ![Description](/assets/images/your-image.jpg)
   ```

### 6. Customize the Homepage

Edit `index.md` to change the welcome message and header.

### 7. Update the About Page

Edit `_pages/about.md` with your information.

## Publishing New Posts

### Post Naming Convention
Files in `_posts/` must follow this format:
```
YYYY-MM-DD-title-with-hyphens.md
```

Examples:
- `2026-02-13-getting-started.md` ✓
- `2026-02-13-how-to-use-docker.md` ✓
- `my-post.md` ✗ (missing date)

### Post Template

```markdown
---
title: "Your Post Title"
date: 2026-02-13
categories:
  - Technology
  - Tutorial
tags:
  - programming
  - linux
toc: true
toc_label: "Table of Contents"
header:
  teaser: /assets/images/post-image.jpg
excerpt: "A short description of your post"
---

Your content starts here...

## Section 1

Content...

## Section 2

More content...
```

### Publishing Process

1. Create your post in `_posts/`
2. Test locally: `bundle exec jekyll serve`
3. Commit and push:
   ```bash
   git add .
   git commit -m "Add new post: Your Post Title"
   git push
   ```
4. Wait 1-2 minutes for GitHub Pages to rebuild

## Common Customizations

### Enable Comments (Disqus)

1. Create account at https://disqus.com
2. Get your shortname
3. Edit `_config.yml`:
   ```yaml
   comments:
     provider: "disqus"
     disqus:
       shortname: "your-shortname"
   ```

### Add Google Analytics

1. Get tracking ID from Google Analytics
2. Edit `_config.yml`:
   ```yaml
   google_analytics: "UA-XXXXXXXXX-X"
   ```

### Add Search

Search is built-in! Just uncomment in `_config.yml`:
```yaml
search: true
```

## File Structure Explained

```
my-jekyll-blog/
├── _config.yml              # Main settings - edit this!
├── _data/
│   └── navigation.yml       # Top navigation menu
├── _pages/                  # Your static pages
│   ├── about.md            # About page
│   ├── categories.md       # Auto-generated categories list
│   └── tags.md             # Auto-generated tags list
├── _posts/                  # YOUR BLOG POSTS GO HERE
│   ├── 2026-02-13-bash-logging.md
│   └── 2026-02-10-docker-containers.md
├── assets/
│   └── images/             # Put your images here
├── Gemfile                  # Ruby dependencies (don't edit)
├── index.md                 # Homepage - customize this!
└── README.md               # This guide
```

## Troubleshooting

### Site not updating on GitHub Pages?
- Wait 2-3 minutes after pushing
- Check the "Actions" tab in your GitHub repo for build status
- Make sure your repo is named `yourusername.github.io`

### Jekyll serve fails?
- Make sure Ruby is installed: `ruby --version`
- Install bundler: `gem install bundler`
- Run: `bundle install`
- Try: `bundle update`

### Post not showing up?
- Check the date in the filename (can't be in the future)
- Make sure the file is in `_posts/` folder
- Restart Jekyll: `Ctrl+C` then `bundle exec jekyll serve`

### Images not loading?
- Check the path: `/assets/images/filename.jpg`
- Make sure image is in `assets/images/` folder
- File names are case-sensitive!

## Next Steps

1. ✅ Customize `_config.yml` with your info
2. ✅ Update the About page
3. ✅ Delete example posts or keep them as reference
4. ✅ Write your first post
5. ✅ Add some images to `assets/images/`
6. ✅ Push to GitHub and go live!

## Learning Resources

- **Jekyll Docs**: https://jekyllrb.com/docs/
- **Minimal Mistakes Docs**: https://mmistakes.github.io/minimal-mistakes/
- **Markdown Guide**: https://www.markdownguide.org/
- **GitHub Pages**: https://docs.github.com/en/pages

## Tips for Success

1. **Write regularly** - Consistency is key
2. **Use good titles** - They help with SEO
3. **Add images** - Visual content engages readers
4. **Categorize posts** - Makes content easier to find
5. **Share on social media** - Build your audience
6. **Engage with readers** - Respond to comments

---

Need help? Check out:
- Jekyll community forum: https://talk.jekyllrb.com/
- GitHub Pages help: https://docs.github.com/en/pages
- Minimal Mistakes discussions: https://github.com/mmistakes/minimal-mistakes/discussions

**Happy blogging! 🎉**
