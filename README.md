# Mona & Tim — Wedding Website

A single-page wedding site for **GitHub Pages**. No build tools or paid website builder required.

## Preview locally

In this folder run `python3 -m http.server 8000`, then open `http://localhost:8000`. (Opening index.html directly may prevent gallery.json loading.)

## Publish

1. Create a **public** GitHub repository, e.g. `mona-and-tim-wedding`.
2. Upload the **contents** of this folder to the repository root (not the ZIP file itself).
3. Go to **Settings → Pages → Build and deployment → Deploy from a branch**, select `main` and `/ (root)`, and Save.
4. Test the `github.io` preview address before connecting your domain.
5. In **Settings → Pages → Custom domain**, enter `www.monaandtimwedding.com`. Follow GitHub's current custom-domain instructions for DNS records at Namecheap. Set up the apex domain too if desired. Enable **Enforce HTTPS** when available. Do not change DNS until ready to switch away from Canva.

## Replace the temporary reference imagery

**Important:** Current `assets/*.webp` files were cropped from the user-provided Canva screenshots, so they are **preview-quality only**. The hero also contains the original lettering baked into the screenshot. Replace with your original high-resolution photos before public launch.

- Replace `assets/hero-reference.webp` with your real hero image, and update the CSS `.hero` background path if the filename changes. If the new hero has no lettering, add a text overlay in `index.html` or ask for that update.
- Put optimized display-sized WebP/JPEG photos into `assets/` (roughly 1600–2200 px longest edge for gallery images).
- Edit `gallery.json`: `professional` and `guest` arrays each list `{ "src": "assets/name.webp", "alt": "description" }`. Optional `download` is a full-resolution file share URL for **individual** photo downloads.
- The **first 12** professional photos in `gallery.json` appear on the homepage. All photos in each array appear in the modal gallery. The guest section uses one featured thumbnail; replace `assets/guest-reference.webp` with your preferred guest photo.
- To change the 12 featured photos, reorder the `professional` array so the preferred 12 come first.

## Vimeo and UGREEN NAS links

Edit `config.js`:

- `vimeo.guestbook` and `vimeo.film`: numeric Vimeo video IDs (for example, `123456789`). For Vimeo links with privacy hashes, embedding may require additional parameters; ask for help configuring those.
- `downloads.professional`, `downloads.guest`, `downloads.guestbook`, `downloads.film`: **public, read-only HTTPS share URLs** from the UGREEN NAS.
- Blank links are intentionally hidden until configured; the video placeholders stay visible until Vimeo IDs are supplied.
- For individual-photo download links, add a `download` property to each `gallery.json` item. UGREEN public share pages may open an intermediate download page rather than triggering a direct browser download.

Do not expose NAS admin login, open router ports unnecessarily, or publish private files in the GitHub repository. Public GitHub repositories make included images and source files publicly accessible. Test all NAS share links in a private/incognito window. Confirm the UGREEN sharing service supports the desired access duration.

## Notes

- Free GitHub Pages is intended for static sites and has published usage limits; keep original-resolution media on the NAS, not in the repository.
- Vimeo streaming is separate from downloading the original videos on your NAS.
- This is an initial functional prototype, not yet the final high-resolution photo gallery.
