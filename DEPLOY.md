# DrillFit Site — Deploy & drillfit.com Cutover

Static site (HTML/CSS/JS, no build step). Hosts free on GitHub Pages. Three pages:
`index.html` (landing), `privacy.html`, `support.html`.

## Before you go live — fill in these

1. **App Store URL.** Search `idXXXXXXXXXX` in `index.html` (3 spots — header, hero, final CTA)
   and replace the whole URL with your real listing URL once the app is live, e.g.
   `https://apps.apple.com/us/app/drillfit/id6480000000`.
2. **Screenshots.** See `assets/screenshots/README.md` — drop in your build-88 captures
   and swap the placeholder divs for `<img>` tags (instructions in that README).
3. **Support email.** The pages use `support@drillfit.com`. If that mailbox doesn't exist yet,
   set it up (or change the address) — Apple's support URL should lead somewhere a user can actually reach you.

## Deploy to the EXISTING GitHub Pages repo (no domain change yet — safe anytime)

This just updates the current live site (sidarth1gaonkar2-creator.github.io/drillfit-site/).
Replace the repo's files with these and push. The `#privacy` anchor still works
(privacy.html has `id="privacy"`, and the old `...drillfit-site/privacy.html` URL is unchanged),
so your CURRENT App Store privacy/support URLs keep resolving. **This does not touch the URLs
Apple reviewed against — safe to do now.**

## drillfit.com cutover — do this AFTER the app launch is confirmed live

The order matters so your live App Store privacy/support links never break.

1. **Buy/own drillfit.com** (if not already).
2. **Add the custom domain on GitHub Pages:** repo → Settings → Pages → Custom domain →
   enter `drillfit.com` → Save. This creates a `CNAME` file in the repo (a `CNAME` file is
   included here with `drillfit.com` — keep it if you use the apex domain).
3. **DNS:** at your domain registrar, point the apex (`@`) to GitHub Pages IPs:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
   And add a `CNAME` record for `www` → `sidarth1gaonkar2-creator.github.io`.
4. **Enable HTTPS** in GitHub Pages settings (wait for the cert to provision — can take a bit).
5. **Verify** `https://drillfit.com`, `https://drillfit.com/privacy.html`, and
   `https://drillfit.com/support.html` all load.
6. **THEN update App Store Connect** (with your next version submission — the v1.1/build 89 one):
   - App Privacy → Privacy Policy URL → `https://drillfit.com/privacy.html`
   - App Information → Support URL → `https://drillfit.com/support.html`
   Do this step LAST — only after drillfit.com is confirmed serving those pages.
7. **Keep the old GitHub Pages URLs working** (don't delete the repo / Pages) so any existing
   links don't 404. GitHub Pages will redirect the `github.io` URL to the custom domain automatically.

## Notes
- No framework, no dependencies — just open `index.html` to preview locally.
- Fonts load from Google Fonts (Oswald, Inter, JetBrains Mono).
- The rank-ladder scroll-reveal respects `prefers-reduced-motion` (shows all rungs immediately if set).
- Insignia are inline SVG (the real rank insignia, carried over from the prior site).
