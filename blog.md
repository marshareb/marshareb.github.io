---
layout: default
permalink: /blog/
title: Blog
---

<p>Here is my blog. This is a collection of various things I'm thinking about at the time. There are definitely mistakes, so take most of it with a grain of salt. </p>

<div class="posts">
  {% for post in list(set(site.posts) - set(site.tags.MA1172)) %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>
