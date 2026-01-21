# Marked Pages - Interactive Documentation Template

A lightweight, zero-build template for creating beautiful, interactive documentation websites using Markdown files. This template automatically renders your Markdown documentation with GitHub-flavored styling and provides a clean navigation interface. Only the key elements below need to be updated.

`Ctrl + click` [here](https://jhauga.github.io/markedPages/index.html) to see a working example.

## Key Elements

- **`docRoot`**: Global variable storing the name of the folder where the documentation is located
  - Defaults to `docs`
- **`docPages`**: Global variable storing an array of human readable strings that match the file names in `docRoot` or the `docs` folder
  - **NOTE** - Use relative path syntax if the file is not in the `docRoot`. See [QUICKSTART](QUICKSTART.md) for illustration
- **`repoBranch`**: Branch where GitHub pages is deployed, defaulting to `main`
- **`defaultUserName`**: GitHub username
- **`defaultRepoName`**: GitHub repository name

## Features

- **Zero Build Process**: No compilation, bundling, or build tools required
- **Markdown-Powered**: Write your documentation in standard Markdown format
- **GitHub Flavored Styling**: Uses GitHub's official markdown CSS for familiar, professional appearance
- **Automatic Navigation**: Generates a navigation menu from your documentation files
- **Smart File Resolution**: Handles multiple naming conventions (camelCase, kebab-case, snake_case)
- **GitHub Pages Ready**: Deploy instantly to GitHub Pages or run locally
- **Responsive Design**: Clean, modern interface that works on all devices
- **Light Mode Forced**: Consistent light theme for optimal readability

## Quick Start

### Option 1: Use as Template (Recommended)

1. Click the "Use this template" button on GitHub
2. Create your new repository
3. Clone your new repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
   cd YOUR-REPO-NAME
   ```

4. Add your Markdown files to the `docs/` folder
5. Update the configuration in `index.html` (see [Configuration section](#configuration))
   - Apply additional edits as needed
6. Enable GitHub Pages in your repository settings

### Option 2: Manual Setup

1. Fork or download this repository
2. Add your documentation Markdown files to the `docs/` folder
3. Configure the menu items in `index.html`
   - Apply additional edits as needed
4. Deploy to GitHub Pages or any static hosting service

## Configuration

### Setting Up Your Documentation

Open `index.html` and modify the configuration variables in the `<head>` section:

```javascript
// Menu items for your documentation pages
const docPages = ["Basics", "Objects", "Classes", "Utility Types"];

// Documentation folder (default: "docs")
const docRoot = "docs";

// For GitHub Pages deployment (auto-detected, but can be overridden)
const defaultUserName = `YOUR-USERNAME`;
const defaultRepoName = `YOUR-REPO`;
const defaultBaseUrl = `https://raw.githubusercontent.com/${defaultUserName}/${defaultRepoName}/main/`;
```

### Adding Documentation Pages

1. **Create Markdown Files**: Add `.md` files to the `docs/` folder

   ```
   docs/
   ├── basics.md
   ├── objects.md
   ├── classes.md
   └── utility-types.md
   ```

2. **Update Menu Items**: Add page names to the `docPages` array in `index.html`

   ```javascript
   const docPages = ["Basics", "Objects", "Classes", "Utility Types"];
   ```

The template will automatically:

- Convert menu names to file paths using multiple naming conventions
- Handle camelCase, kebab-case, and snake_case variations
- Search for matching files (e.g., "Utility Types" → `utility-types.md`, `utility_types.md`, or `utilityTypes.md`)

### Home Page (README.md)

The "Home" menu item automatically loads your repository's `README.md` file. Place your main documentation or welcome content there.

## File Naming Conventions

The template supports multiple file naming conventions and will attempt to find your files using:

- **Kebab-case**: `utility-types.md`
- **Snake_case**: `utility_types.md`
- **camelCase**: `utilityTypes.md`
- **Uppercase/Lowercase variations**: `UTILITY-TYPES.md`, `utility-types.md`

**Example**: A menu item called "API Reference" will search for:

- `api-reference.md`, `API-REFERENCE.md`
- `api_reference.md`, `API_REFERENCE.md`
- `apiReference.md`, `ApiReference.md`

## Project Structure

```
your-repo/
├── index.html          # Main application file
├── README.md           # Home page content
├── docs/               # Documentation folder
│   ├── basics.md
│   ├── objects.md
│   ├── classes.md
│   └── utility-types.md
└── *                   # Repository content
```

## Styling and Customization

### Navigation Bar

The navigation bar uses a professional gradient design:

- **Background**: Dark gradient (dark slate gray to black)
- **Active Link**: Blue accent with light background
- **Hover Effect**: Subtle blue highlight

### Content Area

- **Maximum Width**: 1200px for optimal readability
- **Background**: White with subtle shadow
- **Typography**: GitHub-flavored markdown styles
- **Code Blocks**: Syntax highlighting with light theme

### Customizing Colors

All styling is contained within the `<style>` section of `index.html`. The design follows the [HTML CSS Style Color Guide](.github/instructions/html-css-style-color-guide.instructions.md) with:

- Cool colors (blues, grays) for primary elements
- Light backgrounds for content
- High contrast text for accessibility
- Minimal use of hot colors (reserved for accents)

To customize, edit the CSS variables and classes in the `<style>` block.

## Deployment

### GitHub Pages

1. **Enable GitHub Pages**:
   - Go to your repository Settings
   - Navigate to "Pages" section
   - Select "main" branch as source
   - Select "/ (root)" as folder
   - Click Save

2. **Access Your Site**:

   ```
   https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
   ```

### Local Development

Serve the project using any local server:

**Python**:

```bash
python -m http.server 8000
```

**Node.js (http-server)**:

```bash
npx http-server
```

**VS Code Live Server Extension**:

- Install "Live Server" extension
- Right-click `index.html` → "Open with Live Server"

Then visit `http://localhost:8000` (or appropriate port)

## How It Works

### Architecture

1. **Menu Generation**: The embedded script reads the `docPages` array and creates navigation links
2. **File Loading**: When a link is clicked, the corresponding Markdown file is fetched via XMLHttpRequest
3. **Markdown Parsing**: The [Marked.js](https://marked.js.org/) library converts Markdown to HTML
4. **Rendering**: Converted HTML is injected into the content div with GitHub-flavored styling
5. **URL Detection**: Automatically detects GitHub Pages deployment vs. local development

### Key Components

#### 1. Menu Creation (`createDocPageMenu()`)

- Generates navigation from `docPages` array
- Adds "Home" link automatically
- Applies naming convention resolution

#### 2. Markdown Loading (`loadMarkdown()`)

- Detects environment (localhost vs. GitHub Pages)
- Constructs proper file URLs
- Fetches and parses Markdown content
- Handles file resolution errors

#### 3. Debugging Tools

- Adjusts links for localhost testing
- Provides fallback favicon
- Handles missing resources gracefully

## Dependencies

All dependencies are loaded from CDN (no installation required):

- **[Marked.js](https://cdn.jsdelivr.net/npm/marked/lib/marked.umd.js)**: Markdown parser
- **[GitHub Markdown CSS](https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.8.1/github-markdown.min.css)**: Styling

## Browser Support

Works in all modern browsers:

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Opera (latest)

## Troubleshooting

### Files Not Loading

**Problem**: Markdown files don't load when clicking menu items

**Solutions**:

- Verify file names match the naming conventions
- Check that files are in the correct `docs/` folder
  - Change the value of the `docRoot` global variable if using folder other than `docs/` to house documentation.
- Open browser DevTools Console to see specific error messages
- Ensure file paths in `docPages` array match actual files

### GitHub Pages 404 Errors

**Problem**: Site shows 404 on GitHub Pages

**Solutions**:

- Confirm GitHub Pages is enabled and set to main branch
- Wait 2-3 minutes after pushing changes
- Check that `index.html` is in the root directory
- Verify repository is public (or you have Pages enabled for private repos)

### Styling Issues

**Problem**: Dark mode showing or incorrect styles

**Solutions**:

- Clear browser cache
- Ensure `github-markdown.css` CDN link is accessible
- Check browser console for CSS loading errors
- Verify `color-scheme: light` meta tag is present

### Local Development CORS Errors

**Problem**: Files won't load when opening `index.html` directly

**Solution**: Use a local web server (see [Local Development section](#local-development))

## Contributing

This is a template repository designed to be forked and customized. Feel free to:

- Modify the styling to match your brand
- Add new features or functionality
- Improve the documentation
- Submit issues or pull requests to the original template

## License

This work is dedicated to the public domain under the [CC0 Public Domain](https://creativecommons.org/public-domain/cc0/) Dedication.
This template is provided as-is for public use. Customize and deploy freely for your documentation needs.

## Credits

- **Marked.js**: Fast Markdown parser ([https://marked.js.org/](https://marked.js.org/))
- **GitHub Markdown CSS**: Official GitHub styling ([https://github.com/sindresorhus/github-markdown-css](https://github.com/sindresorhus/github-markdown-css))

## Support

For issues, questions, or suggestions:

1. Check the Troubleshooting section above
2. Review the code comments in `index.html`
3. Open an issue in the template repository
4. Consult the [Marked.js documentation](https://marked.js.org/) for Markdown parsing questions

---
