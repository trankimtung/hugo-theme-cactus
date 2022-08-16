## Cactus 2

A minimalist hugo theme for personal blogs.

Fork from hexo theme [cactus](https://github.com/probberechts/hexo-theme-cactus) created by @probberechts.
[Original version](https://github.com/monkeyWzr/hugo-theme-cactus) ported to Hugo by @monkeyWzr.

[Live demo on Github pages](https://trankimtung.com/hugo-theme-cactus-2/).

## Installation

1. Clone Cactus 2 into `themes` folder.

```
git clone https://github.com/trankimtung/hugo-theme-cactus-2.git themes/cactus-2
```

2. Update Hugo config to use `cactus-2` theme.

```yaml
# config.yaml

theme: cactus-2
```

3. Customize Cactus 2 to your preference. See **Customization** section below or
   a [complete config sample](demo/config.yaml)
4. Build and test your website.

```shell
hugo server
```

5. Publish your website. See Hugo's documentation: [Hosting & Deployment](https://gohugo.io/hosting-and-deployment/)

## Customization

### Color themes

```yaml
# config.yaml

params:
  colortheme: "white" # dark, light, white, or classic
```

### Custom CSS

```yaml
params:
  css:
    - "css/custom.css"
```

You can add multiple custom stylesheets which will be loaded after the main theme css.
For example, the above line will load the CSS-file placed at `/static/css/custom.css`.

### Navigation

```yaml
# Main menu which appears below site header.
menu:
  main:
    - name: Home
      url: /
      weight: 1
    - name: All posts
      url: /posts
      weight: 2
    - name: Tags
      url: /tags
      weight: 3
    - name: About
      url: /about
      weight: 4
```

### Homepage settings

* description: description will be displayed in the homepage. Markdown syntax is supported in the description string.

```yaml
params:
  description: >-
    Hugo is a general-purpose website framework. Technically speaking, Hugo is a
    static site generator. Unlike systems that dynamically build a page with
    each visitor request, Hugo builds pages when you create or update your
    content. Since websites are viewed far more often than they are edited, Hugo
    is designed to provide an optimal viewing experience for your website’s end
    users and an ideal writing experience for website authors.
```

* set your main section (used as the link for the "writings" title on the homepage)

```yaml
params:
  mainSection: posts
```

* change the default main section title from Writings, to something else:

```yaml
params:
  mainSectionTitle: Blog
```

* Show only the 5 most recent posts (default)

```yaml
params:
  showAllPostsOnHomePage: false
  postsOnHomePage: 5

```

* show all posts

```yaml
params:
  showAllPostsOnHomePage: true
  postsOnHomePage: 5 # this option will be ignored
```

* show tags overview (default) or not

```yaml
params:
  tagsOverview: true
```

* display the table of contents inline on blog posts, rather than as part of the navigation menu:

```yaml
params:
  tocInline: true
```

* show projects list (default) or not.

```yaml
params:
  showProjectsList: true
  projectsUrl: 'https://github.com/monkeyWzr'
```

Projects section will not be shown if no data file is detected. See [Projects list](#projects-list) below.

### Projects list

Create your projects data file `data/projects.yaml|toml|json`. Hugo support yaml, toml and json formats.
for former hexo cactus users: please assign your json array to a `list` key.

for example, `data/projects.json`:

```json
{
  "list": [
    {
      "name": "Hexo",
      "url": "https://hexo.io/",
      "desc": "A fast, simple & powerful blog framework"
    },
    {
      "name": "Font Awesome",
      "url": "http://fontawesome.io/",
      "desc": "The iconic font and CSS toolkit"
    }
  ]
}
```

### Social media links

```yaml

params:
  social:
    - name: github
      link: 'https://github.com/trankimtung'
    - name: email
      link: contact@trankimtung.com # no need for "mailto:" at the start
    - name: linkedin
      link: 'https://www.linkedin.com/in/trankimtung/'
```

The `name` key expects the name of a [Font Awesome icon](https://fontawesome.com/icons?d=gallery&s=brands).

### Copyright

Assign your copy right to `.Site.Copyright`. Cactus will append current year to the head.

TODO: Customizable copyright year

```yaml
copyright: "Tran Kim Tung" # cactus theme will use site title if copyright is not set
```

### Comments

Comments is disabled by default. Enable comments in your `.Site.Params`.

```yaml
params:
  comments:
    enabled: true
```

You can also enable/disable comments per post. in your posts' front matter, add:

```yaml
comments: true
```

The site config is ignored when `comments` option exists in front matter.

The default engine is disqus. **By now only disqus is supported in cactus.** I will add more options sooner or later.
See [Comments Alternatives](https://gohugo.io/content-management/comments/#comments-alternatives)

Before using disqus, you need to register and get
your [disqus shortname](https://help.disqus.com/en/articles/1717111-what-s-a-shortname). Assign your shortname
in `.Site.disqusShortname`, or cactus will use `.Site.Title` by default.

```
disqusShortname = "wzr" # cactus will use site title if not set
```

### highlight

Use hugo's built-in [syntax highlighting](https://gohugo.io/getting-started/configuration-markup#highlight).

default config:

```yaml
markup:
  highlight:
    codeFences: true
    guessSyntax: false
    hl_Lines: ''
    lineNoStart: 1
    lineNos: false
    lineNumbersInTable: true
    noClasses: true
    style: monokai
    tabWidth: 4
```

### Analytics

Cactus uses hugo's bulit in analytics templates.
Check [hugo's documents](https://gohugo.io/templates/internal#google-analytics) for details.

Set you tracking id in your site config.

```yaml
googleAnalytics: "UA-XXXXXXXX-XX" # or G-XXXXXXXX if you are using Google Analytics v4 (gtag.js)
```

If you are using Google Analytics v3 (analytics.js), you can switch to asynchronous tracking by
set `params.googleAnalyticsAsync` to `true`.

```yaml
params:
  googleAnalyticsAsync: true # not required
```

### RSS

The rss feed is not generated by default. you can enable it in your site config:

```yaml
params:
  rss: true
```

The rss link will be `https://example.com/index.xml` assuming your `baseURL` is set to `https://example.com/`

Please also check [Configure RSS](https://gohugo.io/templates/rss/#configure-rss)

### Mathjax

Cactus supports mathjax. Just add `mathjax` option in your site config:

```yaml
params:
  mathjax: true
```

You can also enable/disable mathjax per post. In your posts' front matter, add:

```yaml
mathjax: true # or false
```

The site config will be ignored when `mathjax` option exists in front matter.

### Archive

Pagination on posts archive can be disabled to show all posts in chronological order

```yaml
params:
  showAllPostsArchive: true # default false
```

## License

[MIT License](LICENSE)
