# Production Deployment Guide — flanboyant.com

This guide provides a step-by-step checklist and platform instructions to safely and efficiently deploy `flanboyant.com` to production.

---

## 1. Pre-Deployment Checklist (Placeholders to Replace)

Before pushing to production, you must replace the placeholder contact numbers, social media links, and ensure your SEO assets are in place within `index.html`.

### 1.1 WhatsApp Contact Link
Currently, all CTA buttons ("Apply Now", "Message Us", etc.) point to a placeholder Brazilian WhatsApp number: `https://wa.me/5511999999999`.

1. Open `index.html`.
2. Search for `5511999999999` (there are 4 occurrences).
3. Replace it with your actual business WhatsApp number in the international format (without `+` or leading zeros):
   - **For USA (e.g., +1 415 555 0199):** `https://wa.me/14155550199`
   - **For Brazil (e.g., +55 11 98888 8888):** `https://wa.me/5511988888888`

### 1.2 Social Media Profiles
The footer links for **X (Twitter)** and **LinkedIn** currently use `#` as a placeholder:
```html
<a href="#" class="footer-link">X</a>
<a href="#" class="footer-link">LinkedIn</a>
```
1. Open `index.html` and scroll to the bottom (around lines 735-740).
2. Replace `href="#"` with your official links:
   - **X (Twitter):** `<a href="https://x.com/your_handle" class="footer-link" target="_blank" rel="noopener">X</a>`
   - **LinkedIn:** `<a href="https://linkedin.com/company/your_company" class="footer-link" target="_blank" rel="noopener">LinkedIn</a>`

### 1.3 Social Preview Image (OG Image)
The HTML head defines `https://flanboyant.com/og-image.png` as the social media preview card for Twitter, LinkedIn, and Facebook, but the physical file is currently missing from the directory.

1. Design a preview image with standard dimensions: **1200 × 630 pixels**.
2. Save it exactly as `og-image.png`.
3. Save the file directly in the root folder alongside `index.html`.

---

## 2. Recommended Deployment Platforms

Because `flanboyant.com` is a pure static HTML site without build pipelines or complex dependencies, it is incredibly fast to host and 100% free on modern edge platforms.

### Option A: Vercel (Highly Recommended & Easiest)
Vercel is the premier platform for static sites. It takes under 60 seconds to configure.

1. **Via Vercel Web Dashboard (No Git required):**
   - Go to [Vercel](https://vercel.com/) and log in.
   - Go to the **Vercel Deploy** page: `vercel.com/deploy` (or your dashboard).
   - Simply **drag and drop** your project folder containing `index.html`.
   - Vercel will instantly publish it and give you a `.vercel.app` preview URL.
2. **Via Git Repository (Automated CI/CD):**
   - Push your folder to a private or public GitHub/GitLab repository.
   - Import the repository in Vercel.
   - Leave build settings blank (Vercel automatically detects it is a static project).
   - Click **Deploy**. Every push to `main` will instantly trigger a production update.

---

### Option B: Cloudflare Pages (Extremely Fast Global CDN)
Cloudflare offers the most robust free tier for bandwidth and enterprise-grade speed.

1. Log in to your Cloudflare Dashboard.
2. Navigate to **Workers & Pages** > **Pages** > **Create a project**.
3. Select **Connect to Git** or **Direct Upload** (drag and drop).
4. Upload the project folder.
5. Cloudflare will deploy and provide a `.pages.dev` URL.

---

### Option C: GitHub Pages (Completely Free & Integrated)
If you already use GitHub, you can host it directly from your repository.

1. Go to your repository's **Settings** tab.
2. Scroll down to **Pages** in the left sidebar.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose your branch (e.g., `main` or `master`) and directory (`/root`).
5. Click **Save**. Your site will be live at `https://<your-username>.github.io/<repo-name>/` in a few minutes.

---

## 3. Configuring a Custom Domain (`flanboyant.com`)

To link your custom domain bought on GoDaddy, Namecheap, Google Domains, or Route53:

### 3.1 DNS Records Configuration
On your hosting provider (Vercel, Cloudflare, etc.), add your custom domain. They will request you to add the following DNS records inside your domain registrar's panel:

1. **Apex Domain (`flanboyant.com`):**
   - **Type:** `A`
   - **Name:** `@` (or leave blank)
   - **Value:** (Use the IP address provided by Vercel/Cloudflare, e.g., `76.76.21.21` for Vercel)
2. **Subdomain (`www.flanboyant.com`):**
   - **Type:** `CNAME`
   - **Name:** `www`
   - **Value:** (Use the target address provided, e.g., `cname.vercel-dns.com` for Vercel)

*Your hosting provider will automatically provision a free, auto-renewing **SSL (HTTPS) Certificate** within minutes of the DNS records propagation.*

---

## 4. Local Test Before Deploy

To perform a final sanity check locally to verify the switch, links, and styling:

1. Run the local preview server in your terminal:
   ```bash
   npx -y serve . -p 3000
   ```
2. Open **[http://localhost:3000](http://localhost:3000)** in your browser.
3. Test clicking the **Candidates** and **Startups** buttons to make sure they switch instantly and the layout displays beautifully.
4. Open the site on a mobile view (using Chrome DevTools responsive emulator) to verify the layout columns stack perfectly into a single column flow.
