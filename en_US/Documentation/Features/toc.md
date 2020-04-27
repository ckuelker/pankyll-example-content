---
title: Table Of Contents
linkTitle: TOC
type: doc
date: 2020-04-26
keywords:
    - TOC
categories:
    - Feature
tags:
    - TOC
    - Table Of Contents
    - HTML
    - Markdown
    - Pandoc
    - Pankyll
    - Themes
description: Table Of Contents feature documentation

---

The **table of contents** (TOC) feature collects the headings from a [Markdown]
file and creates a [HTML] table of contents that can be used by a theme to
display a table of contents. The TOC is created regardless if a page is
requesting it or not to display it. [Themes] are recommended but can not be
forced to obey the pages wish. For the **table of content** feature to be used
[Pankyll] needs to work hand in hand wit the theme and vice versa. Here are the
details on how the TOC is compiled.  (1) [Pankyll] uses  the [Pandoc] template
`toc.markdown` to extract the table of content from a [Markdown] file.  (2)
After this step again [Pandoc] is used to convert the **table of content** to
[HTML]. (3) This [HTML] snippet is than presented to the theme via the variable
`{{toc}}`. (4) Now for a theme to work, [Pankyll] supports the front matter key
`toc: True` or `toc: False`.  If `toc` is missing, it is treated as `toc:
False`. A theme who displays a **table of content** (which is optional) just
need to test if there is a `toc` content and if there is a `toc: True`.  The
following is an example from `pankyll-theme-newspaper`.

```html
{% if frontmatter.toc and toc %}
<div class="table-of-contents" id="table-of-contents-container">
    {% if cfg.toc[locale].text %}
    <strong>{{ cfg.toc[locale].text }}</strong>
    {% endif %}
{{ toc }}
</div>
{% endif %}

```

> If the theme uses the 'table of content' feature and you should add
> the language localization (translation) to your configuration. The
> following example is for English, German and Japanese.

```yaml
toc:
    en_US:
        text: Table Of Contents # alternative: Contents
    de_DE:
        text: Inhalt
    ja_JP:
        text: 目次
```

[HTML]: https://en.wikipedia.org/wiki/HTML
[Markdown]: https://en.wikipedia.org/wiki/Markdown
[Pandoc]: https://pandoc.org/
[Pankyll]: https://www.pankyll.org/
[Themes]: /en_US/Pankyll-Themes/