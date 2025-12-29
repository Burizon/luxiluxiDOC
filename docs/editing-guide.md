# Editing Guide

Welcome to the Editing Guide! This page will help you understand how to edit content in your GitHub Pages repository.

## Table of Contents
1. [Getting Started](#getting-started)
2. [Editing Files](#editing-files)
3. [Markdown Basics](#markdown-basics)
4. [Best Practices](#best-practices)

---

## Getting Started

Before you start editing, make sure you have:
- A GitHub account
- Access to your repository
- Basic understanding of Git and GitHub

### Accessing Your Files

1. Navigate to your repository on GitHub
2. Click on the file you want to edit
3. Click the pencil icon (✏️) to edit the file

---

## Editing Files

### Editing on GitHub

The easiest way to edit files is directly on GitHub:

1. **Open the file**: Navigate to the file in your repository
2. **Click Edit**: Click the pencil icon in the top right
3. **Make changes**: Edit the content using Markdown
4. **Preview**: Click the "Preview" tab to see how it looks
5. **Commit changes**: Scroll down and add a commit message
6. **Save**: Click "Commit changes" to save

### Editing Locally

For more complex edits, you can work locally:

```bash
# Clone the repository
git clone https://github.com/yourusername/your-repo.git

# Navigate to the directory
cd your-repo

# Open in your favorite editor
code .

# Make your changes, then:
git add .
git commit -m "Your commit message"
git push origin main
```

---

## Markdown Basics

GitHub Pages uses Markdown for content. Here are the essentials:

### Headers
```markdown
# H1 Header
## H2 Header
### H3 Header
```

### Text Formatting
```markdown
**Bold text**
*Italic text*
~~Strikethrough~~
`Code inline`
```

### Links
```markdown
[Link text](https://example.com)
[Internal link](./another-page.md)
```

### Lists
```markdown
- Unordered item 1
- Unordered item 2

1. Ordered item 1
2. Ordered item 2
```

### Code Blocks
````markdown
```javascript
function hello() {
  console.log("Hello, world!");
}
```
````

### Images
```markdown
![Alt text](path/to/image.png)
```

### Blockquotes
```markdown
> This is a quote
> It can span multiple lines
```

### Tables
```markdown
| Header 1 | Header 2 |
|----------|----------|
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |
```

---

## Best Practices

### 1. Write Clear Commit Messages
Always describe what you changed and why:
```
✅ Good: "Update pricing section with new rates"
❌ Bad: "Update file"
```

### 2. Preview Before Committing
Always use the Preview tab to check your formatting before saving.

### 3. Edit One Thing at a Time
Make small, focused changes rather than large sweeping edits.

### 4. Use Branches for Major Changes
For significant updates:
```bash
git checkout -b feature/new-content
# Make your changes
git commit -m "Add new content section"
git push origin feature/new-content
# Create a pull request on GitHub
```

### 5. Keep Backups
Before making major changes, create a backup:
```bash
git branch backup-$(date +%Y%m%d)
```

### 6. Check Links
After editing, verify all links work:
- Internal links to other pages
- External links to websites
- Image links

### 7. Maintain Consistency
- Use the same heading levels throughout
- Follow the same formatting style
- Keep the tone consistent

---

## Quick Reference

### Common Tasks

**Add a new page:**
1. Create a new `.md` file in your repository
2. Add content using Markdown
3. Link to it from other pages

**Fix a typo:**
1. Click the file
2. Click edit (✏️)
3. Make the change
4. Commit with message: "Fix typo in [section]"

**Update navigation:**
1. Edit your `_config.yml` or navigation file
2. Update the menu items
3. Test on a local preview

---

## Need Help?

- [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/) (if using Jekyll)

---

[← Back to README](../README.md) | [Management Guide →](./management-guide.md) | [Functions Guide →](./functions-guide.md)
