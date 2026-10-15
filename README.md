# Minibar Expiry & Stock

A static web app (GitHub Pages) built from `MINIBAR_EXPIRATION.xlsx`.
Open the site to search the register, see what is expired or expiring within 30 days, and view stock per floor.
Expiry status is calculated from the date every time the page loads, so it is always current.

## How it works
1. `MINIBAR_EXPIRATION.xlsx` stays the source of truth (the **Item Register** sheet).
2. GitHub Actions runs `scripts/convert.py` to turn it into `data/register.json`, then publishes the site.
3. To update: replace the xlsx in the repo (keep the same file name) and commit. The site refreshes in ~1 minute.
   It also rebuilds every night.

## One-time setup
1. Create a new repo on GitHub and upload everything in this folder (keep the `.github` folder).
2. Repo **Settings → Pages → Source: GitHub Actions**.
3. Go to the **Actions** tab, run **Build data & deploy** once. Your site will be at
   `https://<username>.github.io/<repo>/`.

## Run locally
    pip install openpyxl
    python scripts/convert.py MINIBAR_EXPIRATION.xlsx
    python -m http.server 8000     # open http://localhost:8000

## Note on privacy
GitHub Pages sites are public by default, and so is anything in a public repo. Use a private repo
(Pages on private repos needs a paid GitHub plan) if the stock data should not be public.
