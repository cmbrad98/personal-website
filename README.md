# Christina M. Bradley — Personal Website

Personal academic website built with [Astro](https://astro.build).

---

## Running the Site Locally

Before you can run or deploy the site, you need **Node.js** installed on your computer. If you haven't done this yet:

1. Go to [nodejs.org](https://nodejs.org) and download the **LTS** version.
2. Run the installer — just click through the defaults.
3. Open **Terminal** (press `Cmd + Space`, type "Terminal", press Enter).

Then, to run the site on your computer:

```bash
# 1. Navigate to your project folder
cd ~/personal-website

# 2. Install dependencies (only needed the first time)
npm install

# 3. Start the local development server
npm run dev
```

Open your browser to `http://localhost:4321` to see the site. Any changes you save will appear instantly.

---

## Adding Your Headshot

1. Save your photo as `headshot.jpg` inside the `public/` folder.
2. Open `src/pages/index.astro` in a text editor.
3. Find this block:

   ```html
   <div class="headshot-placeholder">
     <span>Photo</span>
   </div>
   <!-- To add your headshot: save a photo named "headshot.jpg" in the public/ folder,
        then replace the div above with:
        <img src="/headshot.jpg" alt="Christina M. Bradley" /> -->
   ```

4. Delete the `<div class="headshot-placeholder">...</div>` block and the comment, and replace it with:

   ```html
   <img src="/headshot.jpg" alt="Christina M. Bradley" />
   ```

---

## Updating Your CV

1. Export your latest CV as a PDF.
2. Name the file `CV_ChristinaBradley.pdf`.
3. Drop it into the `public/` folder, replacing the old file.
4. The CV page will automatically show the updated version.

---

## Deploying to GitHub Pages

This is a step-by-step guide assuming you have never deployed a website before.

### Step 1 — Create a GitHub Account

If you don't already have one, go to [github.com](https://github.com) and sign up for a free account.

### Step 2 — Install Git

Git is software that tracks changes to your files and lets you upload them to GitHub.

1. Open **Terminal**.
2. Type `git --version` and press Enter.
3. If a version number appears, you already have Git. If not, macOS will prompt you to install it — click Install.

Set up your identity in Git (only do this once):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

### Step 3 — Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new) (log in first).
2. Under **Repository name**, choose a name. For the cleanest result with a custom domain, any name works — for example: `personal-website`.
3. Leave it set to **Public**.
4. Do **not** check "Add a README file" (the project already has one).
5. Click **Create repository**.

### Step 4 — Connect Your Local Project to GitHub

GitHub will show you a page with setup instructions. You need the URL of your repository — it looks like:

```
https://github.com/YOUR-USERNAME/personal-website.git
```

In Terminal, navigate to your project and run these commands one at a time:

```bash
cd ~/personal-website
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/personal-website.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username and `personal-website` with whatever you named your repository.

### Step 5 — Enable GitHub Pages

1. On GitHub, open your repository.
2. Click the **Settings** tab (top of the page).
3. In the left sidebar, click **Pages**.
4. Under **Source**, select **GitHub Actions** from the dropdown.
5. Click **Save**.

That's it! GitHub will now automatically build and deploy your site every time you push changes. The first deployment takes about 2–3 minutes.

### Step 6 — Find Your Live Site URL

After the deployment finishes:

- Go to **Settings → Pages** in your repository.
- Your live URL will appear there. It will look like: `https://YOUR-USERNAME.github.io/personal-website/`

### Step 7 (Optional) — Use a Custom Domain

If you want to use `christinambradley.com` instead of the default GitHub URL:

1. In **Settings → Pages**, enter `christinambradley.com` in the **Custom domain** field and click Save.
2. GitHub will add a file called `CNAME` to your repository automatically.
3. Log into wherever you registered your domain (e.g., GoDaddy, Namecheap, Squarespace) and update the DNS settings:
   - Add four **A records** pointing to GitHub's IP addresses:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Add a **CNAME record**: `www` → `YOUR-USERNAME.github.io`
4. DNS changes can take up to 48 hours to propagate, but usually happen within an hour.
5. Once it's working, check **Enforce HTTPS** in GitHub Pages settings.

---

## Making Changes After Deployment

Whenever you update the site (edit content, swap your CV, add your headshot):

```bash
cd ~/personal-website
git add .
git commit -m "Describe what you changed"
git push
```

GitHub will automatically rebuild and redeploy the site. Changes are live within 2–3 minutes.

---

## Project Structure

```
personal-website/
├── public/
│   ├── CV_ChristinaBradley.pdf   ← your CV (replace to update)
│   ├── headshot.jpg              ← add your photo here
│   └── favicon.svg
├── src/
│   ├── layouts/
│   │   └── Layout.astro          ← shared header, nav, footer
│   └── pages/
│       ├── index.astro           ← Home page
│       ├── cv.astro              ← CV page
│       ├── research.astro        ← Research page
│       └── teaching.astro        ← Teaching page
├── .github/
│   └── workflows/
│       └── deploy.yml            ← automatic deployment to GitHub Pages
├── astro.config.mjs
└── package.json
```
