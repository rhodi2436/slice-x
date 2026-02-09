# Deployment Guide

## GitHub Pages Setup

This repository is configured to deploy to GitHub Pages with the following structure:
- Main branch content → Root directory (`/`)
- Feature branch content → `/feat` subdirectory

### Enabling GitHub Pages

To enable GitHub Pages deployment for this repository:

1. Go to repository Settings → Pages
2. Under "Build and deployment":
   - Source: Select "GitHub Actions"
3. Save the configuration

### How It Works

The deployment workflow (`.github/workflows/deploy-feat.yml`) automatically:

1. **Checks out two branches:**
   - Main branch for root content
   - Feature branch (`copilot/add-template-selection-feature`) for `/feat` content

2. **Creates deployment structure:**
   ```
   deploy/
   ├── index.html (from main branch)
   ├── README.md (from main branch)
   └── feat/
       ├── index.html (from feature branch)
       └── README.md (from feature branch)
   ```

3. **Deploys to GitHub Pages:**
   - Root: `https://rhodi2436.github.io/slice-x/`
   - Feature: `https://rhodi2436.github.io/slice-x/feat/`

### Workflow Triggers

The workflow runs automatically when:
- Code is pushed to the `copilot/add-template-selection-feature` branch
- Manually triggered via GitHub Actions UI

### Verifying Deployment

After the workflow completes successfully:
1. Check the Actions tab for deployment status
2. Visit the deployment URLs to verify both versions are live
3. Test the new features in the `/feat` subdirectory

### Troubleshooting

**"Action required" status:**
- This usually means GitHub Pages needs to be enabled in repository settings
- Follow the "Enabling GitHub Pages" steps above

**404 errors:**
- Ensure GitHub Pages is enabled
- Check that the workflow completed successfully
- Wait a few minutes for deployment to propagate

**Old content showing:**
- Clear browser cache
- Check the workflow run timestamp
- Verify the correct branch was deployed
