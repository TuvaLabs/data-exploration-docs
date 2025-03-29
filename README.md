# Data Exploration Documentation

This repository contains the documentation for the Data Exploration project. The documentation is built using Docusaurus and is automatically deployed to GitHub Pages.

## Local Development

To run the documentation site locally:

```bash
cd docusaurus
npm install
npm start
```

This will start a local development server and open up a browser window. Most changes are reflected live while editing.

## Building for Production

To create a production build:

```bash
cd docusaurus
npm run build
```

The built site will be in the `docusaurus/build` directory.

## Deployment

The documentation is automatically deployed to GitHub Pages when:
1. Changes are pushed to the main branch
2. A new release is published in the main repository

## Project Structure

```
docs-repo/
├── docusaurus/          # Docusaurus project files
├── .github/            # GitHub Actions workflows
│   └── workflows/
│       └── deploy.yml  # Deployment workflow
└── versions.json       # Version tracking
``` 