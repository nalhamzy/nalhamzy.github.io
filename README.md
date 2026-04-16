# nalhamzy.github.io — root hosting

This is the **apex** GitHub Pages site. Its only job is to serve the
`app-ads.txt` file at `https://nalhamzy.github.io/app-ads.txt`.

## Why this file matters

Google AdMob needs to verify that you (the developer) authorize the
publisher-ID that's shipped inside your Flutter apps. It does this by
crawling `<developer-website>/app-ads.txt` — where `<developer-website>`
is the "Website" URL you set in Play Console + App Store Connect for
each app.

## How each app points here

For every app that serves AdMob ads, set the Play Console / App Store
Connect **Developer website** field to either:

- `https://nalhamzy.github.io/` (simplest — this file is at the root), **or**
- `https://nalhamzy.github.io/<app-slug>/` — in which case the crawler
  can fall back to root-level app-ads.txt. We also mirror it into each
  app's `/docs/app-ads.txt` so subdir crawlers find it locally too.

## Currently-authorized publisher

```
google.com, pub-4401199263287951, DIRECT, f08c47fec0942fa0
```

This is the single AdMob publisher ID used across:
- ChromaPulse (`ca-app-pub-4401199263287951~9761947747`)
- Color Chaos
- Silver Suite (once production app ID is provisioned under the same account)

Parenting Pulse is **ad-free** and does not use this publisher.

## Verifying

1. In AdMob → **Apps → App → App settings → app-ads.txt**.
2. Copy the required record.
3. Paste into this file (already done above).
4. Wait up to 24 hours. Status should flip from "Not found" → "Authorized."

## When to update

Add a new line whenever you add a new ad mediator (e.g. AppLovin,
Unity Ads). Each mediator provides a record.

## Don't
- Don't remove this file — your ad fill rate will drop immediately.
- Don't rename — the filename is literal (`app-ads.txt`, no dot-prefix).
- Don't put it behind Jekyll — GitHub Pages serves static files at the
  root verbatim.
