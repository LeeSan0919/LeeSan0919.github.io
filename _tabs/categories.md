---
layout: page
title: 카테고리
permalink: /categories/
icon: fas fa-stream
order: 1
---

{% assign names = "개발|CTF/Wargame|BugbBounty|블로그/기술문서|논문/컨퍼런스|공모전/자격증" | split: "|" %}
{% assign ids = "development|ctf-wargame|bug-bounty|technical-writing|research|competitions-certifications" | split: "|" %}

<nav aria-label="카테고리 목록">
  <ul>
    {% for name in names %}
    <li>
      <a href="#{{ ids[forloop.index0] }}">{{ name }}</a>
    </li>
    {% endfor %}
  </ul>
</nav>

{% for name in names %}
<section>
  <h2 id="{{ ids[forloop.index0] }}">{{ name }}</h2>

  {% assign posts = site.categories[name] %}
  {% if posts.size > 0 %}
  <ul>
    {% for post in posts %}
    <li>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      · <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
    </li>
    {% endfor %}
  </ul>
  {% else %}
  <p class="text-muted">아직 작성된 글이 없습니다.</p>
  {% endif %}
</section>
{% endfor %}
