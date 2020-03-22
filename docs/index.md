# test of pages on GitHub served from /docs dir

Hi from the docs dir. 🤟

## Accessing jekyll data

**info1:** {{ site.info1 }}

**info2:** {{ site.info2 }}

Here is a string built using site data and filters:

{{ site.info2 | prepend:site.baseurl | upcase }}

Here is a for loop:

The var *site.data.people* is {{ site.data.people }}

{% for item in site.data.people %}
* {{ item.name }} of *{{ item.address }}* 
{% endfor %}
    
## Images

Opeth test image below:

![opeth-in-cauda-venenum-NB](https://user-images.githubusercontent.com/830777/76915877-dc9fa800-6912-11ea-8c1a-08a0ab767f1a.jpg)

## mvc-a architecture

![mvc-a-architecture](https://user-images.githubusercontent.com/830777/76916676-4c169700-6915-11ea-9157-c74e4b1ff234.png)

Full size png [here](https://user-images.githubusercontent.com/830777/76916676-4c169700-6915-11ea-9157-c74e4b1ff234.png)

Full size svg [here](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

## SVG

trying to get proper svg by uploading the image to github into the images folder and then finding the raw url - this doesn't work

![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg)

try again adding `?sanitize=true` as per [this post(https://github.community/t5/How-to-use-Git-and-GitHub/Embedding-a-SVG/td-p/2192)]:

![mvc-a-architecture](https://raw.githubusercontent.com/tcab/pagestest/master/docs/images/mvc-a-architecture.svg?sanitize=true)

works!

## changing SVG

once the file is in github it will have a raw link and that won't change when you update it.  Nice.  But will the pages site re-render the site correctly with the updated image or will it aggressively cache, like it does when you include svg file in regular readme in regular github pages?

Looks like it did change, but you have to change some text on the page, otherwise the page is cached - cos the svg *image url* is the same and there is no intelligence detecting it has changed. So change some text on the page instead. This is better than fiddling with imaginary image query strings on the image reference urls in order to try and trick github to re-render the page.

## Links to other pages

[page2](page2.md)
