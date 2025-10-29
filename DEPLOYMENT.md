# Deploying Thyrel.co.uk to GitHub Pages

## Step 1: Create a GitHub Repository

1. Go to https://github.com/new
2. Name your repository (e.g., `thyrel-website`)
3. Make it **public** (required for free GitHub Pages)
4. Don't initialize with README, .gitignore, or license
5. Click "Create repository"

## Step 2: Initialize Git and Push Your Code

Open a terminal in the `Thyrel_website` directory and run:

```bash
git init
git add .
git commit -m "Initial commit: Thyrel consulting website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/thyrel-website.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (tab at the top)
3. Click **Pages** in the left sidebar (under "Code and automation")
4. Under "Build and deployment":
   - Source: Deploy from a branch
   - Branch: Select `main` and `/ (root)`
   - Click **Save**

Your site will be published at: `https://YOUR-USERNAME.github.io/thyrel-website/`

## Step 4: Configure Your Custom Domain (thyrel.co.uk)

### A. Add Custom Domain in GitHub

1. In the same **Pages** settings page
2. Under "Custom domain", enter: `thyrel.co.uk`
3. Click **Save**
4. This will create a `CNAME` file in your repository

### B. Configure DNS with Your Domain Registrar

Log into your domain registrar (whoever you bought thyrel.co.uk from) and add these DNS records:

**For apex domain (thyrel.co.uk):**

Add these 4 **A records**:
```
Type: A
Name: @ (or leave blank for root domain)
Value: 185.199.108.153

Type: A
Name: @ (or leave blank for root domain)
Value: 185.199.109.153

Type: A
Name: @ (or leave blank for root domain)
Value: 185.199.110.153

Type: A
Name: @ (or leave blank for root domain)
Value: 185.199.111.153
```

**Optional - Add www subdomain:**

Add a **CNAME record**:
```
Type: CNAME
Name: www
Value: YOUR-USERNAME.github.io
```

### C. Wait for DNS Propagation

- DNS changes can take 24-48 hours to fully propagate (though often much faster)
- You can check status at: https://www.whatsmydns.net/#A/thyrel.co.uk

### D. Enable HTTPS (Recommended)

1. Return to GitHub Pages settings
2. After DNS propagates, check "Enforce HTTPS"
3. This may take up to 24 hours to become available

## Step 5: Verify Everything Works

1. Visit https://thyrel.co.uk - your site should load
2. Click the email links to verify `marie@thyrel.co.uk` opens correctly
3. Test on mobile devices for responsive design

## Updating Your Website

Whenever you want to make changes:

```bash
# Make your edits to index.html or styles.css
git add .
git commit -m "Description of changes"
git push
```

Changes will appear on your live site within a few minutes.

## Cost: FREE

- GitHub Pages hosting: Free for public repositories
- No server costs
- Only cost is your domain registration (which you already have)

## Troubleshooting

- **Site not loading?** Check DNS propagation and wait 24-48 hours
- **404 error?** Ensure GitHub Pages is enabled and deploying from `main` branch
- **HTTPS not available?** Wait 24 hours after DNS propagates, then enable it
- **Custom domain not working?** Verify CNAME file exists in repository and DNS records are correct
