# Publishing the Algebras Translation Status Action to GitHub Marketplace

This guide explains how to publish the Algebras Translation Status Action to the GitHub Marketplace.

## Prerequisites

1. Create a new repository for the GitHub Action (e.g., `algebras-status-action`)
2. Have owner or admin permissions for the repository

## Step 1: Prepare Your Repository

1. Create a new repository specifically for this action (don't use your main CLI repository)
2. Copy the following files to the new repository:
   - `.github/marketplace-action.yml` → `action.yml` (in the root)
   - `.github/README.md` → `README.md` (in the root)
   - `LICENSE` file

## Step 2: Create a Release

1. Navigate to your repository on GitHub
2. Click on "Releases" in the right sidebar
3. Click "Create a new release"
4. Enter a tag version (e.g., `v1.0.0`) - Follow [semantic versioning](https://semver.org/)
5. Enter a release title (e.g., "Initial Release")
6. Add release notes describing the action
7. Check "This is a pre-release" if you're not ready for production
8. Click "Publish release"

## Step 3: Publish to GitHub Marketplace

1. Navigate to your repository on GitHub
2. Go to the "Settings" tab
3. Scroll down to "GitHub Apps" section
4. Click "Publish this Action to the GitHub Marketplace"
5. Check "I have read and accept the GitHub Marketplace Developer Agreement"
6. Choose a category for your action (e.g., "Code quality" or "Utilities")
7. Fill in the required information:
   - Primary Category: Select "Continuous integration" or "Code quality"
   - Name: "Algebras Translation Status"
   - Short description: Keep this concise and clear
   - Detailed description: Provide more information about what your action does
   - Creator: "algebras-ai"
8. Upload screenshots (optional)
9. Click "Publish Action to GitHub Marketplace"

## Versioning Strategy

- Use a `v1` major version tag for the initial stable release
- Use `v1.x.y` for specific versions within the v1 lineage
- For breaking changes, increment the major version number (v2, v3, etc.)

## Maintaining Your Action

1. Test each new version thoroughly before releasing
2. Update the README with any changes or improvements
3. Consider creating release notes for each new version
4. Respond to user issues and feedback

## Using GitHub Actions to Test Your Action

Consider creating a workflow in your action repository to test the action itself. Here's an example:

```yaml
name: Test Action

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: ./
        # Test with different inputs to ensure all combinations work
``` 