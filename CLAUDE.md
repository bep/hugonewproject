See background info in https://github.com/gohugoio/hugo/issues/14804

Project structure (CLI args):

--section: Root section name, e.g. "blog". Flag can be repeated for more root sections.
--page: Root page (e.g. "about"). Flag can be repeated for more root pages.

So with `hugonewproject --section blog --section news --page about --palette pastel`

We would create (in `txtar` format)

```txtar
-- content/blog/_index.md --
---
title: Blog
weight 10
---
-- content/news/_index.md --
---
title: Blog
weight 20
---
-- content/about/index.md --
---
title: About
weight 30
---
```

And for the `palette` option, we would hold a set of pretty presets that we would expand to:


```toml
[params.style.palette]
    primary = "#a8d8b9"
    accent  = "#f4a261"
    [params.style.palette.dark]
        primary = "#000000"
        accent  = "#fff"

```

The above works with the current Hugo, but we need to eventually look at  https://github.com/gohugoio/hugo/issues/14805 -- but that's outside the scope of this prototype.

The sections below defines the tasks needed to be done in this prototype:

## Establish a set of palette names

We need to establish a set of names for a palette with a pretty default for testing in the @template project (with a dark variant, see above). I'm not sure how many colors, I'm guessing 4 or 5. As to names, it would be great if there were some established convention that felt familiar for many, a big plus if supported by some great palette generators out there.

## Great a great lookng and flexible template for the generated site

See the files in @template for some initial structure.

The design needs to be solid, but neutral enough to be used for a wide variety of sites. It should also be flexible enough to be easily customized/extended by users. Focus heavily on getting a solid structure with a strong connection between CSS and the templates.

Use the current files as hints, but feel free to change the structure as needed. The goal is to have a solid foundation that can be easily extended and customized by users.

Some additional requirements:

* No external fonts or assets or frameworks.
* The design should be responsive and look good on both desktop and mobile.


