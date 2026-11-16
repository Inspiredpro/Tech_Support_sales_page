# TechSupport Website

| URL | File | Purpose |
|---|---|---|
| `/` | `index.html` | Laptop product discovery page |
| `/enquiry.html` | `enquiry.html` | Original customer enquiry page (unchanged, sends to the n8n webhook) |
| `/api/enquiry` | `api/enquiry.js` | Server-side route that forwards product enquiries to Make |

Edit products in `assets/products-data.js`.

## Deploy with GitHub and Vercel
1. Create a GitHub repository and push this folder so that `index.html` is in the repository root:
   ```
   git init
   git add .
   git commit -m "TechSupport site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USER/YOUR-REPO.git
   git push -u origin main
   ```
2. In Vercel, choose **Add New → Project**, import the repository and keep the defaults. Framework Preset: **Other**. Leave Build Command and Output Directory empty.
3. Before deploying, open **Environment Variables** and add `MAKE_WEBHOOK_URL` with your Make webhook URL (all environments).
4. Click **Deploy**. If you add the variable later, redeploy so it takes effect.

## Local testing
Copy `.env.example` to `.env.local`, set `MAKE_WEBHOOK_URL`, then run `npx vercel dev`.

## Still to do
- Replace the placeholder email and phone in `index.html`.
- Confirm real specs and prices and add product photos in `assets/img/`.
- Make the n8n webhook in `enquiry.html` use its production URL and allow your Vercel domain under CORS (Allowed Origins).
