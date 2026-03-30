# Deploying atelics.com

## GitHub Pages (recommended)

1. **Create the repo:**
   ```
   cd Atelics/site
   git init
   git add .
   git commit -m "Initial site"
   ```

2. **Push to GitHub:**
   ```
   gh repo create atelics --public --source=. --push
   ```

3. **Enable GitHub Pages:**
   - Go to repo Settings → Pages
   - Source: "Deploy from a branch"
   - Branch: `main`, folder: `/ (root)`
   - Save

4. **Wire up the custom domain:**
   - The `CNAME` file is already in the repo (points to `atelics.com`)
   - In your DNS provider, add these records:

   | Type  | Name | Value |
   |-------|------|-------|
   | A     | @    | 185.199.108.153 |
   | A     | @    | 185.199.109.153 |
   | A     | @    | 185.199.110.153 |
   | A     | @    | 185.199.111.153 |
   | CNAME | www  | your-github-username.github.io |

   - Back in GitHub Pages settings, enter `atelics.com` as custom domain
   - Check "Enforce HTTPS"

5. **Verify:** Visit https://atelics.com — should show the landing page. https://atelics.com/margin/ should show Margin.

## Site structure

```
site/
├── index.html          ← atelics.com landing page
├── margin/
│   └── index.html      ← atelics.com/margin/ (Margin story)
├── CNAME               ← custom domain config
└── DEPLOY.md           ← this file
```

## Adding new things

New projects are just new folders with an `index.html`. Add a link on the landing page and push.

## Updating Margin

The source of truth for Margin is `Atelics/Margin/drafts/margin.html`. When you update it there, copy it into `site/margin/index.html` and push.
