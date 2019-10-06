---
layout: post
published: true
title: ' Integrating disqus into your Github jekyll blog'
date: '2019-10-06'
category:
  - research
tags:
  - jekyll
  - disqus
---
## Step 1

Sign up the disqus [https://disqus.com/](https://disqus.com/).

![2019-10-05-github-jekyll-disqus-01.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-01.png)


## Step 2

Select the **I want to install Disqus on my site**.

![2019-10-05-github-jekyll-disqus-02.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-02.png)


## Step 3

Enter the website name.

![2019-10-05-github-jekyll-disqus-03.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-03.png)


## Step 4

Select the **Basic** plan.

![2019-10-05-github-jekyll-disqus-04.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-04.png)


## Step 5

Select the **Jekyll** platform.

![2019-10-05-github-jekyll-disqus-05.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-05.png)


## Step 6

Click the link **Universal Embeded Code**.

![2019-10-05-github-jekyll-disqus-06.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-06.png)


## Step 7

Create a `/ _includes / disqus_comments.html` file on your Github blog and paste the content from item 1.

![2019-10-05-github-jekyll-disqus-07.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-07.png)


## Step 8

Modify the contents of the `/ _includes / disqus_comments.html` file created in Step 7.

{% raw %}
```javascript
...
...
<script>
	var disqus_config = function () {
		this.page.url = '{{ page.url | absolute_url }}';
      	this.page.identifier = '{{ page.url | absolute_url }}';
    };    
...
...
...
```
{% endraw %}

{: .box-note}
**Note:** In the original content, **var disqus_config = function ()** is commented out, but uncomment and change the function contents.


## Step 9

Check your `/ _config.yml` file on your Github blog to see if the **url** value is set.
If not set, set your blog address.

```markdown
# --- Local development options ---
# If your website is hosted locally rather than on GitHub, then you need to uncomment the next two parameters to set the url and baseurl
# *** If you're not sure what this mean, then leave this section as it is. Only modify the url and baseurl if you know what you're doing!***

# url is the the website domain URL without a trailing slash
url: "https://stynxh.github.io"
---
```


## Step 10

Modify the contents of the `/_layouts/post.html` file.

{% raw %}
```javascript
---
layout: base
comments: true
---
...
...
...
    {% if page.comments != false %}
	    {% include disqus_comments.html %}
    {% endif %}  
```
{% endraw %}

{: .box-note}
**Note 1:** Add **comments: true** at the top  
**Note 2:** Add code at the bottom


### Step 11

Click the **Configure** button at the disqus website.

![2019-10-05-github-jekyll-disqus-08.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-08.png)


### Step 12

Enter website name and URL and click **Complete Setup**.

![2019-10-05-github-jekyll-disqus-09.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-09.png)

![2019-10-05-github-jekyll-disqus-10.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-10.png)


### Step 13

verify disqus mail sent to the email address entered when you signed up for disqus.

![2019-10-05-github-jekyll-disqus-11.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-11.png)


## Result

![2019-10-05-github-jekyll-disqus-12.png]({{site.baseurl}}/img/attached-post/2019-10-05-github-jekyll-disqus-12.png)
