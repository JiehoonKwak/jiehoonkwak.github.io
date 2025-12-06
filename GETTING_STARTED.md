# Getting Started: Your Personal Blog

**Live site**: https://jiehoonkwak.github.io
**Local path**: `~/DevHub/sideprojects/blog`

## Quick Commands

```bash
cd ~/DevHub/sideprojects/blog
npm run dev              # Preview at localhost:4321
git add -A && git commit -m "message" && git push   # Deploy
```

## Writing a Post

1. Create file: `src/content/blog/your-post-name.md`
2. Add this template:

```markdown
---
title: 'Your Title'
description: 'Brief summary'
pubDate: 'Dec 06 2024'
---

Your content here. Supports **bold**, *italic*, `code`.

## Headings

- Bullet points
- [Links](https://example.com)
```

3. Preview: `npm run dev` → check localhost:4321
4. Publish: `git add -A && git commit -m "Add post" && git push`

## Project Structure

| Path | Purpose |
|------|---------|
| `src/content/blog/` | Blog posts (.md files) |
| `src/pages/about.astro` | About page |
| `src/consts.ts` | Site title & description |
| `src/styles/global.css` | Colors, fonts |
| `public/images/` | Static images |

## Adding Images

Put in `public/images/`, then in your post:
```markdown
![Alt text](/images/my-image.png)
```

## Troubleshooting

```bash
# Build fails - reset everything
rm -rf node_modules .astro && npm install

# Check deploy status
gh run list --limit 1
```

## Workflow: Obsidian → Blog

1. Draft in Obsidian: `notes/blog-drafts/`
2. Copy to: `blog/src/content/blog/`
3. Add frontmatter, preview, push
