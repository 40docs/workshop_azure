# Cloud Workshop

A comprehensive Azure cloud workshop documentation site built with MkDocs.

## 🚀 Live Site

Visit the live documentation at: https://40docs.github.io/workshop_azure/

✅ **Site is live and themed with 40docs branding!**

## 🛠 Development

### Prerequisites

- Python 3.x
- pip

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/40docs/workshop_azure.git
   cd workshop_azure
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Clone the theme (for local development):
   ```bash
   git clone https://github.com/40docs/theme.git theme
   ```

4. Serve the site locally:
   ```bash
   mkdocs serve
   ```

5. Visit http://127.0.0.1:8000 in your browser

### Building the Site

```bash
mkdocs build
```

## 📁 Structure

```
workshop_azure/
├── docs/                 # Documentation content
│   ├── index.md         # Homepage
│   ├── getting-started.md
│   ├── stylesheets/     # Custom CSS
│   └── javascripts/     # Custom JS
├── theme/               # Custom theme (cloned during build)
├── .github/workflows/   # GitHub Actions
├── mkdocs.yml          # MkDocs configuration
└── requirements.txt    # Python dependencies
```

## 🔄 Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch using GitHub Actions.

The deployment process:
1. Clones the 40docs theme
2. Builds the MkDocs site
3. Deploys to GitHub Pages

## 🎨 Theme

This site uses the custom 40docs theme located at https://github.com/40docs/theme

## 📝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is part of the 40docs organization.