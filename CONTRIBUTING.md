# Contributing to the STACK Website

Thank you for your interest in contributing to the STACK website! This document provides guidelines and instructions for contributing.

## Code of Conduct

We are committed to providing a welcoming and inclusive environment. Please be respectful and constructive in all interactions.

## How Can I Contribute?

### Reporting Issues

- **Check existing issues** first to avoid duplicates
- **Use a clear title** that describes the problem
- **Provide details**: steps to reproduce, expected vs actual behavior, screenshots if relevant
- **Specify the page** where the issue occurs (include URL)

### Suggesting Enhancements

- **Check existing suggestions** in the issues
- **Explain the use case** - why would this be useful?
- **Describe the solution** you'd like to see
- **Consider alternatives** you've thought about

### Contributing Content

The most common contributions are:

1. **Adding case studies** - Share how you or your institution uses STACK
2. **Updating documentation** - Improve existing content, fix typos, clarify instructions
3. **Adding community resources** - Events, projects, research
4. **Fixing broken links** - Help maintain link integrity

## Getting Started

### Prerequisites

- **Git** - Version control
- **Python 3.8+** - Required for MkDocs
- **pip** - Python package manager
- **Text editor** - VS Code, Sublime, vim, etc.

### Setting Up Your Development Environment

1. **Fork the repository** on GitHub

2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/stack-web.git
   cd stack-web
   ```

3. **Add upstream remote** (the original repository):
   ```bash
   git remote add upstream https://github.com/maths/stack-web.git
   ```

4. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

5. **Start the local development server**:
   ```bash
   mkdocs serve
   ```

6. **Open your browser** to http://127.0.0.1:8000/

### Making Changes

1. **Create a new branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bugfix-name
   ```

2. **Make your changes** in the `website_files/` directory

3. **Test locally** - View your changes at http://127.0.0.1:8000/

4. **Check for build warnings**:
   ```bash
   mkdocs build
   ```

5. **Commit your changes**:
   ```bash
   git add .
   git commit -m "Brief description of your changes"
   ```

6. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Create a Pull Request** on GitHub

## Content Guidelines

### File Organization

- Content goes in `website_files/`
- Images go in `website_files/img/` or in subdirectory-specific `Images/` folders
- New pages must be added to `nav:` in `mkdocs.yml` to appear in navigation

### Writing Style

- **Use clear, concise language**
- **Write in present tense** ("STACK provides" not "STACK will provide")
- **Use active voice** when possible
- **Define acronyms** on first use
- **Be inclusive** - consider international audience

### Markdown Guidelines

- Use **ATX-style headings** (`# Heading` not `Underlined Heading\n===`)
- Include **alt text** for all images: `![Alt text](image.png)`
- Use **relative links** for internal pages: `[Link text](../Other/Page.md)`
- Use **HTTPS** for external links
- Test all links before submitting

### Accessibility Requirements

All content must be accessible. Please:

- **Add meaningful alt text** to all images
- **Don't use color alone** to convey information
- **Ensure contrast ratios** meet WCAG 2.1 AA standards (4.5:1)
- **Use semantic HTML** when mixing HTML with Markdown
- **Test with different zoom levels** (up to 200%)
- **Avoid tables** where divs would work (better responsive behavior)

See [Accessibility Guidelines](website_files/Legal/Accessibility.md) for more details.

### Adding a New Page

1. Create your markdown file in the appropriate `website_files/` subdirectory
2. Add the page to `mkdocs.yml` under the `nav:` section:
   ```yaml
   nav:
     - Your Section:
       - Your Page: 'path/to/your-page.md'
   ```
3. Use relative links to connect to other pages
4. Test the navigation locally

### Adding a Case Study

1. Create a new `.md` file in `website_files/CaseStudies/YYYY/` (current year)
2. Use the following frontmatter template:
   ```yaml
   ---
   template: casestudy.html
   title: Your Case Study Title
   shortdescription: Brief one-sentence description
   cardimage: your-image.png
   cardimagealt: Description of the image
   ---
   ```
3. Add images to `website_files/CaseStudies/YYYY/Images/`
4. Add the case study to the auto-generated list (it will appear automatically)

### Adding an Event

1. Create a new `.md` file in `website_files/Events/YYYY-MM-DD-EventName.md`
2. Link to the event from `website_files/Training_and_events.md` if it should be prominently featured
3. Include date, location, and registration information clearly

## Testing Your Changes

### Local Testing Checklist

- [ ] Changes display correctly at different zoom levels (100%, 150%, 200%)
- [ ] Changes work on mobile viewport (use browser DevTools)
- [ ] All links work (click every link you added or modified)
- [ ] Images load and have alt text
- [ ] No build warnings: `mkdocs build` runs cleanly
- [ ] Markdown is formatted consistently with existing content

### Browser Testing

Test your changes in:
- Chrome/Chromium
- Firefox
- Safari (if available)
- Edge

## Pull Request Process

1. **Ensure your branch is up to date** with upstream master:
   ```bash
   git fetch upstream
   git rebase upstream/master
   ```

2. **Resolve any conflicts** if they arise

3. **Create a pull request** with:
   - **Clear title** describing the change
   - **Description** explaining what changed and why
   - **Screenshots** for visual changes
   - **Testing notes** - how you tested the changes

4. **Address review feedback** - maintainers may request changes

5. **Be patient** - reviews may take a few days

## Deployment

Deployment is automatic:
- When your PR is merged to `master`
- GitHub Actions builds the site
- Changes appear on https://stack-assessment.org within minutes

**Important:** Never edit files in the `gh-pages` branch directly. It's automatically generated and will be overwritten.

## Style Guide Quick Reference

### Headings
```markdown
# Top Level Heading (H1)
## Second Level (H2)
### Third Level (H3)
```

### Links
```markdown
[Link text](https://example.com)  # External
[Link text](../Other/Page.md)     # Internal relative
[Link text](/Path/To/Page)        # Internal absolute (use relative instead)
```

### Images
```markdown
![Descriptive alt text](../img/image.png)

<img src="../img/image.png" alt="Descriptive alt text" class="img-fluid">
```

### Code Blocks
````markdown
```python
def example():
    return "Hello"
```
````

### Lists
```markdown
- Unordered item
- Another item
  - Nested item

1. Ordered item
2. Another item
```

## Getting Help

- **Documentation**: See README.md for basic setup
- **Issues**: Check existing issues or create a new one
- **Questions**: Ask in the STACK community forums
- **Email**: Contact C.J.Sangwin@ed.ac.uk for website-specific questions

## Recognition

Contributors are recognized in several ways:
- GitHub contribution graph
- Pull request credits
- Case study authorship
- Community acknowledgment

Thank you for contributing to STACK! Your work helps make mathematical assessment accessible to students and educators worldwide.

---

**Note:** These guidelines may be updated periodically. Check back before making large contributions.
