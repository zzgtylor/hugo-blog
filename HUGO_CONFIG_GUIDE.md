# Hugo Configuration Guide

## Current Configuration Review

### ✅ What's Working Well

Your `hugo.toml` has been properly configured with:

```toml
baseURL = "https://zzgcopilot.com"
languageCode = "zh-cn"
title = "ZZG Copilot Blog"
theme = "PaperMod"
```

**Key Settings Enabled:**
- ✅ Reading time display (`ShowReadingTime = true`)
- ✅ Social share buttons (`ShowShareButtons = true`)
- ✅ Post navigation links (`ShowPostNavLinks = true`)
- ✅ Breadcrumb navigation (`ShowBreadCrumbs = true`)
- ✅ Code copy buttons (`ShowCodeCopyButtons = true`)

### 📋 Recommended Additions

Consider adding these configurations to enhance your blog:

```toml
# Output formats
outputs:
  home:
    - HTML
    - RSS
    - JSON

# Permalinks structure
permalinks:
  posts: "/posts/:year/:month/:slug/"

# Markup settings
markup:
  goldmark:
    renderer:
      unsafe: true
  highlight:
    style: "monokai"

# Pagination
paginate: 10
paginatePath: "page"

# Media types
mediaTypes:
  text/richtext:
    suffixes:
      - rtf
```

## Directory Structure

Ensure your Hugo blog follows this structure:

```
hugo-blog/
├── archetypes/          # Content templates
│   └── default.md
├── content/            # Blog posts and pages
│   ├── posts/
│   ├── about/
│   └── _index.md
├── layouts/            # Custom layouts (optional)
├── static/             # Static assets (images, CSS, JS)
├── themes/
│   └── PaperMod/       # Your theme
├── resources/          # Hugo cache (add to .gitignore)
├── public/             # Built site (add to .gitignore)
├── hugo.toml           # Main configuration
├── DEPLOYMENT_CHECKLIST.md
└── README.md
```

## Content Organization

### Create Posts

Use Hugo archetypes to create new posts:

```bash
hugo new posts/my-first-post.md
```

### Front Matter Template

Each post should have:

```yaml
---
title: "Post Title"
date: 2026-06-17
lastmod: 2026-06-17
tags: ["tag1", "tag2"]
categories: ["Category"]
description: "Brief description of the post"
draft: false
cover:
  image: "/images/cover.jpg"
  alt: "Cover description"
---

Your content here...
```

## Optimization Checklist

### Performance
- [ ] Enable minification: Add `--minify` to build command
- [ ] Optimize images with appropriate formats (WebP, JPEG)
- [ ] Lazy load images in posts
- [ ] Minimize CSS and JavaScript

### SEO
- [ ] Add site description in `params`
- [ ] Configure meta descriptions for posts
- [ ] Set up sitemap (automatic with Hugo)
- [ ] Add robots.txt in static folder
- [ ] Implement Open Graph tags

### Content
- [ ] Use consistent tag naming
- [ ] Add reading time estimates
- [ ] Write compelling meta descriptions
- [ ] Use internal linking between posts
- [ ] Add related posts section

## Configuration Examples

### Add Social Links

```toml
[params]
  homeInfoParams = {Title = "欢迎来到 ZZG Copilot", Content = "分享技术教程与文章"}
  socialIcons = [
    { name = "github", url = "https://github.com/zzgtylor" },
    { name = "twitter", url = "https://twitter.com/yourhandle" },
    { name = "linkedin", url = "https://linkedin.com/in/yourprofile" }
  ]
```

### Add Site Analytics

```toml
[params]
  googleAnalyticsID = "G-XXXXXXXXXX"
```

### Custom CSS/JS

Place in `static/` directory and reference in theme configuration.

## Deployment Environment Variables

### Netlify
- `HUGO_VERSION`: 0.147.1
- `GOLANG_VERSION`: (optional, for extended Hugo)

### GitHub Actions
These are handled automatically by the provided workflow.

## Troubleshooting

### Build Issues

**Problem**: Hugo command not found
```bash
# Solution: Check Hugo is installed and version matches
hugo version
```

**Problem**: Theme not found
```bash
# Solution: Ensure theme is in themes/ directory
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

**Problem**: Images not loading
```bash
# Solution: Place images in static/ folder
# Reference as: ![alt](/images/filename.jpg)
```

### Content Issues

**Problem**: Posts not showing
```bash
# Solution: Check front matter doesn't have draft: true
# Ensure posts are in content/posts/ directory
```

**Problem**: Menu items not appearing
```bash
# Solution: Verify menu configuration in hugo.toml
# Check weight values are unique
```

## Performance Metrics

Test your site with:
- [Lighthouse](https://lighthouse-web.app)
- [PageSpeed Insights](https://pagespeed.web.dev)
- [GTmetrix](https://gtmetrix.com)

## Resources

- [Hugo Documentation](https://gohugo.io)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)
- [Hugo Best Practices](https://gohugo.io/getting-started/configuration/)
- [Chinese Hugo Community](https://discourse.gohugo.io)

## Next Steps

1. Add content to `content/posts/` directory
2. Create `content/about/_index.md` for about page
3. Test locally: `hugo server`
4. Push to GitHub
5. Monitor Netlify deployment
6. Verify site at https://zzgcopilot.com
