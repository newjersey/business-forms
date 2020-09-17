# Business Forms

`https://forms.business.nj.gov/<FORM>`

Where `FORM` is the name of a directory with an `index.html` file, which generally contain a simple iframe pass-through to a hosted form.

- [Create a new form page](https://github.com/newjersey/business-forms/new/master/_forms?value=---%0Alayout%3A%20cognito%20%23%20or%20jotform%0Atitle%3A%20%0Adescription%3A%20%0Aform%3A%20%0A---%0A)
- [Create a new redirect page](https://github.com/newjersey/business-forms/new/master/_forms?value=---%0Alayout%3A%20redirect%0Alocation%3A%20%0A---%0A)

Web hosting through GitHub Pages with DNS pointed in Azure.

NOTE: when first pushing a new `docs/FORM/index.html` file, GitHub Pages tends to immediately resolve `/FORM/` but takes a few minutes for `/FORM` to establish a redirect. Just wait a few minutes for that to happen.

## Adding new forms

To add a new form, create a new html file in the `_forms` directory with filename for the desired path, such as `_forms/covid-recovery-consulting.html`. The file should include yaml metadata with the following options:

### Form pages

To generate an embedded form page, use the following metadata:
```yaml
---
layout:             # Either `cognito` or `jotform`
title:              # Form title used for the page meta title
description:        # Form description used for the page meta description (optional)
form:               # The form ID number, such as `73` for Cognito or `200804024879051` for Jotform
permalink:          # Explicitly specify the page URL instead of using the file name (optional)
---
```

[See an example](_forms/exemption.html).

The URL for the form will follow the directory structure and file name, unless a `permalink` value is specified in the form's metadata. For instance, a file at `_forms/covid-recovery-consulting.html` will generate a url like `https://forms.business.nj.gov/covid-recovery-consulting/`.

Files may be nested in directories, so `_forms/grant.html` will generate a URL like `/grant/`, and `_forms/grant/es.html` will generate a URL like `/grant/es/`.


### Redirects

To generate a redirect, use the following metadata:
```yaml
---
layout: redirect
location:           # the absolute URL of the redirect destination
permalink:          # Explicitly specify the page URL instead of using the file name (optional)
---
```

[See an example](_forms/grant/en.html).

## Legacy forms

Forms created before 9/2020 were full static pages. They are in the `_forms_legacy` directory and only copied when the site is built.

## Site configuration

A Google Analytics ID is specified in `_config.yml`.
