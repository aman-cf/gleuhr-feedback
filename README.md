# GLEUHR Product Feedback Form

The page customers open when they scan the QR code on a GLEUHR product.
Live address: **https://feedback.gleuhr.com/products-qr**

## What's in this folder

| File | What it does |
|------|--------------|
| `index.html` | The feedback form (product name, love meter, what they loved + comments, optional phone number). |
| `vercel.json` | Makes `/products-qr` open the form, and adds standard security settings. |

Responses are sent to the Google Sheet **GLEUHR Product Feedback** (tab: `Responses`) through a Google Apps Script web app. The script link is set near the bottom of `index.html` as `ENDPOINT`.

## Publishing (GitHub + Vercel)

1. Upload these files to a GitHub repository (private is fine).
2. In Vercel: **Add New → Project**, import the repository, keep the default settings (no build command, no framework), and click **Deploy**.
3. In the Vercel project: **Settings → Domains → Add** `feedback.gleuhr.com`.
4. Where gleuhr.com's DNS is managed, add the record Vercel shows. It's usually:
   - Type: `CNAME`, Name: `feedback`, Value: `cname.vercel-dns.com`
5. Wait for Vercel to show the domain as valid (usually a few minutes), then open
   https://feedback.gleuhr.com/products-qr and send a test response.

## Changing things later

- **Text or presets:** edit `index.html` and push to GitHub. Vercel republishes automatically.
- **Google Apps Script:** update the existing deployment (*Deploy → Manage deployments → Edit → Version: New version*) so the link stays the same. If you ever create a *new* deployment, paste its `/exec` link into `ENDPOINT` in `index.html`.
- The script must stay set to **Execute as: Me** and **Who has access: Anyone**.

## Privacy

The sheet stores customers' phone numbers. Share it only with the people who need it, and never make it public.
