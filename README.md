# Apps by Narayan

A dependency-free static website for Narayan Kuleindiren’s iOS apps, hosted with GitHub Pages at [apps.narayankuleindiren.com](https://apps.narayankuleindiren.com).

## Routes

- `/` — app directory
- `/scene/` — Scene overview and support
- `/scene/privacy/` — Scene privacy policy
- `/since-then/` — Since Then overview and support
- `/since-then/privacy/` — Since Then privacy policy
- `/app-ads.txt` — Google Mobile Ads publisher declaration

## Local preview

From the repository root, run:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/`. Use a local server rather than opening the HTML files directly, because links and assets use root-relative paths.

## Deployment

GitHub Pages publishes directly from the root of the `main` branch. The repository includes:

- `CNAME` for `apps.narayankuleindiren.com`
- `.nojekyll` so GitHub Pages serves files without Jekyll processing
- `app-ads.txt` at the hostname root

In the repository’s **Settings → Pages**, set **Source** to “Deploy from a branch”, choose `main` and `/ (root)`, then save. The custom domain should be `apps.narayankuleindiren.com`.

DNS should contain this record:

| Type | Host | Target |
| --- | --- | --- |
| CNAME | `apps` | `narayan-k.github.io` |

Once DNS has propagated and GitHub reports a successful DNS check, enable **Enforce HTTPS** in the Pages settings.

## Adding another app

1. Create a lowercase, hyphenated directory such as `new-app/` with its own `index.html`.
2. Reuse `/assets/styles.css` and `/favicon.svg`.
3. Add a card to the homepage.
4. Add a privacy route at `new-app/privacy/` when required.
5. Update this route list and verify every internal link before publishing.

## Privacy policy maintenance

The Scene policy reflects the app implementation reviewed on 6 October 2026: local `UserDefaults` persistence, no accounts, Google Mobile Ads, Google User Messaging Platform, ads in Endless and Zen, and an ad-free Daily mode.

The Since Then policy reflects the app implementation reviewed on 6 October 2026: local App Group `UserDefaults` persistence, local notifications, StoreKit purchases and optional consent-gated PostHog analytics. Review each policy whenever the corresponding app’s data handling, SDKs or behaviour changes.

This privacy policy is a plain-language technical summary, not legal advice. It should receive human/legal review before being treated as final.
