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

|               | GitHub README.md           | GitHub Pages via /docs |
| --- | --- | --- |
| sanitised raw | perfect                        | perfect  |
| naive         | ok but ugly github framed page | ok   |
| regeneration  | flaky                          | flaky    |

*(more detailed table on main [README.md](https://github.com/tcab/pagestest))*

Note:
- all "GitHub Pages via /docs" techniques need extra syntax `[![text](link)](link)` to the url to get clickable link
- perfect means "works, and has nice link to full browser page svg where you can zoom"
- all image updating for the "sanitised" and "naive" approaches seem to take a while - which could be a cache/etag/browser issue - but everything eventually updates. Sometimes manually visiting and refresh the https://raw.githubusercontent.com github view in browser helps the effects to ripple through). The Github Pages naive technique seems to be the slowest to update.


### 1 - "Sanitised raw" technique

```
https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true
```

Need to add `?sanitize=true` for this to work, as per [this post](https://github.community/t5/How-to-use-Git-and-GitHub/Embedding-a-SVG/td-p/2192):

![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

- works locally on dev machine
- works on github pages via /docs ✅
- CLICKING ON IMAGE - **does nothing** - no link is active! ❌ mitigation works ✅
- updates ok when .svg changes? 🤨  takes a while to update when underlying .SVG changed

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
- updates ok when .svg changes? 🤨  takes a while to update when underlying .SVG changed - **slowest to update**

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
- updates ok when .svg changes? only if `&cache=no` in url.

I thought maybe Github Pages hosting would improve the "regeneration" technique success rate, but its the same problem.  Overall its a flaky technique. In fact it might be even worse on Github Pages.

Even though it makes for more complex urls, try to mitigate lack of link problem with the advice:
> In other words, whatever the syntax for the image, treat that whole syntax as the text to link. So the ugly syntax also works: `[![alt text](image link)](web link)`

[![code map example 01](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/abulka/lcodemaps/master/plantuml/example-01.puml&fmt=svg)



## Links to other pages

[page2](page2.md)
