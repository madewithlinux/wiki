# jekyll static wiki on github pages
tags: [[webdev]]
- [jekyll static wiki on github pages](#jekyll-static-wiki-on-github-pages)
- [TODO features](#todo-features)
- [features that I have added or implemented](#features-that-i-have-added-or-implemented)
  - [backlinks (WIP)](#backlinks-wip)
  - [list of all pages](#list-of-all-pages)
  - [turn raw urls into links automatically](#turn-raw-urls-into-links-automatically)
  - [generate and serve the site locally](#generate-and-serve-the-site-locally)
- [reference links](#reference-links)


# TODO features
* tags
  * (could implement with backlinks?)
* categories
* list of recent changes
* hide `_site/` better, so that vscode markdown wikilink add foam plugin thing doesn't try to use those markdown files to link to

# features that I have added or implemented

## backlinks (WIP)
a kind-of implementation of backlinks is in [`_layout/page.html`](https://github.com/madewithlinux/wiki/blob/master/_layouts/page.html). It looks for wikilinks (links like `[[this]]`) in markdown or html.

This implementation is very hacky. I don't think there's a good way of actually doing this with the standard github-pages jekyll config, I think it's worth setting up a CI-server and using a plugin or something to make backlinks automatically (such as maybe this one: https://github.com/raghuveerdotnet/simply-jekyll )

Another problem with doing it this way is that every page must search through the content of every other page to look for links.
(so that's $O(n^2)$ on the number of pages, right?)
This would probably be a big problem if I had a significant number of pages. So, good luck with that, future-joules.



## list of all pages
I can do this with a [liquid](https://shopify.github.io/liquid/) template:
```liquid
{% raw %}
{% for page in site.pages %}
{%- if page.published != false and page.title != nil -%}
* [[{{ page.title }}]({{ page.url }})]
{% endif -%}
{% endfor %}
{% endraw %}
```

## turn raw urls into links automatically
enable `autolink` extension in `_config.yml` (ref https://github.com/github/jekyll-commonmark-ghpages)


## generate and serve the site locally
1. install ruby
2. add `Gemfile`:
  ```ruby
  source 'https://rubygems.org'
  gem 'github-pages', group: :jekyll_plugins
  ```
3. `bundle install`
4. run it like:
  ```bash
  bundle exec jekyll serve --livereload
  ```
5. optional: automate it with a `justfile`
  ```
  localhost:
    bundle exec jekyll serve --livereload
  ```


# reference links
* jekyll docs https://jekyllrb.com/docs/variables/
* liquid template docs https://shopify.github.io/liquid/
* jekyll's docs on their additions to liquid templates https://jekyllrb.com/docs/liquid/
* how actually baseurl works https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/



