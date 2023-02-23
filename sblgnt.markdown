---
layout: page
title: Context Tree for the SBLGNT Edition
permalink: /sblgnt/
---

Click on a link below to view the rendered context tree for that book.

<ul>
{% for book in site.data.sblgnt %}
    <li>
        <a target="_blank" href="{{ book.url }}">{{ book.name }}</a>
    </li>
{% endfor %}
</ul>

## Note

Files are served using the https://cdn.statically.io/gh/ protocol in order to enable proper stylesheet rendering. This is a free service, and may be subject to downtime or other issues. If you experience any issues, please let us know. If you are interested in sponsoring this project, please contact us.
