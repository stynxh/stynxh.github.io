---
layout: post
published: true
title: github blog with Beautiful Jekyll 테마 카테고리 설정
date: '2019-09-29'
category:
  - study
tags:
  - github blog
  - jekyll
  - beautiful-jekyll theme
---
Github 블로그에 Beautiful Jekyll 테마를 사용할 경우 다음과 같이 카테고리를 설정할 수 있다.

## Step 1

**_config.yml** 파일 수정

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
**Note:** 추후 카테고리가 추가될 경우, 새로운 카테고리 이름을 추가하여 _config.yml 파일을 다시 수정한다.


## Step 2

/category 디렉토리를 만들고 각 카테고리 이름으로 .md 파일을 만든다.

![/_posts/attached-img/2019-09-29-jekyll-theme-add-category_1.png]

![_posts/attached-img/2019-09-29-jekyll-theme-add-category_2.png]

.md 파일의 내용은 다음과 같다.  

~~~
---
layout: category
title: study
permalink: category/study
---
~~~

{: .box-note}
**Note:** 추후 카테고리가 추가될 경우, 새로운 카테고리 이름으로 .md 파일을 추가해준다.


## Step 3

/_layouts 디렉토리에 **category.html** 파일을 만들고 다음과 같이 작성한다.

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


## 결과

![_posts/attached-img/2019-09-29-jekyll-theme-add-category_3.png]

![_posts/attached-img/2019-09-29-jekyll-theme-add-category_4.png]
