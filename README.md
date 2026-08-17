# Lifely — Grocery Store Website

A static multi-page grocery store website built with **HTML, CSS, and vanilla JavaScript**. Products can be browsed by category, added to a shopping cart, and checked out through a payment form.

**Live site:** https://mhamzanadeem.github.io/Lifely/

---

## Table of Contents

- [Pages](#pages)
- [Project Structure](#project-structure)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Run locally](#run-locally)
- [Deploy to GitHub Pages](#deploy-to-github-pages)
  - [Automated deploy (recommended)](#automated-deploy-recommended)
  - [Manual deploy](#manual-deploy)
- [Development Workflow](#development-workflow)
- [Contributing](#contributing)
- [License](#license)

---

## Pages

| Page | File | Description |
| --- | --- | --- |
| Home | `index.html` | Landing page, hero section and services |
| Categories | `categories.html` | Browse product categories |
| Meat | `Chicken.html` | Chicken, Mutton, Beef + cart |
| Fruits | `fruit.html` | Apple, Pear, Orange + cart |
| Beverages | `beverages.html` | Coke, Fanta, Sprite + cart |
| Vegetables | `vegetable.html` | Tomato, Onion, Garlic + cart |
| Biscuits | `biscuits.html` | Chocolate chip, Wafer, Biscuits + cart |
| Pulses | `pulses.html` | Chickpeas, Soya bean, Lentils + cart |
| Top Selling | `topseller.html` | Popular items + cart |
| Payment | `payment.html` | Billing address / payment checkout form |
| Login | `login.html` | Sign in form (demo only) |
| Sign Up | `signup.html` | Create an account form (demo only) |

---

## Project Structure

```
Lifely/
│
├── index.html               # Landing page (root of the site)
├── categories.html          # Category listing
├── Chicken.html             # Product category page
├── fruit.html               # Product category page
├── beverages.html           # Product category page
├── vegetable.html           # Product category page
├── biscuits.html            # Product category page
├── pulses.html              # Product category page
├── topseller.html           # Top selling items
├── payment.html             # Checkout / payment
├── login.html               # Login
├── signup.html              # Sign up
│
├── css/
│   ├── style.css            # Home page, navbar, footer
│   ├── categories.css       # Categories page
│   ├── categoriespages.css  # Shared product / cart pages
│   ├── topseller.css        # Top selling page
│   ├── login.css            # Login / signup
│   └── payment.css          # Payment page
│
├── images/                  # All site images (logo, products, backgrounds)
├── js/
│   └── cart.js              # Shared shopping cart logic
│
├── .nojekyll                # Tells GitHub Pages to skip Jekyll build
└── README.md
```

---

## Features

- Product categories: Meat, Fruits, Beverages, Vegetables, Biscuits, Pulses
- Working shopping cart (add to cart, change quantity, remove, total price) shared across all product pages via `js/cart.js`
- Checkout page with billing address and payment form
- Login/Sign-up demo pages
- Responsive footer with social media links
- Pure HTML/CSS/JS — no frameworks or build tools required

---

## Getting Started

### Prerequisites

- A web browser
- [Git](https://git-scm.com/) installed (for version control)
- A [GitHub](https://github.com/) account (for publishing)

### Run locally

The site is fully static — just open a page in a browser:

```
git clone https://github.com/mhamzanadeem/Lifely.git
cd Lifely
```

Then open `index.html` in your browser.

> Tip: some browsers restrict local file access. If anything looks off, serve the folder instead:

```
python -m http.server
```

Then visit http://localhost:8000

---

## Deploy to GitHub Pages

### Automated deploy (recommended)

Use the included GitHub Actions workflow by creating `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: "."
      - name: Deploy
        id: deployment
        uses: actions/deploy-pages@v4
```

Then:

1. Push the workflow file to `main`:
   ```
   git add .github/workflows/deploy.yml
   git commit -m "Add GitHub Pages deploy workflow"
   git push
   ```
2. Every push to `main` now builds and deploys automatically.
3. Your site will be at `https://<your-username>.github.io/Lifely/`

### Manual deploy

1. Go to **Settings → Pages** in the repository:  
   https://github.com/mhamzanadeem/Lifely/settings/pages
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Choose **Branch**: `main`, **Folder**: `/ (root)`.
4. Click **Save**.
5. Wait 1–2 minutes, then visit:
   ```
   https://mhamzanadeem.github.io/Lifely/
   ```

> The empty `.nojekyll` file at the repo root prevents Jekyll from interfering with the static files.

---

## Development Workflow

1. Make changes to the HTML/CSS/JS files locally and test them.
2. Check what changed:
   ```
   git status
   git diff
   ```
3. Stage and commit:
   ```
   git add -A
   git commit -m "Describe your change"
   ```
4. Push to publish (Pages updates automatically if enabled):
   ```
   git push
   ```

---

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes and push them to your fork.
4. Open a pull request describing your changes.

---

## License

For educational purposes only.