# Jekyll URL Shortener

> :scissors: :link: This is a template repository for making URL Shorteners with Jekyll and GitHub Pages. Create short URLs that can be easily shared, tweeted, or emailed to friends. Fork this repo to get started.

View the URL Shortener in action:

* https://hlaueriksson.github.io/jekyll-url-shortener/

Read a blog post about the URL Shortener:

* https://conductofcode.io/post/introducing-jekyll-url-shortener/

Table of Contents:

  - [Getting Started](#getting-started)
    - [Domain](#domain)
    - [Repository](#repository)
    - [Configuration](#configuration)
    - [GitHub Pages](#github-pages)
    - [Links](#links)
  - [Built With](#built-with)
  - [Showcase](#showcase)
  - [Running Jekyll locally](#running-jekyll-locally)
  - [Customizing the redirect template](#customizing-the-redirect-template)

## Getting Started

Follow these steps to create your own URL Shortener:

1. Get a domain name
2. Configure the DNS for the domain
3. Fork or clone this repo
4. Edit the `_config.yml` file
5. Host on GitHub Pages
6. Create link pages

### Domain

Get a *(preferably short)* domain name from your favorite [registrar](https://www.icann.org/registrar-reports/accredited-list.html).

You probably want to use a [apex domain](https://help.github.com/articles/about-supported-custom-domains/#apex-domains) for your URL Shortener.

Go to your DNS provider and [setup the apex domain](https://help.github.com/articles/setting-up-an-apex-domain/).

If you create DNS `A` records, point to the these GitHub IP addresses:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

### Repository

[Fork](https://help.github.com/articles/fork-a-repo/) or [clone](https://help.github.com/articles/cloning-a-repository/) this repository.

I prefer to use the *domain name* as the name for the repository when I host a site on GitHub Pages.

Take the opportunity to edit the `Description` and `Website` of the repository. Also consider to add `topics` to categorize your repository.

You probably want to rewrite the content of this `README.md` file.

### Configuration

Edit the `_config.yml` file:

```yml
title: Jekyll URL Shortener
description: This is a URL Shortener made with Jekyll and GitHub Pages. Create short URLs that can be easily shared, tweeted, or emailed to friends. ✂️🔗
logo: /assets/img/logo.png
show_downloads: true
google_analytics:
theme: jekyll-theme-minimal

permalink: /:slug/

plugins:
  - jekyll-redirect-from

#repository: hlaueriksson/jekyll-url-shortener
```

Change the `title` and `description` to something you like. Consider to make your own `logo` by replacing the `/assets/img/logo.png` image.

The `show_downloads` flag indicates whether to provide downloads links for the code in the repository on the site.

Set the `google_analytics` tracking code if you are interested in the website traffic.

Read more about the `theme` at https://github.com/pages-themes/minimal

The global `permalink` for pages is set to `/:slug/`.

> Permalinks are the output path for your pages, posts, or collections. They allow you to structure the directories of your source code different from the directories in your output.

> Slugified title from the document’s filename (any character except numbers and letters is replaced as hyphen). May be overridden via the document’s `slug` front matter.

Read more about permalinks at https://jekyllrb.com/docs/permalinks/

It is the `jekyll-redirect-from` plugin that does the redirecting from the *short link* to the *target page*.

> Sometimes, you may want to redirect a site page to a totally different website.

Read more about the plugin at https://github.com/jekyll/jekyll-redirect-from

You can find more useful `plugins` to add at https://pages.github.com/versions/

When running Jekyll locally, uncomment the `repository` line and point to your own GitHub repo.

### GitHub Pages

Go to the repo [/settings](../../settings) and scroll down to the **GitHub Pages** section.

Set the `Source` to `master branch`: https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/

Point the `Custom domain` to your domain name: https://help.github.com/articles/using-a-custom-domain-with-github-pages/

This will create a `CNAME` file in the repo:

```txt
example.com
```

> Custom domains are stored in a `CNAME` file in the root of your repository. You can add or update your custom domain through your repository settings. You can also edit the file directly to update your custom domain.

Read more about adding a custom domain at https://help.github.com/articles/adding-or-removing-a-custom-domain-for-your-github-pages-site/

Make sure the `Enforce HTTPS` checkbox is ticked: https://help.github.com/articles/securing-your-github-pages-site-with-https/

> HTTPS provides a layer of encryption that prevents others from snooping on or tampering with traffic to your site. When HTTPS is enforced, your site will only be served over HTTPS.

Read more about GitHub Pages at https://pages.github.com

### Links

Create a new short link by creating a page: https://jekyllrb.com/docs/pages/

Create the file in the root of the repository.

This repository has one example, [`repo.md`](repo.md):

```md
---
title: Jekyll URL Shortener
redirect_to: https://github.com/hlaueriksson/jekyll-url-shortener
---
```

This results in:

* "Short" link: https://hlaueriksson.github.io/jekyll-url-shortener/repo/
* Target page:  https://github.com/hlaueriksson/jekyll-url-shortener
* *(Ironically the short link is 5 characters longer than the target page URL)*

The `title` could be used to describe the target page. Consider to take the *exact* title of the target page.

The `redirect_to` is the URL to the target page. This is the only [front matter](https://jekyllrb.com/docs/front-matter/) that is mandatory to make the short link work.

The file can have a `.md` (Markdown) or `.html` extension.

By default, the file name will be the *slug* of the short link. This behavior is configured in `_config.yml`.

If you want to use a different slug, set the `permalink` variable:

```md
permalink: /something/
```

Take the opportunity to get a real short slug by using *emojis*:

```md
permalink: /😻/
```

Find appropriate emojis to copy from https://www.emojicopy.com

## Built With

* Jekyll: https://jekyllrb.com
* jekyll-theme-minimal: https://github.com/pages-themes/minimal
* jekyll-redirect-from: https://github.com/jekyll/jekyll-redirect-from
* GitHub Pages: https://pages.github.com

## Showcase

| Repo | Site |
| :--- | :--- |
| https://github.com/hlaueriksson/hlaueriksson.me | https://hlaueriksson.me

## Running Jekyll locally

See https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/

Edit `_config.yml` and uncomment the `repository` line and point to your own GitHub repo.

Run:

```cmd
bundle exec jekyll serve
```

Browse:

http://localhost:4000

## Customizing the redirect template

See https://github.com/jekyll/jekyll-redirect-from#customizing-the-redirect-template

The template in this repository, [`_layouts/redirect.html`](_layouts/redirect.html):

```html
<!DOCTYPE html>
<html lang="en-US">
  {% if site.google_analytics %}
  <!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytics }}"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', '{{ site.google_analytics }}');
  </script>
  {% endif %}
  <meta charset="utf-8">
  <title>Redirecting&hellip;</title>
  <link rel="canonical" href="{{ page.redirect.to }}">
  <script>location="{{ page.redirect.to }}"</script>
  <meta http-equiv="refresh" content="0; url={{ page.redirect.to }}">
  <meta name="robots" content="noindex">
  <h1>Redirecting&hellip;</h1>
  <a href="{{ page.redirect.to }}">Click here if you are not redirected.</a>
</html>
```

The Google Analytics script is added at the top of the HTML.

If the `google_analytics` tracking code is specified in `_config.yml`, then the script is rendered in the redirect template.
