# MyCloud Onboarding Runbook

A comprehensive, professional documentation site built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) for MyCloud platform onboarding. This project serves as a complete template for cloud platform documentation.

**Live Site:** https://tchooibm.github.io/CloudOnboardRunbookPoc/  
**Repository:** https://github.com/tchooibm/CloudOnboardRunbookPoc

---

## Table of Contents

- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Adding New Pages](#adding-new-pages)
- [Theme Customization](#theme-customization)
- [Working with Images](#working-with-images)
- [Advanced Customizations](#advanced-customizations)
- [GitHub Pages Deployment](#github-pages-deployment)
- [Development Workflow](#development-workflow)
- [Contributing](#contributing)

---

## Quick Start

### Prerequisites

- Python 3.14+ (recommended) or 3.9+
- pip (Python package manager)
- Git

### Installation

1. Clone the repository:

```bash
git clone https://github.com/tchooibm/CloudOnboardRunbookPoc.git
cd CloudOnboardRunbookPoc
```

2. Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
# OR
venv\Scripts\activate  # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Serve locally:

```bash
mkdocs serve
```

Visit `http://127.0.0.1:8000` in your browser. The site automatically reloads when you save changes.

---

## Project Structure

```
CloudOnboardRunbookPoc/
├── README.md                          # This file
├── mkdocs.yml                         # MkDocs configuration
├── requirements.txt                   # Python dependencies
├── .gitignore                         # Git ignore rules
├── .github/
│   └── workflows/
│       └── ci.yml                     # GitHub Actions CI/CD
├── docs/
│   ├── index.md                       # Homepage
│   ├── assets/
│   │   └── images/                    # Images for documentation
│   ├── getting-started/
│   │   ├── index.md
│   │   ├── create-account.md
│   │   ├── verify-account.md
│   │   ├── mfa-setup.md
│   │   └── best-practices-images.md  # Image usage guide
│   ├── account-setup/
│   │   ├── index.md
│   │   ├── billing.md
│   │   ├── api-keys.md
│   │   └── iam-roles.md
│   ├── infrastructure/
│   │   ├── index.md
│   │   ├── compute/
│   │   ├── storage/
│   │   └── networking/
│   ├── security/
│   │   ├── index.md
│   │   └── audit-logging.md
│   └── troubleshooting/
│       ├── index.md
│       └── authentication.md
├── site/                              # Generated site (do not edit)
└── .cache/                            # MkDocs cache
```

---

## Adding New Pages

### Basic Page Creation

1. **Create the markdown file** in the appropriate section:

```bash
touch docs/section-name/new-page.md
```

2. **Add markdown content:**

```markdown
# Page Title

Introduction paragraph explaining the purpose.

## First Section

Content for the first section.

### Subsection

More detailed information.

## Second Section

Additional content.
```

3. **Update navigation** in `mkdocs.yml`:

```yaml
nav:
  - Section Name:
      - Overview: section-name/index.md
      - Existing Page: section-name/existing-page.md
      - New Page: section-name/new-page.md  # Add this line
```

4. **Save and verify** locally at `http://127.0.0.1:8000`

### Page Best Practices

✅ **Do:**
- Use descriptive headings (`#`, `##`, `###`)
- Keep sections short and focused
- Include table of contents for long pages
- Use clear, concise language
- Link to related pages
- Add examples and code blocks

❌ **Don't:**
- Use more than 3 levels of headings
- Write paragraphs longer than 5 sentences
- Use technical jargon without explanation
- Leave pages incomplete

### Linking Between Pages

Use relative paths for links:

```markdown
[Link to getting started](../getting-started/index.md)
[Link to billing](billing.md)
[Link to security](../security/audit-logging.md)
```

---

## Theme Customization

### Changing Colors and Palette

Edit `mkdocs.yml` in the `theme` section:

```yaml
theme:
  name: material
  palette:
    # Light mode
    - scheme: light
      primary: blue
      accent: light-blue
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    # Dark mode
    - scheme: dark
      primary: blue
      accent: light-blue
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
```

#### Available Color Names

**Primary Colors:**  
`red`, `pink`, `purple`, `deep-purple`, `indigo`, `blue`, `light-blue`, `cyan`, `teal`, `green`, `light-green`, `lime`, `yellow`, `amber`, `orange`, `deep-orange`, `brown`, `grey`, `blue-grey`

#### Color Examples

**Professional Blue Theme (Current):**
```yaml
primary: blue
accent: light-blue
```

**Vibrant Purple & Orange:**
```yaml
primary: purple
accent: orange
```

**Corporate Green & Teal:**
```yaml
primary: green
accent: teal
```

**Tech Red & Black:**
```yaml
primary: red
accent: grey
```

### Changing Logo and Favicon

#### Using External URLs

Update `mkdocs.yml`:

```yaml
theme:
  logo: https://mycloud.example.com/logo.png
  favicon: https://mycloud.example.com/favicon.ico
```

#### Using Local Files

1. Create the `docs/assets/images/` directory:

```bash
mkdir -p docs/assets/images
```

2. Add your logo and favicon files:
   - `docs/assets/images/logo.png` (recommended: 128x128 px)
   - `docs/assets/images/favicon.ico` (32x32 px)

3. Update `mkdocs.yml`:

```yaml
theme:
  logo: assets/images/logo.png
  favicon: assets/images/favicon.ico
```

#### Logo Specifications

| Property | Specification |
|----------|---------------|
| **Format** | PNG, SVG, or JPG |
| **Logo Size** | 128x128 px minimum |
| **Favicon Size** | 32x32 px |
| **Favicon Format** | .ico or .png |
| **Background** | Transparent (recommended) |

#### Creating a Favicon

Use online favicon generators:
- [Favicon.io](https://favicon.io)
- [RealFaviconGenerator](https://realfavicongenerator.net)

Or use ImageMagick from CLI:

```bash
convert logo.png -resize 32x32 favicon.ico
```

### Navigation Features

Enable additional features in `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.tabs              # Top-level tabs
    - navigation.sections          # Section grouping
    - navigation.top               # "Back to top" button
    - navigation.instant           # Instant loading
    - search.suggest               # Search suggestions
    - search.highlight             # Highlight search matches
    - content.code.copy            # Copy button on code blocks
    - content.tabs.link            # Linkable tabs
    - toc.integrate                # Table of contents in sidebar
```

---

## Working with Images

### Image Markdown Syntax

```markdown
![Alt text describing the image](path/to/image.png)

![MyCloud Dashboard](/assets/images/dashboard.png)
```

### Adding Images to Your Project

1. **Create assets directory:**

```bash
mkdir -p docs/assets/images
```

2. **Add images to the directory:**

```bash
cp /path/to/my/image.png docs/assets/images/
```

3. **Reference in markdown:**

```markdown
![MyCloud Dashboard](../assets/images/dashboard.png)

# Or from any section:
![Setup Guide](/assets/images/setup-guide.png)
```

### Best Practices for Documentation Images

See the dedicated guide: [Best Practices for Using Images in Runbooks](getting-started/best-practices-images.md)

Key points:
- Use PNG format for clarity (lossless compression)
- Keep images under 200KB for fast loading
- Add descriptive alt text for accessibility
- Use consistent sizing and styling
- Annotate screenshots with arrows or highlights
- Include images in code blocks when showing examples

### Image Examples

**Inline Image:**
```markdown
![MyCloud Logo](/assets/images/logo.png)
```

**Image with Caption:**
```markdown
![Architecture Diagram](/assets/images/architecture.png)

*Figure 1: High-level system architecture showing compute, storage, and networking components.*
```

**Side-by-Side Images:**
```markdown
| Before | After |
|--------|-------|
| ![Before](/assets/images/before.png) | ![After](/assets/images/after.png) |
```

---

## Advanced Customizations

### Custom CSS Styling

1. Create `docs/assets/stylesheets/custom.css`:

```bash
mkdir -p docs/assets/stylesheets
touch docs/assets/stylesheets/custom.css
```

2. Add custom styles:

```css
:root {
  --md-primary-fg-color: #0066cc;
  --md-accent-fg-color: #00b4d8;
}

.md-content h1 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
}
```

3. Reference in `mkdocs.yml`:

```yaml
extra_css:
  - assets/stylesheets/custom.css
```

### Custom JavaScript

1. Create `docs/assets/javascripts/custom.js`:

```bash
mkdir -p docs/assets/javascripts
touch docs/assets/javascripts/custom.js
```

2. Add JavaScript:

```javascript
// Custom tracking or interactivity
document.addEventListener('DOMContentLoaded', function() {
  console.log('Documentation loaded!');
});
```

3. Reference in `mkdocs.yml`:

```yaml
extra_javascript:
  - assets/javascripts/custom.js
```

### Adding Social Links

Update `mkdocs.yml`:

```yaml
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/tchooibm
    - icon: fontawesome/brands/twitter
      link: https://twitter.com/mycloud
    - icon: fontawesome/brands/linkedin
      link: https://linkedin.com/company/mycloud
```

### Search Configuration

Enhance search in `mkdocs.yml`:

```yaml
plugins:
  - search:
      lang: en
      separator: '[\s\-\.]+'
      prebuild_index: packages
```

### Markdown Extensions

Configure supported markdown features in `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition                    # !!! note blocks
  - pymdownx.details             # <details> collapsible sections
  - pymdownx.superfences         # Better code blocks
  - pymdownx.tabbed             # Tab support
  - pymdownx.highlight          # Syntax highlighting
  - tables                       # Table support
  - toc                          # Table of contents
  - footnotes                    # Footnote support
```

### Using Admonitions (Notes, Warnings, Tips)

```markdown
!!! note
    This is a note with additional information.

!!! warning
    This is important! Pay attention to this.

!!! tip
    Pro tip: This will save you time.

!!! danger
    This is dangerous and could cause data loss.

!!! success
    You did it! This action was successful.
```

### Using Tabs

```markdown
=== "Python"

    ```python
    import mycloud
    client = mycloud.Client()
    ```

=== "Node.js"

    ```javascript
    const mycloud = require('mycloud');
    const client = new mycloud.Client();
    ```

=== "Go"

    ```go
    import "github.com/mycloud/sdk"
    client := mycloud.NewClient()
    ```
```

---

## GitHub Pages Deployment

### Prerequisites

- GitHub repository configured as public or with Pages enabled
- Git with SSH access configured
- Repository branch: `main`

### How Automatic Deployment Works

The CI/CD workflow (`.github/workflows/ci.yml`) automatically:

1. **Triggers** on push to `main` branch
2. **Installs** mkdocs-material and dependencies
3. **Builds** static site from markdown using `mkdocs gh-deploy --force`
4. **Deploys** to `gh-pages` branch
5. **Publishes** at GitHub Pages URL

### Configuration Steps

#### Step 1: Verify GitHub Pages Settings

1. Go to your repository: https://github.com/tchooibm/CloudOnboardRunbookPoc
2. Click **Settings** → **Pages**
3. Confirm:
   - **Source**: Deploy from a branch
   - **Branch**: `gh-pages`
   - **Folder**: `/ (root)`

#### Step 2: Push to GitHub

Make any changes and push:

```bash
git add .
git commit -m "Update documentation"
git push origin main
```

#### Step 3: Monitor Deployment

1. Go to **Actions** tab in your repository
2. Watch the `ci` workflow run
3. Once complete (green checkmark), your site is live

#### Step 4: View Live Site

Access your documentation at:

```
https://tchooibm.github.io/CloudOnboardRunbookPoc/
```

**Note:** First deployment takes 1-2 minutes. Subsequent updates typically appear within 10-30 seconds.

### Troubleshooting GitHub Pages

| Issue | Solution |
|-------|----------|
| Still seeing README | Verify GitHub Pages source is `gh-pages` branch, not `main` |
| Workflow fails | Check **Actions** tab for error messages; verify `requirements.txt` exists |
| `gh-pages` branch missing | Workflow creates it automatically on first successful run |
| Changes not appearing | Clear browser cache; wait 30 seconds; check workflow status |
| 404 error on subpages | Verify `mkdocs.yml` has correct `site_url` value |

### Using a Custom Domain

1. Go to **Settings** → **Pages**
2. Enter custom domain: `docs.mycloud.com`
3. Click **Save**
4. Update DNS records with your domain provider to point to GitHub Pages
5. Enable "Enforce HTTPS"
6. Update `mkdocs.yml`:

```yaml
site_url: https://docs.mycloud.com/
```

---

## Development Workflow

### Local Development

1. Start the development server:

```bash
mkdocs serve
```

2. Edit markdown files in `docs/` directory
3. Changes automatically reload at `http://127.0.0.1:8000`
4. Use browser DevTools to inspect styles

### Building for Production

Build the static site:

```bash
mkdocs build
```

Output is in the `site/` directory (not needed for GitHub Pages—workflow handles it).

### Preview Before Publishing

```bash
# Build locally
mkdocs build

# Serve the built site
python -m http.server 8001 --directory site
```

Visit `http://127.0.0.1:8001` to preview production build.

### Cleaning Build

Remove generated files:

```bash
mkdocs build --clean
```

---

## Advanced Examples

### Multi-Language Documentation

Add language switcher in `mkdocs.yml`:

```yaml
extra:
  alternate:
    - name: English
      link: /en/
      lang: en
    - name: Español
      link: /es/
      lang: es
```

### Analytics Integration

Add Google Analytics in `mkdocs.yml`:

```yaml
extra:
  analytics:
    provider: google
    property: G-XXXXXXXXXX
```

### Versioning

Use Mike for documentation versioning:

```bash
pip install mike
mike deploy 1.0 latest
```

### Redirects

Create `docs/.redirects` for old URLs:

```
/old-page /new-page
/docs/legacy /infrastructure/compute
```

---

## File Organization Best Practices

```
docs/
├── index.md                    # Always start with index
├── section1/
│   ├── index.md               # Section overview
│   ├── topic1.md              # Individual topics
│   └── topic2.md
└── assets/
    ├── images/                # All images
    │   ├── logo.png
    │   ├── screenshot1.png
    │   └── diagram.svg
    └── stylesheets/           # Custom CSS
        └── custom.css
```

**Key Rules:**
- Each directory has an `index.md` overview
- Related files grouped in directories
- Images in centralized `assets/images/`
- Consistent naming: lowercase, hyphens for spaces
- README files not needed (index.md replaces them)

---

## Contributing

### Contribution Process

1. Create a feature branch:

```bash
git checkout -b feature/add-new-section
```

2. Make changes locally:

```bash
mkdocs serve
```

3. Test thoroughly in browser

4. Commit with clear messages:

```bash
git commit -m "Add new onboarding section with examples"
```

5. Push and create Pull Request:

```bash
git push origin feature/add-new-section
```

### Style Guide

- **Headings**: Use `#` for H1, `##` for H2, max 3 levels
- **Line length**: Keep under 100 characters for readability
- **Code blocks**: Always specify language (python, bash, yaml, etc.)
- **Links**: Use relative paths for internal links
- **Images**: Use descriptive alt text
- **Lists**: Use consistent formatting (bullets or numbers)
- **Tables**: Keep to reasonable width for mobile viewing

### Documentation Standards

✅ **Must include:**
- Clear title and description
- Step-by-step instructions
- Code examples
- Expected output or results
- Troubleshooting section for complex topics

❌ **Avoid:**
- Typos and grammar errors
- Outdated information
- Unexplained technical jargon
- Wall-of-text paragraphs
- Broken internal links

---

## Resources

### Official Documentation

- [MkDocs Official Docs](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Material Publishing Guide](https://squidfunk.github.io/mkdocs-material/publishing-your-site/)
- [GitHub Pages Help](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)

### Useful Tools

- [Markdown Linter](https://github.com/igorshubovych/markdownlint-cli)
- [Image Optimization](https://imageoptim.com)
- [Favicon Generator](https://favicon.io)
- [Color Palette Generator](https://coolors.co)
- [PlantUML for Diagrams](https://plantuml.com)

### Similar Projects

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [AWS Documentation](https://docs.aws.amazon.com/)
- [Google Cloud Documentation](https://cloud.google.com/docs)

---

## License

This project is licensed under the MIT License. See LICENSE file for details.

## Support

- **Issues**: Open a GitHub issue in the repository
- **Email**: support@mycloud.example.com
- **Documentation**: https://tchooibm.github.io/CloudOnboardRunbookPoc/

---

**Last Updated:** 2026-08-19  
**Version:** 1.0  
**Maintained by:** MyCloud Documentation Team
