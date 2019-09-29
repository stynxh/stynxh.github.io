---
layout: post
published: false
title: Setting the category github blog with beautiful jekyll theme
---
If you use the Beautiful Jekyll theme on your Github blog, you can set the categories as follows.

## Step 1

Edit the **_config.yml** file

~~~
...
...
...

# --- Navigation bar options --- #

# List of links in the navigation bar

navbar-links:
  Category:
    - TroubleShooting: "/category/troubleshooting"
    - Study: "/category/study"

...
...
...
~~~

{: .box-note}
**Note:** If a category is added, modify the **_config.yml** file again by adding a new category name.


## Step 2

Create a **/category** directory and create an .md file with each category name.

![2019-09-29-jekyll-theme-add-category_1.png]({{site.baseurl}}/img/attached-post/2019-09-29-jekyll-theme-add-category_1.png)

![2019-09-29-jekyll-theme-add-category_2.png]({{site.baseurl}}/img/attached-post/2019-09-29-jekyll-theme-add-category_2.png)


The contents of the .md file are as follows.  

~~~
---
layout: category
title: study
permalink: category/study
---
~~~

{: .box-note}
**Note:** If a category is added, add a .md file with the new category name.


## Step 3

Create a **category.html** file in the **/ _layouts** directory and write:

~~~
---
layout: default
---
<ul class="posts-list">  
  {% assign category = page.category | default: page.title %}
  <h4>Posts in {{ category }} ({{ site.categories[category].size }})</h4> 
  {% for post in site.categories[category] %}   
    <li>
      <a class="post-title" href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      <small><time>
        {{ post.date | date:"%F" }} {{ post.date | date: "%a" }}.
      </time></small>
    </li>
  {% endfor %}
</ul>
~~~



## Result

![2019-09-29-jekyll-theme-add-category_3.png]({{site.baseurl}}/img/attached-post/2019-09-29-jekyll-theme-add-category_3.png)

![2019-09-29-jekyll-theme-add-category_4.png]({{site.baseurl}}/img/attached-post/2019-09-29-jekyll-theme-add-category_4.png)

