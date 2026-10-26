# Pushman product site

This dependency-free static site is the source for `https://pushman.io`.
It follows the private Pushman design guidelines while publishing only supported product behavior.

The homepage is indexable and uses `https://pushman.io/` as its canonical URL.
Its Open Graph and summary card reuse the public 512×512 app icon. Keep the
metadata, `robots.txt`, and sitemap aligned when adding public pages. Account,
pairing, and approval screens belong to the separate application site.

Deployment is managed separately. Keep only public static assets here. Do not add
analytics, credentials, unreleased plans, or production infrastructure details.
