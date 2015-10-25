---
layout: page
title: Публикации
permalink: /publications/
---
<ol>
{% for pubs in site.data.publications %}
{% assign pub = pubs[1] %}
<li>
 {% for auth in pub.authors %}
  {% if site.data.employees[auth] %}
   {% assign author = site.data.employees[auth] %}
   <a href="{{site.baseurl}}/employees/#{{ name }}"> 
 	  {% if author.shortname %}
     {{author.shortname}}
    {% else %}
     {% if author.surname %} {{author.surname}} {% endif %}
     {% if author.firstname %}{{author.firstname | truncate:1,''}}.{% endif %}{% if author.patronymic %}{{auth.patronymic | truncate:1,''}}.{% endif %}
    {% endif %}
   </a>
  {% else %}
   {{auth}}
  {% endif %}
   {% unless forloop.last %},{% endunless %}
  {% endfor %} {{pub.authors | join:','}} «{{pub.name}}». — {{pub.origin}}: {{pub.journal}}, {{pub.year}}. — c.{{pub.pages | join: '-'}}
	</li>
{% endfor %}
</ol>
