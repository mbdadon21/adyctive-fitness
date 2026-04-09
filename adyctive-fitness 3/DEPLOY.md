# Adyctive Fitness — Cloudflare Pages Deployment Guide

## Project structure

```
adyctive-fitness/
├── index.html          ← Homepage
├── css/
│   └── style.css       ← Shared design system
├── js/
│   └── main.js         ← Shared scripts
└── pages/
    ├── about.html
    ├── rates.html
    ├── nutrition.html
    ├── calendar.html
    └── get-started.html
```

---

## Step 1 — Create a GitHub repository

1. Go to https://github.com and sign in (or create a free account)
2. Click **New repository**
3. Name it: `adyctive-fitness`
4. Set it to **Private** (recommended)
5. Click **Create repository**
6. Upload all your site files — drag and drop them from your computer onto the repository page, preserving the folder structure above

---

## Step 2 — Connect to Cloudflare Pages

1. Go to https://dash.cloudflare.com and sign in (or create a free account)
2. In the left sidebar, click **Workers & Pages**
3. Click **Create** → **Pages** tab → **Connect to Git**
4. Click **Connect GitHub** and authorize Cloudflare
5. Select your `adyctive-fitness` repository
6. Click **Begin setup**

### Build settings (on the next screen)

| Setting | Value |
|---|---|
| Project name | `adyctive-fitness` (or whatever you like) |
| Production branch | `main` |
| Framework preset | **None** |
| Build command | *(leave blank)* |
| Build output directory | `/` (or leave blank) |

7. Click **Save and Deploy**

That's it. Cloudflare will deploy your site in about 60 seconds and give you a URL like:
`https://adyctive-fitness.pages.dev`

---

## Step 3 — Connect your custom domain

1. In your Cloudflare Pages project, go to **Custom domains**
2. Click **Set up a custom domain**
3. Enter: `adyctivefitness.com`
4. Follow the DNS instructions:
   - **If your domain is already on Cloudflare:** It auto-configures
   - **If your domain is elsewhere (GoDaddy, Namecheap, etc.):** Add a CNAME record:
     - Name: `@` (or `www`)
     - Value: `adyctive-fitness.pages.dev`
5. SSL/HTTPS is free and automatic — no extra steps

---

## Step 4 — Set up the contact form (Web3Forms)

The Get Started page uses Web3Forms — a free, serverless form service that works perfectly with static sites.

1. Go to https://web3forms.com
2. Enter Naarah's email address and click **Create Access Key**
3. Copy the Access Key
4. Open `pages/get-started.html` and find this line:
   ```html
   <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
   ```
5. Replace `YOUR_ACCESS_KEY_HERE` with the key you copied
6. Save and push to GitHub — Cloudflare will auto-redeploy in ~30 seconds

Form submissions will go directly to Naarah's email inbox. The free tier allows 250 submissions/month.

---

## Step 5 — Future updates

Whenever you update the site:
1. Edit the HTML/CSS files on your computer
2. Commit and push changes to GitHub
3. Cloudflare Pages auto-deploys within ~30 seconds

No FTP, no cPanel, no WordPress dashboard needed.

---

## Optional: Add a calendar embed

On the Calendar page, there's a placeholder for a booking/calendar embed.

**Recommended free options:**

| Tool | Free tier | Embed type |
|---|---|---|
| Calendly | Yes (1 event type) | `<script>` or `<iframe>` |
| Google Calendar | Yes | `<iframe>` |
| Acuity Scheduling | Paid | `<iframe>` |
| Mindbody | Paid | Widget |

For **Calendly** (simplest):
1. Sign up at https://calendly.com
2. Create your event type
3. Go to **Share** → **Add to website** → copy the embed code
4. Paste it into the calendar placeholder in `pages/calendar.html`

---

## Cost summary

| Service | Monthly cost |
|---|---|
| Cloudflare Pages hosting | **$0** (free, unlimited bandwidth) |
| Custom domain (if renewing) | ~$10–15/year |
| Web3Forms (form handling) | **$0** (250 submissions/month free) |
| Calendly (basic) | **$0** (1 event type free) |
| **Total** | **~$1/month** (just domain renewal) |

Compare to WordPress hosting which typically runs $15–50/month.
