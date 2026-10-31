# Christmas Elf — public legal pages

Static pages for GitHub Pages: `index.html` (support + data deletion), `privacy.html`, `terms.html`.
Drafted from the app's actual behaviour (2026-10-30). **Not legal advice** — have them reviewed before release,
and update them whenever data handling changes (new provider, new data, new retention).

## Before publishing: replace every placeholder

| Placeholder | Example |
|---|---|
| `[OPERATOR NAME]` | Your full name or company name (the data controller) |
| `[COUNTRY]` | Türkiye |
| `[POSTAL ADDRESS]` | Contact address (required by GDPR/KVKK for the controller) |
| `[SUPPORT EMAIL]` | support@psmprep.com |
| `[EFFECTIVE DATE]` | 1 December 2026 |
| `[YEAR]` | 2026 |

Check nothing is left: `grep -n '\[[A-Z ]*\]' legal-site/*.html` must print nothing.

## Publish on GitHub Pages

1. Create a public repository (e.g. `christmas-elf-legal`) and upload the four files (`index.html`, `privacy.html`, `terms.html`, `style.css`).
2. Repository → Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)` → Save.
3. After a minute the site is at `https://<github-user>.github.io/christmas-elf-legal/`.

## Connect the app

Set the two public URLs (https only) for local runs in `apps/mobile/.env` and for builds in EAS:

```
EXPO_PUBLIC_PRIVACY_URL=https://<github-user>.github.io/christmas-elf-legal/privacy.html
EXPO_PUBLIC_TERMS_URL=https://<github-user>.github.io/christmas-elf-legal/terms.html
```

The same privacy URL goes into App Store Connect and Google Play Console; the index page doubles as the
support URL and Google Play's account-deletion URL.
