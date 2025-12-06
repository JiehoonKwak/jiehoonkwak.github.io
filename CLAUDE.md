# Blog Project Guide

> For Claude: This is Jiehoon's personal blog at https://jiehoonkwak.github.io
> Built with Astro, deployed via GitHub Pages + GitHub Actions

## Quick Reference

| Item | Value |
|------|-------|
| **Local path** | `/Users/jiehoonk/DevHub/sideprojects/blog` |
| **Live URL** | https://jiehoonkwak.github.io |
| **GitHub repo** | https://github.com/JiehoonKwak/jiehoonkwak.github.io |
| **Framework** | Astro v5 |
| **Deploy** | GitHub Actions (auto on push to main) |

## Project Structure

```
blog/
├── src/
│   ├── content/
│   │   └── blog/           # Blog posts go here (.md or .mdx)
│   ├── pages/
│   │   ├── index.astro     # Home page
│   │   ├── about.astro     # About page
│   │   └── blog/           # Blog listing & post pages
│   ├── components/         # Reusable UI components
│   ├── layouts/            # Page layouts
│   ├── styles/             # Global CSS
│   └── consts.ts           # Site title, description
├── public/                 # Static assets (images, favicon)
├── astro.config.mjs        # Astro configuration
└── .github/workflows/      # GitHub Actions deploy workflow
```

## Commands

```bash
# Navigate to project
cd ~/DevHub/sideprojects/blog

# Start dev server (live preview at localhost:4321)
npm run dev

# Build for production (outputs to ./dist)
npm run build

# Preview production build
npm run preview

# Deploy (just push to main)
git add -A && git commit -m "message" && git push
```

## Writing Blog Posts

### 1. Create a new post

Create a `.md` file in `src/content/blog/`:

```markdown
---
title: 'Your Post Title'
description: 'A brief description for SEO and previews'
pubDate: 'Dec 06 2024'
heroImage: '../../assets/optional-image.jpg'
---

Your content here. Supports full Markdown:

## Headings work

- Bullet points
- **Bold** and *italic*

Code blocks with syntax highlighting:

\`\`\`python
print("Hello, world!")
\`\`\`
```

### 2. Frontmatter fields

| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Post title |
| `description` | Yes | Short summary (shown in previews, SEO) |
| `pubDate` | Yes | Publication date (e.g., 'Dec 06 2024') |
| `heroImage` | No | Cover image path |
| `updatedDate` | No | Last updated date |

### 3. Naming convention

Use kebab-case for filenames:
- `my-first-post.md` → URL: `/blog/my-first-post`
- `crispr-screen-analysis.md` → URL: `/blog/crispr-screen-analysis`

## Adding Images

### Option 1: In assets folder (recommended)
```markdown
heroImage: '../../assets/my-image.jpg'
```
Put images in `src/assets/`

### Option 2: In public folder
```markdown
![Alt text](/images/my-image.jpg)
```
Put images in `public/images/`

## Customization

### Site metadata
Edit `src/consts.ts`:
```typescript
export const SITE_TITLE = 'Jiehoon Kwak';
export const SITE_DESCRIPTION = 'Your description here';
```

### Styling
Edit `src/styles/global.css` for colors, fonts, spacing

### About page
Edit `src/pages/about.astro`

### Navigation
Edit `src/components/Header.astro`

## Workflow: Obsidian → Blog

1. **Draft in Obsidian**: Write in `notes/blog-drafts/` folder
2. **When ready**: Copy to `blog/src/content/blog/`
3. **Add frontmatter**: title, description, pubDate
4. **Preview**: `npm run dev`
5. **Publish**: `git add -A && git commit -m "Add post: title" && git push`

## Troubleshooting

### Build fails
```bash
# Clear cache and rebuild
rm -rf node_modules .astro dist
npm install
npm run build
```

### Sharp image error (M-series Mac)
```bash
npm uninstall sharp
npm install sharp@0.33.5
```

### Changes not showing on live site
- Wait 1-2 minutes for GitHub Actions
- Check: `gh run list --limit 1`
- Force refresh browser (Cmd+Shift+R)

## Content Ideas (from personal context)

Based on Jiehoon's research and interests:

**Technical/Research:**
- CRISPR screen data analysis workflows
- Single-cell RNA-seq with scanpy
- AI-augmented wet lab protocols
- Bioinformatics tool comparisons

**AI/Productivity:**
- Claude Code power user tips
- Obsidian + AI workflow
- Research context management

**Personal/Career:**
- Physician-scientist journey
- MD → PhD transition
- Work-life balance reflections
