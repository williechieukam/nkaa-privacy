# Nkaa — Privacy Policy

Public hosting for the [Nkaa](https://github.com/williechieukam/vendor-ledger) app
privacy policy, served via GitHub Pages for the Google Play Store listing.

**Live URL:** https://williechieukam.github.io/nkaa-privacy/

The page (`index.html`) is the canonical, publicly linkable privacy policy. The source
of truth for the wording lives in the app repo at `docs/privacy-policy.md`; keep the two
in sync when the policy changes.

## Design

The page uses the app's design system, so it reads as the same product. Everything is
self-contained — no CDN, no analytics, no third-party requests, which is the least a
privacy policy can do.

**Color** — the "Grassfields regalia" palette from
`app/src/main/kotlin/app/vendorledger/android/ui/theme/Color.kt`. Each CSS token carries
its Kotlin name in a comment. The app's rule that green and red stay reserved for money
direction holds here too: containers and labels use soft indigo, and Laterite appears
only on the passphrase warning, where it means the same thing as `error` in the app.

**Type** — Bricolage Grotesque for headings and IBM Plex Sans for everything else,
matching `ui/theme/Type.kt`. The date uses `tnum`, the app's `tabularFigures()`.

**Fonts** — `fonts/*.woff2` are subsets of the TTFs in
`app/src/main/res/font`, cut to the Latin ranges this page needs (74 KB for four faces,
down from 603 KB). Both families are SIL OFL 1.1; see `fonts/OFL.txt`. To regenerate
after a font change in the app repo, `pip install fonttools brotli` and re-run
`pyftsubset` per the ranges recorded in `fonts/OFL.txt`.

When changing the stylesheet, keep the `@media (prefers-color-scheme: dark)` block last
and let it redefine **only** `:root` tokens. It previously sat above the rules it meant
to override and silently lost the cascade, which left the permission chips illegible in
dark mode.
