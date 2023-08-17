---
layout: default
permalink: /teaching/
title: Teaching
---

<p> This semester I am TAing <a href="https://math.osu.edu/courses/math-1172">MA 1172</a>. Here are a collection of notes on what we talked about during recitation. </p>

<div class="posts">
  {% for tag in site.tags %}
  {% if tag[0] == "MA1172" %}
  {% for post in tag[1] %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
    {% endfor %}
  {% endfor %}
</div>
