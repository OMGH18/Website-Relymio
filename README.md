# Webpage-Relymio

Public, static, bilingual (English/French) website for Relymio, kept separate from the private mobile-app repository. It is prepared for `relymio.djabelsolutions.fr` and can be published directly through GitHub Pages.

## Deploy with GitHub Pages

The repository includes `.github/workflows/pages.yml`. It publishes the repository root whenever `main` changes.

1. Push the repository to GitHub.
2. In the repository, open **Settings → Pages** and choose **GitHub Actions** as the source.
3. Wait for the `Deploy website to GitHub Pages` workflow to complete.
4. GitHub will provide the temporary `*.github.io` URL. No IONOS change is needed for this step.

If the GitHub repository is not created yet, create an empty **public** repository named `Webpage-Relymio` under `OMGH18`, then connect and publish this local repository:

```bash
git remote add origin git@github.com:OMGH18/Webpage-Relymio.git
git add .
git commit -m "Prepare Relymio public website"
git push -u origin main
```

When the domain is ready, configure it in GitHub Pages and add the DNS record requested by GitHub in IONOS. `CNAME.example` contains the intended hostname; copy it to `CNAME` only when the custom domain is actually attached.

## Routes

The repository root is the static document root. The required public routes are:

- `/` — product presentation;
- `/legal.html?doc=privacy` — privacy policy;
- `/legal.html?doc=terms` — terms of use;
- `/legal.html?doc=notice` — legal notice;
- `/screens.html` — visual product tour of the native app screens and code map.

The language switcher stores only the visitor’s language choice in `localStorage`. No website analytics script is installed by default. If analytics is added later, obtain consent before loading it and keep the website events separate from private app content.

Before going live, replace the legal placeholders for the exact legal address, publishing director and web host details, then have the legal texts reviewed by a qualified lawyer.

## Local preview

Because this is a static site, serve the repository root with any static server, for example `python -m http.server 8080`, then open `http://localhost:8080`.

## Repository boundary

The app source remains in `Relymio-app`. This repository intentionally contains only public website assets, public legal pages, the app-screen tour and the GitHub Pages workflow. Do not put private keys, RevenueCat secrets, PostHog project secrets or Supabase service-role credentials here.
