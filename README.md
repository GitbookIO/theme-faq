# GitBook FAQ Theme

Theme for using GitBook to publish an FAQ or Knowledge Base. This theme works perfectly with search plugins (as the [default one](https://github.com/GitbookIO/plugin-search) or [algolia](https://github.com/GitbookIO/plugin-algolia)).

## Usage

This theme requires GitBook version 3 or later.

Add the theme to your book's configuration (`book.json`):

```js
{
    "plugins": [
        "theme-faq",
        "-fontsettings",
        "-sharing"
    ]
}
```

**NOTE** `theme-faq` is not compatible with plugins that modify the toolbar (since there is no toolbar). Embedded search will not work as a result. This includes the default plugins `fontsettings` and `sharing` that need to be disabled explicitly (add a minus flag "-" before each plugin parameter).

### Add relations between articles

Suggestions for other articles can be shown at the bottom of an article.

Relationships are specified in the YAML frontmatter of a page:

```md
---
related:
    - some/other/page.md
    - another_related_article.md

---

Content of my article!
```

### Add logo to header

Extend the theme by creating a file `_layouts/website/page.html` in your book with:

```html
{% extends template.self %}

{% block faq_header_brand %}
<img src="https://mywebsite.com/logo.png" height="30" />
{% endblock %}
```

### Add navigation links to the header

Extend the theme by creating a file `_layouts/website/page.html` in your book with:

```html
{% extends template.self %}

{% block faq_menu %}
<ul class="nav navbar-nav navbar-right">
    <li><a href="#">Contact us</a></li>
    <li><a href="#">Return to SuperWebsite</a></li>
</ul>
{% endblock %}
```

### Add a short description on the home page

The content of your `README` is used as a short description for the home page of your FAQ.

If you wish use a specific file for this description instead of your project's README, you can configure your `book.json` to do so:

```json
{
  "structure": {
     "readme": "home-page-description.md"
  }
}
```
