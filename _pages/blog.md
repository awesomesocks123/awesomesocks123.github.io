---
layout: default
permalink: /blog/
title: blog
nav: true
nav_order: 5
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3 # The number of links after the current page
---

<div class="post">

{% assign blog_name_size = site.blog_name | size %}
{% assign blog_description_size = site.blog_description | size %}

{% if blog_name_size > 0 or blog_description_size > 0 %}

  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>
  {% endif %}

{% if site.display_tags and site.display_tags.size > 0 or site.display_categories and site.display_categories.size > 0 %}

  <div class="tag-category-list">
    <ul class="p-0 m-0">
      {% for tag in site.display_tags %}
        <li>
          <i class="fa-solid fa-hashtag fa-sm"></i> <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">{{ tag }}</a>
        </li>
        {% unless forloop.last %}
          <p>&bull;</p>
        {% endunless %}
      {% endfor %}
      {% if site.display_categories.size > 0 and site.display_tags.size > 0 %}
        <p>&bull;</p>
      {% endif %}
      {% for category in site.display_categories %}
        <li>
          <i class="fa-solid fa-tag fa-sm"></i> <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">{{ category }}</a>
        </li>
        {% unless forloop.last %}
          <p>&bull;</p>
        {% endunless %}
      {% endfor %}
    </ul>
  </div>
  {% endif %}

{% assign featured_posts = site.posts | where: "featured", "true" %}
{% if featured_posts.size > 0 %}
<br>

<!-- <div class="container featured-posts">
  <h3>Featured Book Report</h3>
  <div class="row">
  {% for post in featured_posts %}
    <div class="col-md-12 mb-4">
      <a href="{{ post.url | relative_url }}">
        <div class="card hoverable">
          <div class="card-body">
            <h3 class="card-title">{{ post.title }}</h3>
            <p class="card-text">{{ post.description }}</p>
            {% if post.external_source == blank %}
              {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
            {% else %}
              {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
            {% endif %}
            {% assign year = post.date | date: "%Y" %}
            <p class="post-meta">
              {{ read_time }} min read &nbsp; &middot; &nbsp;
              <a href="{{ year | prepend: '/blog/' | relative_url }}">
                <i class="fa-solid fa-calendar fa-sm"></i> {{ year }} </a>
            </p>
          </div>
        </div>
      </a>
    </div>
  {% endfor %}
  </div>
</div> -->
{% endif %}

  <div class="book-reports">
    <h3>All Blog Posts</h3>
    
    {% if page.pagination.enabled %}
      {% assign postlist = paginator.posts %}
    {% else %}
      {% assign postlist = site.posts %}
    {% endif %}
    
    <div class="row">
    {% for post in postlist %}
      {% if post.external_source == blank %}
        {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
      {% else %}
        {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
      {% endif %}
      {% assign year = post.date | date: "%Y" %}
      {% assign tags = post.tags | join: "" %}
      {% assign categories = post.categories | join: "" %}
      
      <div class="col-md-12 mb-4">
        <div class="card hoverable">
          <div class="card-body">
            <h4>
              <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h4>
            <p>{{ post.description }}</p>
            <p class="post-meta">
              {{ read_time }} min read &nbsp; &middot; &nbsp;
              {{ post.date | date: '%B %d, %Y' }}
            </p>
            <p class="post-tags">
              <a href="{{ year | prepend: '/blog/' | relative_url }}">
                <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}</a>
              
              {% if tags != "" %}
                &nbsp; &middot; &nbsp;
                {% for tag in post.tags %}
                  <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">
                    <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}</a>
                  {% unless forloop.last %}&nbsp;{% endunless %}
                {% endfor %}
              {% endif %}
              
              {% if categories != "" %}
                &nbsp; &middot; &nbsp;
                {% for category in post.categories %}
                  <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">
                    <i class="fa-solid fa-tag fa-sm"></i> {{ category }}</a>
                  {% unless forloop.last %}&nbsp;{% endunless %}
                {% endfor %}
              {% endif %}
            </p>
          </div>
        </div>
      </div>
    {% endfor %}
    </div>
  </div>

{% if page.pagination.enabled %}
{% include pagination.liquid %}
{% endif %}

</div>
