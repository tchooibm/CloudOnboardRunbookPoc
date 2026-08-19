# MyCloud Onboarding Runbook

A comprehensive documentation site built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) for MyCloud platform onboarding.

## Quick Start

### Prerequisites

- Python 3.14+ (recommended) or 3.9+
- pip (Python package manager)

### Installation

1. Clone the repository:

```bash
git clone https://github.com/your-org/mycloud-onboarding-runbook.git
cd mycloud-onboarding-runbook
```

2. Create a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Serve the documentation locally:

```bash
mkdocs serve
```

Visit `http://127.0.0.1:8000` in your browser.

---

## Configuration Guide

### 1. Changing Colors and Theme

The site theme is configured in `mkdocs.yml`. Modify the `theme` section to customize colors:

```yaml
theme:
  name: material
  palette:
    - scheme: light
      primary: blue           # Primary color (light mode)
      accent: light-blue      # Accent color (light mode)
    - scheme: dark
      primary: blue           # Primary color (dark mode)
      accent: light-blue      # Accent color (dark mode)
```

#### Available Colors

MkDocs Material supports these color names:

**Primary Colors:**
- `red`, `pink`, `purple`, `deep-purple`, `indigo`, `blue`, `light-blue`, `cyan`, `teal`, `green`, `light-green`, `lime`, `yellow`, `amber`, `orange`, `deep-orange`, `brown`, `grey`, `blue-grey`

**Example - Blue and Red:**

```yaml
theme:
  palette:
    - scheme: light
      primary: blue
      accent: red
    - scheme: dark
      primary: deep-blue
      accent: red
```

#### Enable Light/Dark Mode Toggle

Add this to the `theme` section to let users toggle between light and dark mode:

```yaml
theme:
  palette:
    - scheme: light
      primary: blue
      accent: light-blue
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    - scheme: dark
      primary: blue
      accent: light-blue
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
```

### 2. Changing the Logo

Update the `logo` and `favicon` URLs in `mkdocs.yml`:

```yaml
theme:
  logo: https://mycloud.example.com/logo.png
  favicon: https://mycloud.example.com/favicon.ico
```

#### Using Local Logo

To use a logo stored in your project:

1. Create a `docs/assets/images/` directory:

```bash
mkdir -p docs/assets/images
```

2. Add your logo file: `docs/assets/images/logo.png`

3. Update `mkdocs.yml`:

```yaml
theme:
  logo: assets/images/logo.png
  favicon: assets/images/favicon.ico
```

#### Logo Specifications

- **Format:** PNG, SVG, or JPG
- **Logo size:** Recommended 128x128 px for best quality
- **Favicon:** 32x32 px for favicon

### 3. Updating Documentation Content

Documentation files are located in the `docs/` directory organized by section:

```
docs/
├── index.md                          # Home page
├── getting-started/
│   ├── index.md
│   ├── create-account.md
│   ├── verify-account.md
│   └── mfa-setup.md
├── account-setup/
│   ├── index.md
│   ├── billing.md
│   ├── api-keys.md
│   └── iam-roles.md
├── infrastructure/
│   ├── index.md
│   ├── compute/first-vm.md
│   ├── storage/buckets.md
│   └── networking/vnets.md
├── security/
│   ├── index.md
│   └── audit-logging.md
└── troubleshooting/
    ├── index.md
    └── authentication.md
```

#### Adding a New Page

1. Create a new markdown file in the appropriate directory:

```bash
touch docs/section-name/new-page.md
```

2. Add content using markdown:

```markdown
# Page Title

Your content here.

## Section

More content.
```

3. Update `mkdocs.yml` navigation to include the new page:

```yaml
nav:
  - Section Name:
      - Overview: section-name/index.md
      - New Page: section-name/new-page.md
```

4. Save and the site will automatically rebuild locally.

#### Markdown Tips

- Use headings `#`, `##`, `###` for structure
- Create tables with pipe syntax: `| Header | Header |`
- Use code blocks with ` ``` ` for syntax highlighting
- Add callouts with `!!! note`, `!!! warning`, `!!! tip`

**Example callout:**

```markdown
!!! warning
    This is an important warning that users should see.
```

#### Linking Between Pages

Link to other pages using relative paths:

```markdown
[Link Text](../other-section/page.md)
[Getting Started](getting-started/index.md)
```

### 4. Deploying to GitHub Pages

#### Prerequisites

- GitHub account and repository
- Git installed locally
- Push access to the repository

#### Step 1: Enable GitHub Pages

Go to your repository **Settings** → **Pages**:
- Source: **GitHub Actions**

#### Step 2: GitHub Actions Workflow (Pre-configured)

The `.github/workflows/deploy.yml` is pre-configured and will:
1. Build the documentation on every push to `main`
2. Deploy it to the `gh-pages` branch automatically
3. Make it available at your GitHub Pages URL

No additional setup needed — just push to GitHub!

#### Step 3: View Your Site

Your documentation is live at:

```
https://tchooibm.github.io/CloudOnboardRunbookPoc/
```

After pushing changes to `main`, they'll be automatically published within seconds.

Repository: https://github.com/tchooibm/CloudOnboardRunbookPoc

#### Custom Domain (Optional)

To use a custom domain instead of GitHub Pages domain:

1. Go to repository **Settings** → **Pages**
2. Under "Custom domain", enter your domain: `docs.mycloud.com`
3. Click **Save**
4. Update your domain provider's DNS records to point to GitHub Pages
5. Enable "Enforce HTTPS"
6. Update `mkdocs.yml` `site_url` with your custom domain

---

## Project Structure

```
.
├── README.md                 # This file
├── mkdocs.yml               # MkDocs configuration
├── requirements.txt         # Python dependencies
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions deployment
├── docs/
│   ├── index.md
│   ├── getting-started/
│   ├── account-setup/
│   ├── infrastructure/
│   ├── security/
│   ├── troubleshooting/
│   └── assets/
│       └── images/
└── site/                    # Generated site (do not edit)
```

## Development Workflow

### Local Development

1. Make changes to markdown files in `docs/`
2. The site automatically rebuilds at `http://127.0.0.1:8000`
3. Use browser DevTools to inspect and debug

### Building for Production

Build the site for deployment:

```bash
mkdocs build
```

This generates the static site in the `site/` directory.

### Cleaning Build

Remove the generated site:

```bash
mkdocs build --clean
```

## Customization Examples

### Change Theme to Purple and Orange

Edit `mkdocs.yml`:

```yaml
theme:
  palette:
    - scheme: light
      primary: purple
      accent: orange
    - scheme: dark
      primary: deep-purple
      accent: orange
```

### Add Custom CSS

Create `docs/assets/stylesheets/custom.css`:

```css
:root {
  --custom-color: #FF6B6B;
}

body {
  font-family: 'Segoe UI', sans-serif;
}
```

Add to `mkdocs.yml`:

```yaml
extra_css:
  - assets/stylesheets/custom.css
```

### Add Navigation Sections

Organize navigation with groups in `mkdocs.yml`:

```yaml
nav:
  - Home: index.md
  - Getting Started:
      - Overview: getting-started/index.md
      - Create Account: getting-started/create-account.md
  - Reference:
      - API: reference/api.md
      - CLI: reference/cli.md
```

## Troubleshooting

### Port Already in Use

If port 8000 is busy:

```bash
mkdocs serve --dev-addr 127.0.0.1:8001
```

### Changes Not Showing

1. Stop the server (Ctrl+C)
2. Clear cache: `mkdocs build --clean`
3. Restart: `mkdocs serve`

### GitHub Pages Not Updating

1. Check GitHub Actions tab for failed builds
2. Verify `.github/workflows/deploy.yml` is correct
3. Ensure `mkdocs.yml` has correct site URL
4. Force a rebuild by making a new commit

## Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

## Contributing

To contribute to this documentation:

1. Create a feature branch: `git checkout -b feature/add-new-section`
2. Make your changes
3. Test locally: `mkdocs serve`
4. Commit and push: `git push origin feature/add-new-section`
5. Create a Pull Request on GitHub

## License

This documentation is licensed under the MIT License. See LICENSE file for details.

## Support

For issues or questions:
- Open an issue on GitHub
- Email: docs@mycloud.example.com
- Visit: https://support.mycloud.example.com

---

**Last Updated:** 2026-08-19 | **Version:** 1.0
