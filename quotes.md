---
layout: page
permalink: /quotes/
title: quotes
description: The inspirational quotes ever uttered across the world
---

<ul class="post-list">
{% for quote in site.quotes reversed %}
    <li>
        <span class="quote-title">{{ quote.title }}</span> 
        <p class="post-meta">— {{ quote.author }}</p>
      </li>
{% endfor %}
</ul>