source 'https://rubygems.org'

require 'json'
require 'open-uri'

gem 'jekyll'
gem 'jekyll-sitemap'
gem 'octopress', '~> 3.0.0.rc.12'
gem 'rouge'

versions = JSON.parse(open('https://pages.github.com/versions.json').read)
gem 'github-pages', versions['github-pages']
