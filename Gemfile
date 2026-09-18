source "https://rubygems.org"

# Plain, modern Jekyll instead of the "github-pages" gem — that gem
# pins to Jekyll 3.9 / Liquid 4.0.3 to mirror GitHub's old legacy
# build pipeline, which breaks on current Ruby (calls to `tainted?`,
# a method Ruby removed in 3.2+). Deploying via GitHub Actions (see
# .github/workflows/pages.yml) means the exact Jekyll version no
# longer needs to match GitHub's pipeline — we control it directly.
gem "jekyll", "~> 4.3"
gem "webrick"
gem "jekyll-feed"
gem "jekyll-sitemap"
