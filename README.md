# pagestest
testing github pages

hi there.

see also the `hello.yml` file in .github/workflows which apparently spins up ubuntu and then runs some commands - every time you push?

Interesting, so when you have the 'github pages' set to main master, it just uses your normal `README.md` as its content.

So what if we add an `index.md` ? Yes, it then takes priority 👍

What about if we add `index.html` ?  Yes it does. 🧐 Which means if `index.html` is part of your project itself, then it will inadvertently be displayed.  Note that all auto magic theme style info is stripped when displaying `index.html` - presumably this gives you freedom to totally style as you wish.

## Ok, let's try a /docs subdir now....

Of course you have to change repo settings... 
And you have to re-select a theme, so that the `_config.yml` is created in the `/docs` dir.  Presumably you could move the `_config.yml` into the `/docs` dir instead of having to reselect the theme.

Works OK.

Doco on the minimal theme can be found [here](https://github.com/pages-themes/minimal) - it seems you need to:

Configuration variables

Minimal will respect the following variables, if set in your site's `_config.yml`:

```
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```
logo: [Location of the logo]
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```



