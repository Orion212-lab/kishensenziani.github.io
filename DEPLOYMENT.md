# GitHub Pages Deployment Guide

## Issue Fixed
The website was not appearing live on the web because the GitHub Actions workflow for deploying to GitHub Pages was missing.

## What Was Done
Added a GitHub Pages deployment workflow (`.github/workflows/pages.yml`) that:
- Automatically builds the Jekyll site on every push to the `master` branch
- Deploys the built site to GitHub Pages
- Can also be triggered manually from the GitHub Actions tab

## ⚠️ IMPORTANT: The Site Won't Work Until You Complete These Steps

The workflow file is currently only in this Pull Request branch. **You must merge this PR to the `master` branch AND configure GitHub Pages for the site to work.**

## What You Need to Do

### Step 1: Merge This Pull Request
1. Review and approve this PR
2. Click the **Merge pull request** button to merge it into the `master` branch

### Step 2: Enable GitHub Pages in Repository Settings
After the PR is merged to the `master` branch, configure GitHub Pages:

1. Go to your repository on GitHub: https://github.com/Orion212-lab/kishensenziani.github.io
2. Click on **Settings** (top menu)
3. In the left sidebar, click on **Pages**
4. Under "Build and deployment":
   - **Source**: Select "GitHub Actions" (NOT "Deploy from a branch")
5. Save the settings

### Step 3: Verify the Deployment
Once the PR is merged to `master`:
1. Go to the **Actions** tab in your repository
2. You should see the "Deploy Jekyll site to Pages" workflow running
3. Wait for it to complete (should turn green ✓)
4. Your site will be live at: **https://orion212-lab.github.io/kishensenziani.github.io/**

   Or if the repository is renamed to match the pattern exactly (username.github.io), it would be at:
   **https://kishensenziani.github.io/**

### Step 4: Troubleshooting
If the workflow fails:
- Check the Actions tab for error messages
- Verify GitHub Actions has the required permissions:
  - Go to Settings > Actions > General
  - Under "Workflow permissions", ensure at least "Read repository contents and packages permissions" is selected
  - The workflow needs `contents: read`, `pages: write`, and `id-token: write` permissions (already configured in the workflow file)
  - Click Save if you made changes

### Step 5: Future Updates
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
