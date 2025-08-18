---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
{% include base_path %}

{% assign items = site.publications | sort: "date" | reverse %}

{% if items.size == 0 %}
<p><em>No publications found. Make sure files live in <code>_publications/</code> and have valid front matter (title, date).</em></p>
{% endif %}

<ul class="archive__list">
{% for post in items %}
  <li class="archive__item">
    <h2 class="archive__item-title">
      {% if post.link %}
        <a href="{{ post.link }}" target="_blank" rel="noopener">{{ post.title }}</a>
      {% else %}
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% endif %}
    </h2>

    {% if post.venue or post.date %}
      <p class="page__meta">
        {% if post.venue %}<em>{{ post.venue }}</em>{% if post.date %}, {% endif %}{% endif %}{{ post.date | date: "%Y" }}
      </p>
    {% endif %}

    {% if post.excerpt %}
      <div class="archive__item-excerpt">
        {{ post.excerpt | markdownify }}
      </div>
    {% endif %}
  </li>
{% endfor %}
</ul>
