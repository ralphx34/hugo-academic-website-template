# Hugo Academic Personal Website Template

A reusable Hugo template for an academic personal website with Home, Research, Teaching, CV, and Contact pages.

## Requirements

Install Hugo before using the template.

Confirm that Hugo is available:

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