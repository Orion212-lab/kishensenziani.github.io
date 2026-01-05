# GitHub Pages Deployment Guide

## Issue Fixed
The website was not appearing live on the web because the GitHub Actions workflow for deploying to GitHub Pages was missing.

## What Was Done
Added a GitHub Pages deployment workflow (`.github/workflows/pages.yml`) that:
- Automatically builds the Jekyll site on every push to the `master` branch
- Deploys the built site to GitHub Pages
- Can also be triggered manually from the GitHub Actions tab

## What You Need to Do

### 1. Enable GitHub Pages in Repository Settings
After this PR is merged to the `master` branch, you need to configure GitHub Pages in your repository settings:

1. Go to your repository on GitHub: https://github.com/Orion212-lab/kishensenziani.github.io
2. Click on **Settings** (top menu)
3. In the left sidebar, click on **Pages**
4. Under "Build and deployment":
   - **Source**: Select "GitHub Actions" (NOT "Deploy from a branch")
5. Save the settings

### 2. Verify the Deployment
Once the PR is merged to `master`:
1. Go to the **Actions** tab in your repository
2. You should see the "Deploy Jekyll site to Pages" workflow running
3. Wait for it to complete (should turn green ✓)
4. Your site will be live at: **https://orion212-lab.github.io/kishensenziani.github.io/**

   Or if the repository is renamed to match the pattern exactly (username.github.io), it would be at:
   **https://kishensenziani.github.io/**

### 3. Troubleshooting
If the workflow fails:
- Check the Actions tab for error messages
- Make sure all required permissions are granted to GitHub Actions:
  - Go to Settings > Actions > General
  - Under "Workflow permissions", select "Read and write permissions"
  - Check "Allow GitHub Actions to create and approve pull requests"
  - Click Save

### 4. Future Updates
After the initial setup, every time you push changes to the `master` branch, the site will automatically rebuild and redeploy. You can also manually trigger a deployment:
1. Go to the **Actions** tab
2. Click on "Deploy Jekyll site to Pages"
3. Click "Run workflow"
4. Select the `master` branch
5. Click "Run workflow"

## Technical Details
The workflow uses:
- Ruby 3.1 with Bundler for dependency management
- Jekyll for static site generation
- GitHub's official Actions for Pages deployment
- Production environment variables for optimal Jekyll builds
