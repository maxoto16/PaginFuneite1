# GitHub Pages Setup Instructions

This document provides step-by-step instructions to enable GitHub Pages for the PaginFuneite1 project.

## Automatic Setup (Recommended)

The repository includes a GitHub Actions workflow that should automatically enable and deploy to GitHub Pages. However, if the automatic setup fails, follow the manual setup instructions below.

## Manual Setup Instructions

### Step 1: Enable GitHub Pages

1. Go to the repository settings: https://github.com/maxoto16/PaginFuneite1/settings
2. Scroll down to the "Pages" section in the left sidebar
3. Click on "Pages"

### Step 2: Configure Source

1. Under "Source", select **"GitHub Actions"**
2. This will enable the workflow-based deployment

### Step 3: Verify Configuration

1. The workflow should automatically trigger when you push to the `master` branch
2. Check the "Actions" tab to see if the deployment is running
3. Once completed, your site will be available at: https://maxoto16.github.io/PaginFuneite1/

### Step 4: Troubleshooting

If you encounter issues:

1. **Check workflow permissions**: Make sure the workflow has permissions to write to Pages
2. **Verify branch**: Ensure you're pushing to the `master` branch
3. **Check action logs**: Look at the GitHub Actions logs for error details

### Files included for deployment:

- `index.html` - Main page
- `style.css` - Stylesheet
- `script.js` - JavaScript functionality
- `.nojekyll` - Prevents Jekyll processing

## Workflow Details

The deployment uses GitHub Actions with the following steps:

1. **Checkout**: Downloads the repository code
2. **Setup Pages**: Configures GitHub Pages settings
3. **Upload artifact**: Packages the static files
4. **Deploy**: Publishes to GitHub Pages

The workflow is triggered on:
- Pushes to the `master` branch
- Manual workflow dispatch from the Actions tab

## Support

If you continue to experience issues, please check:

1. Repository permissions (ensure you have admin access)
2. GitHub Actions are enabled for the repository
3. The `.github/workflows/static.yml` file is present and correctly configured

The site should be automatically deployed and accessible at https://maxoto16.github.io/PaginFuneite1/ once GitHub Pages is properly configured.