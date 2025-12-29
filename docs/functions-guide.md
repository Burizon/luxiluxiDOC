# Functions Guide

Welcome to the Functions Guide! This page will help you understand and use common functions in GitHub Pages and Jekyll.

## Table of Contents
1. [Introduction](#introduction)
2. [Markdown Functions](#markdown-functions)
3. [Jekyll Functions](#jekyll-functions)
4. [Git Functions](#git-functions)
5. [GitHub Actions Functions](#github-actions-functions)

---

## Introduction

This guide covers the most commonly used functions when working with GitHub Pages. Whether you're writing content, customizing your site, or automating workflows, these functions will help you work more efficiently.

---

## Markdown Functions

### Basic Formatting Functions

#### Text Styling
Transform your text appearance:

```markdown
**make_bold("text")**
Result: **text**

*make_italic("text")*
Result: *text*

~~strikethrough("text")~~
Result: ~~text~~

`inline_code("text")`
Result: `text`
```

#### Headings
Create hierarchical structure:

```markdown
# create_heading(1, "Title")       → # Title
## create_heading(2, "Section")    → ## Section
### create_heading(3, "Subsection") → ### Subsection
```

### Link Functions

#### Creating Links
```markdown
<!-- Basic link -->
[link_text](url)
Example: [GitHub](https://github.com)

<!-- Link with title -->
[link_text](url "hover title")
Example: [GitHub](https://github.com "Visit GitHub")

<!-- Reference-style link -->
[link_text][reference]
[reference]: url
```

#### Internal Navigation
```markdown
<!-- Link to another page -->
[text](./path/to/page.md)

<!-- Link to section on same page -->
[text](#section-heading)

<!-- Link to section on another page -->
[text](./page.md#section-heading)
```

### List Functions

#### Unordered Lists
```markdown
create_list([
  "Item 1",
  "Item 2",
  "Item 3"
])

Result:
- Item 1
- Item 2
- Item 3
```

#### Ordered Lists
```markdown
create_numbered_list([
  "First step",
  "Second step",
  "Third step"
])

Result:
1. First step
2. Second step
3. Third step
```

#### Nested Lists
```markdown
- Parent item
  - Child item 1
  - Child item 2
    - Grandchild item
```

### Code Block Functions

#### Syntax Highlighting
````markdown
```language
code here
```

Example:
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```
````

#### Line Highlighting (if supported)
````markdown
```javascript{1,3-5}
function example() {
  let x = 1;        // highlighted
  let y = 2;
  let z = 3;        // highlighted
  return x + y + z; // highlighted
}
```
````

### Table Functions

#### Create Table
```markdown
create_table({
  headers: ["Column 1", "Column 2", "Column 3"],
  alignment: ["left", "center", "right"],
  rows: [
    ["Data 1", "Data 2", "Data 3"],
    ["Data 4", "Data 5", "Data 6"]
  ]
})

Result:
| Column 1 | Column 2 | Column 3 |
|:---------|:--------:|---------:|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```

---

## Jekyll Functions

### Liquid Template Functions

#### Variables
```liquid
<!-- Define variable -->
{% assign variable_name = "value" %}

<!-- Use variable -->
{{ variable_name }}

<!-- Capture content -->
{% capture my_var %}
  Content here
{% endcapture %}
```

#### Conditionals
```liquid
<!-- If statement -->
{% if condition %}
  Content when true
{% elsif other_condition %}
  Alternative content
{% else %}
  Default content
{% endif %}

<!-- Unless (opposite of if) -->
{% unless condition %}
  Content when false
{% endunless %}
```

#### Loops
```liquid
<!-- For loop -->
{% for item in collection %}
  {{ item.title }}
{% endfor %}

<!-- For loop with limit -->
{% for item in collection limit:5 %}
  {{ item }}
{% endfor %}

<!-- For loop with conditions -->
{% for post in site.posts %}
  {% if post.featured %}
    {{ post.title }}
  {% endif %}
{% endfor %}
```

#### Filters
Common Jekyll filters:

```liquid
<!-- String filters -->
{{ "hello" | capitalize }}           → Hello
{{ "HELLO" | downcase }}             → hello
{{ "hello world" | upcase }}         → HELLO WORLD
{{ "hello_world" | replace: "_", " " }} → hello world

<!-- Array filters -->
{{ array | first }}                  → First element
{{ array | last }}                   → Last element
{{ array | size }}                   → Number of elements
{{ array | sort }}                   → Sorted array
{{ array | join: ", " }}             → Joined string

<!-- Date filters -->
{{ page.date | date: "%Y-%m-%d" }}   → 2024-01-15
{{ page.date | date_to_string }}     → 15 Jan 2024

<!-- URL filters -->
{{ "/path/to/file" | relative_url }} → /baseurl/path/to/file
{{ "/path" | absolute_url }}         → https://example.com/path
```

### Include Functions

#### Including Partials
```liquid
<!-- Basic include -->
{% include header.html %}

<!-- Include with parameters -->
{% include button.html 
   text="Click Me" 
   url="/contact" 
   style="primary" 
%}

<!-- Include from subdirectory -->
{% include components/card.html 
   title=post.title 
   content=post.excerpt 
%}
```

### Layout Functions

#### Front Matter
```yaml
---
layout: default
title: Page Title
description: Page description
date: 2024-01-15
categories: [tutorial, documentation]
tags: [jekyll, guide]
author: Your Name
---
```

#### Using Layouts
In `_layouts/default.html`:
```html
<!DOCTYPE html>
<html>
<head>
  <title>{{ page.title }}</title>
</head>
<body>
  {% include header.html %}
  
  <main>
    {{ content }}
  </main>
  
  {% include footer.html %}
</body>
</html>
```

### Site Variables

#### Accessing Site Data
```liquid
<!-- Site configuration -->
{{ site.title }}
{{ site.description }}
{{ site.url }}
{{ site.baseurl }}

<!-- Collections -->
{% for post in site.posts %}
  {{ post.title }}
{% endfor %}

{% for page in site.pages %}
  {{ page.url }}
{% endfor %}

<!-- Custom data from _data/ -->
{{ site.data.navigation }}
{{ site.data.authors.john.name }}
```

---

## Git Functions

### Basic Git Commands

#### Repository Functions
```bash
# Initialize repository
git init

# Clone repository
git clone <repository-url>

# Check status
git status

# View history
git log
git log --oneline
git log --graph --oneline --all
```

#### Staging Functions
```bash
# Stage specific file
git add <filename>

# Stage all changes
git add .

# Stage by pattern
git add "*.md"

# Unstage file
git reset <filename>

# Interactive staging
git add -p
```

#### Commit Functions
```bash
# Commit with message
git commit -m "Your message"

# Commit all tracked changes
git commit -am "Your message"

# Amend last commit
git commit --amend

# Amend without editing message
git commit --amend --no-edit
```

#### Branch Functions
```bash
# List branches
git branch
git branch -a  # include remote

# Create branch
git branch <branch-name>

# Switch branch
git checkout <branch-name>

# Create and switch
git checkout -b <branch-name>

# Delete branch
git branch -d <branch-name>

# Rename branch
git branch -m <old-name> <new-name>
```

#### Remote Functions
```bash
# View remotes
git remote -v

# Add remote
git remote add origin <url>

# Fetch from remote
git fetch origin

# Pull from remote
git pull origin <branch>

# Push to remote
git push origin <branch>

# Set upstream
git push -u origin <branch>
```

#### Merge Functions
```bash
# Merge branch into current
git merge <branch-name>

# Merge with no fast-forward
git merge --no-ff <branch-name>

# Abort merge
git merge --abort
```

### Advanced Git Functions

#### Stash Functions
```bash
# Stash changes
git stash

# Stash with message
git stash save "WIP: feature"

# List stashes
git stash list

# Apply stash
git stash apply
git stash apply stash@{0}

# Pop stash (apply and remove)
git stash pop

# Drop stash
git stash drop
```

#### Diff Functions
```bash
# Show changes
git diff

# Show staged changes
git diff --staged

# Compare branches
git diff branch1..branch2

# Show changes for file
git diff <filename>
```

#### Reset Functions
```bash
# Soft reset (keep changes)
git reset --soft HEAD~1

# Mixed reset (unstage changes)
git reset HEAD~1

# Hard reset (discard changes)
git reset --hard HEAD~1

# Reset file
git checkout -- <filename>
```

---

## GitHub Actions Functions

### Workflow Syntax

#### Basic Workflow Structure
```yaml
name: Workflow Name

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  job-name:
    runs-on: ubuntu-latest
    steps:
      - name: Step name
        uses: actions/checkout@v2
      
      - name: Run command
        run: echo "Hello World"
```

#### Trigger Functions

```yaml
# Push trigger
on:
  push:
    branches:
      - main
      - develop
    paths:
      - 'docs/**'

# Pull request trigger
on:
  pull_request:
    types: [opened, synchronize]

# Schedule trigger (cron)
on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly

# Manual trigger
on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy'
        required: true
```

#### Action Functions

```yaml
# Use an action
- uses: actions/checkout@v2
  with:
    fetch-depth: 0

# Run shell command
- run: npm install

# Run multiple commands
- run: |
    npm install
    npm run build
    npm test

# Set environment variables
- name: Set env
  env:
    NODE_ENV: production
  run: npm run build
```

#### Conditional Functions

```yaml
# Run step conditionally
- name: Deploy
  if: github.ref == 'refs/heads/main'
  run: npm run deploy

# Use expressions
- name: Test
  if: success() && github.event_name == 'push'
  run: npm test
```

#### Matrix Strategy

```yaml
strategy:
  matrix:
    node-version: [14, 16, 18]
    os: [ubuntu-latest, windows-latest]

steps:
  - uses: actions/setup-node@v2
    with:
      node-version: ${{ matrix.node-version }}
```

---

## Practical Examples

### Example 1: Blog Post with Jekyll

```markdown
---
layout: post
title: "How to Use Functions"
date: 2024-01-15
categories: tutorial
---

## Introduction

{% assign author = "John Doe" %}
Welcome to this tutorial by {{ author }}.

{% if page.categories contains "tutorial" %}
This is a tutorial post.
{% endif %}

{% for tag in page.tags %}
- {{ tag }}
{% endfor %}
```

### Example 2: Navigation Component

```liquid
<!-- _includes/navigation.html -->
<nav>
  <ul>
    {% for item in site.data.navigation %}
      <li>
        <a href="{{ item.url | relative_url }}"
           {% if page.url == item.url %}class="active"{% endif %}>
          {{ item.title }}
        </a>
      </li>
    {% endfor %}
  </ul>
</nav>
```

### Example 3: Automated Deployment

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.0
          
      - name: Install dependencies
        run: |
          gem install bundler
          bundle install
          
      - name: Build site
        run: bundle exec jekyll build
        
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./_site
```

---

## Tips and Best Practices

### 1. Function Reusability
Create reusable includes for common functions:
```liquid
<!-- _includes/format-date.html -->
{{ include.date | date: "%B %d, %Y" }}

<!-- Usage -->
{% include format-date.html date=page.date %}
```

### 2. Error Handling
Add fallbacks for missing data:
```liquid
{{ page.author | default: "Anonymous" }}
{{ post.image | default: "/assets/default.png" }}
```

### 3. Performance
Optimize loops and conditionals:
```liquid
<!-- Cache expensive operations -->
{% capture nav_html %}
  {% include navigation.html %}
{% endcapture %}
{{ nav_html }}
```

### 4. Documentation
Document custom functions:
```yaml
# _data/functions.yml
format_date:
  description: "Formats date to readable format"
  usage: "{% include format-date.html date=page.date %}"
  parameters:
    - date: "Date object to format"
```

---

## Troubleshooting

### Common Issues

**Liquid syntax errors:**
- Check for matching tags (`{% if %}` needs `{% endif %}`)
- Verify filter syntax
- Use `| inspect` to debug values

**Git conflicts:**
- Use `git status` to identify conflicts
- Edit files to resolve markers
- Stage and commit resolved files

**Action failures:**
- Check the Actions tab for logs
- Verify syntax in YAML files
- Check secret availability

---

## Resources

- [Liquid Template Language](https://shopify.github.io/liquid/)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

[← Editing Guide](./editing-guide.md) | [← Management Guide](./management-guide.md) | [← Back to README](../README.md)
