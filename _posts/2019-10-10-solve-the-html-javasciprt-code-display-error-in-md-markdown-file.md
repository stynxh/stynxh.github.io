---
layout: post
published: true
title: Solve the html javasciprt code display error in md (markdown) file
tags:
  - MD
  - Markdown
  - code block
  - troubleshooting
date: '2019-10-10'
---
## Situation

Use code block (`` `code` ``) to display code when creating MD file. However, in the case of html and javascript code, the execution result of the code is output instead of the code.

```javascript
---
layout: default
---
<ul class="posts-list">  
  {% assign category = page.category | default: page.title %}
  <h4>Posts in {{ category }} </h4>
```  

## Solution

Wrap it in { % raw % } code { % endraw % } codeblock.

> **Note:** `{` And `%` should be used without spaces.

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
