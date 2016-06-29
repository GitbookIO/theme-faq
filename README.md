# GitBook FAQ Theme

Theme for using GitBook to publish an FAQ or Knowledge Base. This theme works perfectly with search plugins (as the [default one](https://github.com/GitbookIO/plugin-search) or [algolia](https://github.com/GitbookIO/plugin-algolia)).

## Usage

This theme requires GitBook version 3 or later.

Add the theme to your book's configuration (`book.json`):

```js
{
    "plugins": [
        "theme-faq",
        "-fontsettngs",
        "-sharing"
        ]
}
```

**NOTE** `theme-faq` is not compatible with plugins that modify the toolbar (since there is no toolbar). Embedded search will not work as a result. 

This includes the default plugins `fontsettings` and `sharing` that need to be disabled explicitly (add a minus flag "-" before each plugin parameter).

If you disable both, the search bar will work. Otherwise the javascript fails when loading the page.

### Add relations between articles

Suggestions for other articles can be shown at the bottom of an article. 

Relationships are specified in the YAML frontmatter of a page.  Use the syntax of the markup language you are writing in.

#### For Markdown Topics
```md
---
related:
    - some/other/page.md
    - another_related_article.md
    
---

My article!
```

#### For AsciiDoc Articles
```adoc
---
related:

- some/other/page.md
- another_related_article.md

---

My article!
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

### Add a detailed README on your home page

The contents of your README is used as a short description on the home page of your FAQ. 

If you want to keep a separate and more detailed README file for your project, you can specify alternative README in the `book.json` file.

The detailed README is shown when you click on the FAQ from your writer's profile home page.

```json
{
  "structure": {
     "readme": "home-page-description.md"
  }
}
```
