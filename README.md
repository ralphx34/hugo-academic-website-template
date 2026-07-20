# Hugo Academic Personal Website Template

A reusable Hugo template for an academic personal website with Home, Research, Teaching, CV, and Contact pages.

## Requirements

Install Hugo before using the template.

Confirm that Hugo is available. Open an terminal and run:

```bash
hugo version
```

## Run the Website Locally

Open a terminal in the project folder and run:

```bash
hugo server
```

Open the displayed address, normally:

```text
http://localhost:1313/
```

Stop the server with `Ctrl + C`.

To include draft content:

```bash
hugo server -D
```

## Personal Information

Edit the `[params]` section of:

```text
hugo.toml
```

Update the name, position, institution, email, and other personal information.

## Profile Photograph

Place the photograph in:

```text
static/images/
```

For example:

```text
static/images/profile.jpg
```

Then set this value in `hugo.toml`:

```toml
profileImage = "images/profile.jpg"
```

You may delete the placeholder image after replacing it with your desired profile image.

## Curriculum Vitae

Place the PDF in:

```text
static/files/
```

For example:

```text
static/files/cv.pdf
```

Then set this value in `hugo.toml`:

```toml
cvFile = "files/cv.pdf"
```

You may delete the placeholder CV after replacing it with your own CV.

## Homepage Content

Edit:

```text
content/_index.md
```

Use this file for the biography, current work, and other homepage text.

## Add a Research Entry

Run:

```bash
hugo new content research/paper-title.md --kind research
```

Open the generated file and complete its fields.

Available categories are:

```text
working-paper
publication
work-in-progress
```

Change:

```toml
draft = true
```

to:

```toml
draft = false
```

when the entry is ready to appear.

## Add a Teaching Entry

Run:

```bash
hugo new content teaching/course-title.md --kind teaching
```

Complete the generated fields and change:

```toml
draft = true
```

to:

```toml
draft = false
```

when the entry is ready to appear.

## Professional Links

Add profile URLs under `[params.links]` in `hugo.toml`.

Supported links include:

- Google Scholar
- GitHub
- ORCID
- LinkedIn
- Institutional profile

Leave an unwanted field empty to hide it.

## Static Files

Place downloadable files in:

```text
static/files/
```

Place images in:

```text
static/images/
```

A file stored at:

```text
static/files/example.pdf
```

is referenced in content as:

```text
files/example.pdf
```

## Visual Themes

The template includes three complete visual themes:

```text
classic
modern
minimal
```

Select a theme in the `[params]` section of `hugo.toml`:

```toml
themeStyle = "classic"
```

For example, switch to the Modern theme with:

```toml
themeStyle = "modern"
```

Or use the Minimal theme:

```toml
themeStyle = "minimal"
```

Save `hugo.toml` while `hugo server` is running to preview the selected theme.

### Theme Files

The active stylesheets are organized as:

```text
assets/css/
├── base.css
└── themes/
    ├── classic.css
    ├── modern.css
    └── minimal.css
```

`base.css` contains the structural rules shared by every theme, including responsive behavior, grids, component sizing, and basic page organization.

Each file inside `assets/css/themes/` defines a complete visual design. Theme files can change:

- Fonts
- Colors
- Backgrounds
- Header presentation
- Link appearance
- Buttons
- Profile-image shape
- Cards and lists
- Borders
- Shadows
- Spacing
- Decorative elements

The selected theme loads after `base.css`, so it can override any shared rule when necessary.

## Create a Custom Theme

To create another theme, copy one of the existing theme files:

```text
assets/css/themes/classic.css
```

Rename the copy. For example:

```text
assets/css/themes/emerald.css
```

Modify the new file without changing the HTML layouts or content.

Select it in `hugo.toml`:

```toml
themeStyle = "emerald"
```

The filename and configuration value must match exactly:

```text
emerald.css
themeStyle = "emerald"
```

The new theme automatically uses the existing homepage, navigation, Research page, Teaching page, CV page, Contact page, professional links, and responsive layout.

If `themeStyle` refers to a file that does not exist, Hugo will report a build error.

## Customize an Existing Theme

Open the selected file inside:

```text
assets/css/themes/
```

For example, to customize the Classic theme, edit:

```text
assets/css/themes/classic.css
```

Use `hugo server` to preview changes as they are saved.

Common CSS properties include:

```css
color: #17365d;
background-color: #fffdf8;
font-family: Georgia, "Times New Roman", serif;
border-radius: 8px;
box-shadow: 0 4px 14px rgba(0, 0, 0, 0.1);
```

Colors use hexadecimal values such as:

```css
#17365d
```

Useful color-selection tools can provide replacement hexadecimal values.

### Change the Profile Photograph Shape

Circular:

```css
.profile-image {
    border-radius: 50%;
}
```

Slightly rounded:

```css
.profile-image {
    border-radius: 8px;
}
```

Rectangular:

```css
.profile-image {
    border-radius: 0;
}
```

### Change the Font

Change the `font-family` rule in the selected theme:

```css
body {
    font-family: Arial, Helvetica, sans-serif;
}
```

A serif alternative is:

```css
body {
    font-family: Georgia, "Times New Roman", serif;
}
```

### Change Theme Colors

Search the selected theme file for its existing color values and replace them consistently. Commonly repeated colors usually represent:

- Main accent color
- Link color
- Heading color
- Background color
- Muted text color
- Border color

## Customize the Shared Structure

Edit:

```text
assets/css/base.css
```

to change structural behavior shared by every theme, such as:

- Maximum website width
- Homepage columns
- Profile-image dimensions
- Navigation wrapping
- Mobile breakpoint
- Contact-information grid
- Research and teaching entry spacing

A theme can override a shared structural rule by defining the same selector in its own stylesheet.

For example, `base.css` gives the homepage a two-column grid:

```css
.home-intro {
    display: grid;
    grid-template-columns: 180px 1fr;
}
```

A particular theme could override it with:

```css
.home-intro {
    grid-template-columns: 250px 1fr;
}
```

## Customize the HTML Layout

The HTML templates are stored in:

```text
layouts/
```

Important layout files include:

| File | Controls |
|---|---|
| `layouts/_default/baseof.html` | Overall page structure and metadata |
| `layouts/partials/header.html` | Site title and navigation |
| `layouts/partials/footer.html` | Footer |
| `layouts/index.html` | Homepage |
| `layouts/research/list.html` | Research page sections |
| `layouts/partials/research-entry.html` | Individual research entries |
| `layouts/teaching/list.html` | Teaching page |
| `layouts/partials/teaching-entry.html` | Individual teaching entries |
| `layouts/cv/single.html` | CV page |
| `layouts/contact/single.html` | Contact page |
| `layouts/404.html` | Page-not-found screen |

Edit a layout when changing which objects appear, their ordering, or the information they contain.

Edit CSS when changing only how those objects look.

Hugo expressions appear between double braces:

```text
{{ }}
```

These expressions retrieve configuration settings and content. Preserve them unless intentionally changing how Hugo constructs the page.

## Build the Website

Create the production website with:

```bash
hugo
```

Hugo generates the finished site inside:

```text
public/
```

Do not edit files inside `public/`. They are regenerated whenever Hugo builds the website.

## Deploy with GitHub Pages

This repository includes:

```text
.github/workflows/hugo.yaml
```

The workflow builds the Hugo website and deploys the generated `public/` folder through GitHub Pages whenever a change is pushed to the `main` branch.

### 1. Create a GitHub Repository

Create a new public GitHub repository.

Do not initialize it with a README, `.gitignore`, or license because the local project already contains those files.

### 2. Connect the Local Project

From the project folder, run:

```bash
git init
git add .
git commit -m "Create personal website"
git branch -M main
git remote add origin REPOSITORY-URL
git push -u origin main
```

Replace `REPOSITORY-URL` with the repository’s HTTPS or SSH URL.

### 3. Enable GitHub Pages

On GitHub:

1. Open the repository.
2. Select **Settings**.
3. Select **Pages** in the sidebar.
4. Under **Build and deployment**, set **Source** to **GitHub Actions**.

There is no separate Save button.

### 4. Monitor Deployment

After pushing the repository:

1. Open the **Actions** tab.
2. Select **Build and deploy Hugo site**.
3. Wait for the `build` and `deploy` jobs to finish.

Both jobs should display green check marks.

The live address for a project repository normally follows this format:

```text
https://USERNAME.github.io/REPOSITORY-NAME/
```

For example:

```text
https://example-user.github.io/personal-website/
```

### 5. Publish Updates

After editing the website, commit and push the changes:

```bash
git add .
git commit -m "Update website"
git push
```

GitHub Actions will rebuild and redeploy the website automatically.

### GitHub Pages Base URL

The deployment workflow automatically supplies the correct GitHub Pages base URL during the production build:

```yaml
--baseURL "${{ steps.pages.outputs.base_url }}/"
```

Therefore, a GitHub Pages deployment does not require manually changing `baseURL` before every build.

The placeholder in `hugo.toml` may remain:

```toml
baseURL = "https://example.com/"
```

When using another hosting provider or a custom domain, replace it with the site’s permanent public address.

### Troubleshooting

If deployment fails:

1. Open the repository’s **Actions** tab.
2. Open the failed workflow.
3. Select the failed job.
4. Expand the failed step and read its error message.

Confirm that:

- GitHub Pages uses **GitHub Actions** as its source.
- The default branch is named `main`.
- `.github/workflows/hugo.yaml` exists.
- The selected `themeStyle` has a matching file in `assets/css/themes/`.
- The website builds locally with `hugo`.

## Project Structure

```text
personal-website/
├── archetypes/
├── assets/
│   └── css/
├── content/
│   ├── research/
│   ├── teaching/
│   ├── _index.md
│   ├── contact.md
│   └── cv.md
├── layouts/
├── static/
│   ├── files/
│   └── images/
├── .gitignore
├── hugo.toml
└── README.md
```

## License

This website template is available under the MIT License. See `LICENSE` for details.
