---
url1: https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true
---
# test of pages on GitHub served from /docs dir

Hi from the docs dir. 🤟

## Accessing jekyll data

**info1:** {{ site.info1 }}

**info2:** {{ site.info2 }}

**url1** {{ page.url1 }}

Here is a string built using site data and filters:

{{ site.info2 | prepend:site.baseurl | upcase }}

### Here is a for loop:

The var *site.data.people* is 
```ruby
{{ site.data.people }}
```

{% for item in site.data.people %}
* {{ item.name }} of *{{ item.address }}* [{{ item.name }}](http://www.google.com)
{% endfor %}

## Images

Opeth test image below:

![opeth-in-cauda-venenum-NB](https://user-images.githubusercontent.com/830777/76915877-dc9fa800-6912-11ea-8c1a-08a0ab767f1a.jpg)

## mvc-a architecture

![mvc-a-architecture](https://user-images.githubusercontent.com/830777/76916676-4c169700-6915-11ea-9157-c74e4b1ff234.png)

Full size png [here](https://user-images.githubusercontent.com/830777/76916676-4c169700-6915-11ea-9157-c74e4b1ff234.png)

Full size svg [here](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)




## SVG (github pages via /docs)

Tested on:

- a regular github markdown page e.g. `README.md`
- a jeckyll generated github page markdown page
- locally in vscode markdown previewer
- TODO local jekyl hosted serving

### Summary

|               | normal GitHub README.md | GitHub Pages via /docs |
| sanitised raw | perfect                 | perfect (needs mitigation to get clickable link)    |
| naive         | ugly github framed page | perfect (needs mitigation to get clickable link)    |
| regeneration  | flaky                   | flaky (needs mitigation to get clickable link)    |

> perfect means "works, and has nice link to full browser page svg where you can zoom"
> mitigate means you need to add extra syntax to the url to make hyperlink work


### 1 - "Sanitised raw" technique

```
https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true
```

Need to add `?sanitize=true` for this to work, as per [this post](https://github.community/t5/How-to-use-Git-and-GitHub/Embedding-a-SVG/td-p/2192):

![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

- works locally on dev machine
- works on github pages via /docs ✅
- CLICKING ON IMAGE - **does nothing** - no link is active! ❌ mitigation works ✅


Even though it makes for more complex urls, try to mitigate lack of link problem with the advice:
> In other words, whatever the syntax for the image, treat that whole syntax as the text to link. So the ugly syntax also works: `[![alt text](image link)](web link)`

[![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

Here is an attempt at using jekyl page variable to simplify the url syntax of this image ref. WORKS! 😊

[![mvc-a-architecture]({{page.url1}})]({{page.url1}})

### 2 - "Naive" technique

```
./images/mvc-a-architecture.svg
```

![mvc-a-architecture](./images/mvc-a-architecture.svg)

- works on github pages via /docs ✅
- CLICKING ON IMAGE - **does nothing** - no link is active! ❌ mitigation works ✅
- works locally on dev machine
- note that `?sanitize=true` not needed, though doesn't hurt.

Even though it makes for more complex urls, try to mitigate lack of link problem with the advice:
> In other words, whatever the syntax for the image, treat that whole syntax as the text to link. So the ugly syntax also works: `[![alt text](image link)](web link)`

[![mvc-a-architecture](./images/mvc-a-architecture.svg)](./images/mvc-a-architecture.svg)




### 3 - "Regeneration" from .puml technique

```
http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg
```

![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)

- works on github pages via /docs, but.... ALSO too slow to refresh, ALSO sometimes image fails to appear probably due to timeout. ✅😯
- CLICKING ON IMAGE - **does nothing** - no link is active!  ❌  mitigation works ✅😱 (but slow and also risks timing out)
- does not work locally on dev machine - at least not in vscode previewer.
- *may* work in local jekyll server but this project isn't set up with local jekill

I thought maybe Github Pages hosting would improve the "regeneration" technique success rate, but its the same problem.  Overall its a flaky technique. In fact it might be even worse on Github Pages.

Even though it makes for more complex urls, try to mitigate lack of link problem with the advice:
> In other words, whatever the syntax for the image, treat that whole syntax as the text to link. So the ugly syntax also works: `[![alt text](image link)](web link)`

[![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)



## Regular GitHub serving vs. GitHub Pages serving

All the above techniques need to be tested both on:

- a regular github markdown page e.g. `readme.md`
- a jeckyll generated github page markdown page

because the serving of the pages may influence the reliability of each technique.

### local serving

Arguably we also need evidence re local serving success via:

- vscode markdown preview
- jekyll local server

## changing SVG

**TODO**

More investigation and clarification needed here.

once the file is in github it will have a raw link and that won't change when you update it.  Nice.  But will the pages site re-render the site correctly with the updated image or will it aggressively cache, like it does when you include svg file in regular readme in regular github pages?

Looks like it did change, but you have to change some text on the page, otherwise the page is cached - cos the svg *image url* is the same and there is no intelligence detecting it has changed. So change some text on the page instead. This is better than fiddling with imaginary image query strings on the image reference urls in order to try and trick github to re-render the page.

## Links to other pages

[page2](page2.md)
