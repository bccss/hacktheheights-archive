# Hack The Heights Archive - Setup Guide

This archive site uses a hybrid approach to maintain all past Hack The Heights websites:

## Repository Structure

1. **Local Content (2016-2019)**: 
   - Content for 2016-2019 is stored directly in this repository in the corresponding year folders
   - These folders are preserved and deployed directly

2. **Remote Repositories (2021+)**:
   - Content for 2021 and later years is stored in separate repositories (`bccss/hth2021`, etc.)
   - These are automatically pulled, built (if needed), and deployed by the GitHub Actions workflow

## How the Workflows Work

This repository uses two separate GitHub Actions workflows:

1. **`deploy.yml`** - Pulls content from remote repositories
   - Handles years that are stored in their own repositories
   - Pulls from `bccss/hth2021`, `bccss/hth2023`, etc.
   - Builds sites using npm/Vite if needed
   - Preserves existing content (doesn't wipe out local content)

2. **`pages.yml`** - Handles local content and main site files
   - Updates the main `index.html` and site structure
   - Preserves the year folders (both local and those created by the other workflow)

## Adding New Years

### For New Years with Their Own Repository

1. Add the year to the matrix in `.github/workflows/deploy.yml`:
   ```yaml
   - year: 2025
     type: vite  # Use 'static' for plain HTML/CSS/JS sites
   ```

2. Update `index.html` to include links to the new year

### For Years You Want to Add Directly to This Repository

1. Create a folder for the year (e.g., `2025/`)
2. Add the site content directly to that folder
3. No need to modify the workflow files
4. Update `index.html` to include links to the new year

## Testing Locally

You can test the site locally by running:
```
python -m http.server
```

Visit http://localhost:8000 to view the site 