# Hack The Heights Archive

This repository hosts the archive site for all previous Hack The Heights events at Boston College. The site is accessible at [archive.hacktheheights.org](https://archive.hacktheheights.org).

## Structure

- The main `index.html` file serves as the homepage which links to each year's archived site
- Each year's site is in its own directory (`/2016`, `/2017`, etc.)
- **Hybrid Approach:** Some years (2016-2019) are stored directly in this repo, while others are pulled from their own repositories
- GitHub Pages is used to serve the content

## How It Works

This archive uses two different approaches:

1. **Local Content (2016-2019):** 
   - Stored directly in this repository
   - Deployed as-is to GitHub Pages

2. **Remote Repositories (2021+):**
   - Stored in separate repositories (`bccss/hth2021`, `bccss/hth2023`, etc.)
   - Automatically pulled and deployed by GitHub Actions

For detailed setup instructions, see [SETUP.md](SETUP.md).

## Adding a New Year

### For a site in its own repository:

1. Add the year to the matrix in `.github/workflows/deploy.yml`
2. Make sure the corresponding repository exists (e.g., `bccss/hth2025`)
3. Run the workflow manually or wait for the scheduled run

### For a site you want to add directly:

1. Create a folder for the year (e.g., `2025/`)
2. Add the site content directly to that folder

Either way, update the main `index.html` to include links to the new year.

## Development

- The site is built and deployed automatically via GitHub Actions
- To test locally, you can use a local web server:
  ```
  python -m http.server
  ```
- Visit http://localhost:8000 to view the site

## Customizing

You can customize the look and feel of the main index page by editing the `index.html` file. Each year's site maintains its original design from that year's hackathon. 