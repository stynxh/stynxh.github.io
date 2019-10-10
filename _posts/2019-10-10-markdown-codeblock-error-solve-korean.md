---
layout: post
published: true
title: MD (markdown) 파일 작성시 코드가 제대로 표시되지 않을때 해결법
date: '2019-10-10'
category:
  - troubleshooting
tags:
  - MD
  - Markdown
  - code block
---
## 현상

MD파일 작성 시 코드를 표시하고 싶을때 코드 블록 (``` code ```)을 사용하는데 html, javascript 코드의 경우 코드가 아닌 코드의 실행결과가 출력되는 경우가 있다.

```javascript
---
layout: default
---
<ul class="posts-list">  
  {% assign category = page.category | default: page.title %}
  <h4>Posts in {{ category }} </h4>
```  

## 해결

{ % raw % } codeblock { % endraw % } 로 감싸주면 된다.

{: .box-note}
**Note:** `{` 와 `%` 는 공백없이 붙여서 사용해야 한다.

{% raw %}
```javascript
---
layout: default
---
<ul class="posts-list">  
  {% assign category = page.category | default: page.title %}
  <h4>Posts in {{ category }} </h4>
```
{% endraw %}

