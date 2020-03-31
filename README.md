# pagestest
testing github pages

hi there.  [live demo](https://tcab.github.io/pagestest/).

see also the `hello.yml` file in .github/workflows which apparently spins up ubuntu and then runs some commands - every time you push?

Interesting, so when you have the 'github pages' set to main master, it just uses your normal `README.md` as its content.

So what if we add an `index.md` ? Yes, it then takes priority 👍

What about if we add `index.html` ?  Yes it does. 🧐 Which means if `index.html` is part of your project itself, then it will inadvertently be displayed.  Note that all auto magic theme style info is stripped when displaying `index.html` - presumably this gives you freedom to totally style as you wish.

## Ok, let's try a /docs subdir now....

Of course you have to change repo settings... 
And you have to re-select a theme, so that the `_config.yml` is created in the `/docs` dir.  Presumably you could move the `_config.yml` into the `/docs` dir instead of having to reselect the theme.

Works OK.

## Using the "minimal theme"
Doco on the minimal theme can be found [here](https://github.com/pages-themes/minimal) - it seems you need to:

Configuration variables

Minimal will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```yml
logo: [Location of the logo]
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```

Tip: The `[]` brackets are not needed and must be replaced with your content.
e.g.

```yml
theme: jekyll-theme-minimal
logo: https://user-images.githubusercontent.com/830777/76915877-dc9fa800-6912-11ea-8c1a-08a0ab767f1a.jpg
```

## Inserting Images

Great [tip](https://ardalis.com/add-images-easily-to-github): simply **paste** an image into a dummy GitHub *issue* and the markdown is created for you - discard the issue when done.  The image is __hosted somewhere internally inside GitHub__. 🤗




## SVG (github main page README.md)

Tested on:

- a regular github markdown page e.g. `README.md`
- a jeckyll generated github page markdown page
- locally in vscode markdown previewer
- TODO local jekyl hosted serving


### 1 - "Sanitised raw" technique

```
https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true
```

Need to add `?sanitize=true` for this to work, as per [this post](https://github.community/t5/How-to-use-Git-and-GitHub/Embedding-a-SVG/td-p/2192):

![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

- works locally on dev machine
- works on github main page README.md ✅
- nice link to full browser page svg where you can zoom ✅






### 2 - "Naive" technique

```
./docs/images/mvc-a-architecture.svg
```

![mvc-a-architecture](./docs/images/mvc-a-architecture.svg)

- works locally on dev machine
- works on main github README ✅
- CLICKING ON IMAGE - takes you to ugly github framed page  ❌
- Note that `?sanitize=true` not needed, though doesn't hurt.

Even though it makes for more complex urls, try to mitigate the **ugly github framed page** problem with the advice:
> In other words, whatever the syntax for the image, treat that whole syntax as the text to link. So the ugly syntax also works: `[![alt text](image link)](web link)`
[![mvc-a-architecture](./docs/images/mvc-a-architecture.svg)](./docs/images/mvc-a-architecture.svg)





### 3 - "Regeneration" from .puml technique

```
http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg
```

![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)

- works on main github README, but... too slow to refresh, sometimes image fails to appear probably due to timeout ✅😯
- CLICKING ON IMAGE works and takes you to some `https://camo.githubusercontent.com/...` url where you get the full screen SVG and can zoom ok ✅
- does not work locally on dev machine - at least not in vscode previewer.
- *may* work in local jekyll server but this project isn't set up with local jekill
