---
layout: default
title: Markdown Syntax Cheatsheet
---

# Markdown Syntax Cheatsheet

Quick reference guide for writing documentation with beautiful formatting.

---

## Note Boxes & Callouts

### Note (Blue)
Use for helpful information and general notes.

```html
<div class="note">
<strong>Note</strong>
Your note content goes here. You can include multiple paragraphs, lists, and other elements.
</div>
```

<div class="note">
<strong>Note</strong>
Your note content goes here. You can include multiple paragraphs, lists, and other elements.
</div>

---

### Tip (Green)
Use for helpful advice and best practices.

```html
<div class="tip">
<strong>Tip</strong>
Pro tip content here. This helps users work more efficiently.
</div>
```

<div class="tip">
<strong>Tip</strong>
Pro tip content here. This helps users work more efficiently.
</div>

---

### Warning (Orange)
Use for important warnings that need attention.

```html
<div class="warning">
<strong>Warning</strong>
Warning message here. Users should be cautious about this.
</div>
```

<div class="warning">
<strong>Warning</strong>
Warning message here. Users should be cautious about this.
</div>

---

### Important (Red)
Use for critical information users must know.

```html
<div class="important">
<strong>Important</strong>
Critical information that users absolutely need to know.
</div>
```

<div class="important">
<strong>Important</strong>
Critical information that users absolutely need to know.
</div>

---

### Caution (Yellow)
Use for cautionary information about potential issues.

```html
<div class="caution">
<strong>Caution</strong>
Proceed carefully. There may be risks or limitations.
</div>
```

<div class="caution">
<strong>Caution</strong>
Proceed carefully. There may be risks or limitations.
</div>

---

## Typography

### Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

### Text Formatting

```markdown
**Bold text**
*Italic text*
***Bold and italic***
~~Strikethrough~~
```

**Bold text**
*Italic text*
***Bold and italic***
~~Strikethrough~~

### Links

```markdown
[Link text](https://example.com)
[Link with title](https://example.com "Title text")
```

[Link text](https://example.com)

### Inline Code

```markdown
Use `inline code` for commands and code snippets.
```

Use `inline code` for commands and code snippets.

---

## Code Blocks

Code blocks are automatically styled with beautiful gradients, shadows, and a colorful accent bar at the top for a modern, polished look.

### Basic Code Block

````markdown
```
Plain code block
No syntax highlighting
```
````

```
https://api.example.com/v1/endpoint
```

### Code Block with Language

````markdown
```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}
```
````

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}
```

### Enhanced Code Block Features

All code blocks automatically include:
- **Gradient background** - Subtle light-to-white gradient
- **Colorful accent bar** - Blue-to-green gradient stripe at the top
- **Box shadow** - Depth and elevation
- **Generous padding** - Plenty of breathing room
- **Horizontal scrolling** - For long lines of code

### Common Languages

Specify the language after the opening backticks for better context:

- `javascript` or `js`
- `python` or `py`
- `java`
- `css`
- `html`
- `bash` or `shell`
- `json`
- `xml`
- `yaml`
- `markdown` or `md`
- `sql`
- `c`, `cpp`, `csharp`
- `ruby`, `go`, `rust`

---

## Lists

### Unordered Lists

```markdown
- Item 1
- Item 2
  - Nested item 2.1
  - Nested item 2.2
- Item 3
```

- Item 1
- Item 2
  - Nested item 2.1
  - Nested item 2.2
- Item 3

### Ordered Lists

```markdown
1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item
```

1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item

### Task Lists

```markdown
- [x] Completed task
- [ ] Incomplete task
- [ ] Another task
```

- [x] Completed task
- [ ] Incomplete task
- [ ] Another task

---

## Blockquotes

```markdown
> This is a blockquote.
> It can span multiple lines.
>
> And multiple paragraphs.
```

> This is a blockquote.
> It can span multiple lines.
>
> And multiple paragraphs.

---

## Tables

```markdown
| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Row 1    | Data     | Data     |
| Row 2    | Data     | Data     |
| Row 3    | Data     | Data     |
```

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Row 1    | Data     | Data     |
| Row 2    | Data     | Data     |
| Row 3    | Data     | Data     |

### Table Alignment

```markdown
| Left aligned | Center aligned | Right aligned |
|:-------------|:--------------:|--------------:|
| Left         | Center         | Right         |
| Text         | Text           | Text          |
```

| Left aligned | Center aligned | Right aligned |
|:-------------|:--------------:|--------------:|
| Left         | Center         | Right         |
| Text         | Text           | Text          |

---

## Images

```markdown
![Alt text](/path/to/image.jpg)
![Alt text with title](/path/to/image.jpg "Image title")
```

### Image with Link

```markdown
[![Alt text](/path/to/image.jpg)](https://example.com)
```

---

## Horizontal Rules

```markdown
---
```

or

```markdown
***
```

---

## Utility Classes

### Text Alignment

```html
<p class="text-center">Centered text</p>
<p class="text-right">Right-aligned text</p>
<p class="text-muted">Muted text color</p>
<p class="text-small">Smaller text</p>
```

### Spacing

```html
<div class="mt-0">No top margin</div>
<div class="mt-1">Medium top margin</div>
<div class="mt-2">Large top margin</div>
<div class="mt-3">Extra large top margin</div>

<div class="mb-0">No bottom margin</div>
<div class="mb-1">Medium bottom margin</div>
<div class="mb-2">Large bottom margin</div>
<div class="mb-3">Extra large bottom margin</div>
```

### Flexbox

```html
<div class="flex">Flex container</div>
<div class="flex flex-col">Flex column</div>
<div class="flex items-center">Center items</div>
<div class="flex justify-between">Space between</div>
<div class="flex gap-1">Medium gap</div>
<div class="flex gap-2">Large gap</div>
<div class="flex gap-3">Extra large gap</div>
```

---

## Buttons

```html
<button class="btn">Primary Button</button>
<button class="btn btn-secondary">Secondary Button</button>
<a href="#" class="btn">Link as Button</a>
```

<button class="btn">Primary Button</button>
<button class="btn btn-secondary">Secondary Button</button>

---

## Cards

```html
<div class="card">
  <div class="card-header">
    <h3>Card Title</h3>
  </div>
  <div class="card-body">
    <p>Card content goes here.</p>
  </div>
  <div class="card-footer">
    Footer information
  </div>
</div>
```

<div class="card">
  <div class="card-header">
    <h3>Card Title</h3>
  </div>
  <div class="card-body">
    <p>Card content goes here. You can include any HTML or markdown content.</p>
  </div>
  <div class="card-footer">
    Last updated: February 2026
  </div>
</div>

---

## Special Characters & Escaping

### Escape Special Characters

Use backslash `\` to escape markdown characters:

```markdown
\* Not italic \*
\# Not a heading
\[Not a link\]
```

### HTML Entities

```html
&copy;   → ©
&trade;  → ™
&reg;    → ®
&nbsp;   → (non-breaking space)
&lt;     → <
&gt;     → >
&amp;    → &
```

---

## Quick Tips

1. **Leave blank lines** between different elements (headings, paragraphs, lists, code blocks)
2. **Indent with 4 spaces** for nested lists
3. **Use meaningful alt text** for images for accessibility
4. **Preview your content** before publishing
5. **Keep lines under 100 characters** for readability in source code

---

## Resources

- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/)
- [CommonMark Spec](https://commonmark.org/)
