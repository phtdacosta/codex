source "https://rubygems.org"

# GitHub Pages builds this site with the classic (zero-config) pipeline.
# The github-pages gem pins Jekyll + the whitelisted plugins to the exact
# versions GitHub runs, so `what builds locally == what deploys`.
gem "github-pages", group: :jekyll_plugins

# Plugins used by the theme (all on the GitHub Pages whitelist).
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-paginate"
end

# Local preview server.
gem "webrick", "~> 1.8"

# Windows / JRuby niceties (harmless elsewhere).
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
