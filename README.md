# slacken-site

Static GitHub Pages site for **Slacken**, an iOS puzzle game.

Its one job right now is hosting the privacy policy that the App Store
listing and the app's Settings screen link to.

| Path                 | Served at                                              |
|----------------------|--------------------------------------------------------|
| `index.html`         | `https://jinyangwang27.github.io/slacken-site/`         |
| `privacy/index.html` | `https://jinyangwang27.github.io/slacken-site/privacy`  |

Plain HTML with inline CSS — no build step, no dependencies, no
JavaScript. `.nojekyll` disables Jekyll processing so the files are
served exactly as committed.

## Enabling Pages

Publishing is a repository setting and cannot be done from a pull
request. After merging, go to **Settings → Pages** and set:

- **Source:** Deploy from a branch
- **Branch:** `main` / `(root)`

Then confirm the policy URL returns 200:

```
curl -I https://jinyangwang27.github.io/slacken-site/privacy
```

The App Store listing and `SettingsView.swift` in the app repo both
point at that exact URL, so it must resolve before submitting for
review.

## Editing the policy

`privacy/index.html` is the published copy. The source of truth lives in
the app repo at `Store/privacy-policy.md`; keep the two in sync and bump
the effective date in both whenever the policy changes materially.
