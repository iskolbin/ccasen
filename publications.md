---
layout: page
title: Публикации
permalink: /publications/
---
<ol>
{% assign sortedpubs = site.data.pubs | sort: pubyear[0] %}
{% for pubyear in sortedpubs %}
<h3>{{pubyear[0] | remove: 'publications_'}}</h3>
{% assign publications = pubyear[1] %}
{% for pubs in publications %}
{% assign pub = pubs[1] %}
<li>
 {% for auth in pub.authors %}
  {% if site.data.employees[auth] %}
	 {% if pub.lang %}
   {% assign p = "p." %}
   {% assign author = site.data.employees[auth].translate[pub.lang] %}
   {% else %}
   {% assign p = "c." %}
   {% assign author = site.data.employees[auth] %}
   {% endif %}
   <a href="{{site.baseurl}}/employees/#{{ name }}"> 
 	  {% if author.shortname %}
     {{author.shortname}}
    {% else %}
     {% if author.surname %} {{author.surname}} {% endif %}
     {% if author.firstname %}{{author.firstname | truncate:1,''}}.{% endif %}{% if author.patronymic %}{{author.patronymic | truncate:1,''}}.{% endif %}
    {% endif %}
   </a>
  {% else %}
   {{auth}}
  {% endif %}
   {% unless forloop.last %},{% endunless %}
  {% endfor %} «{{pub.name}}». — {% if pub.origin %}{{pub.origin}}:{% endif %} {% if pub.journal %}{{pub.journal}},{% endif %}{%if pub.conference %}{{pub.conference}},{% endif %} {{pub.year}}.{% if pub.pages %} — {{p}}{{pub.pages | join: '-'}}{% endif %}{% if pub.mpages %} — {{p}}{{pub.mpages | join: ','}}{% endif %}
	</li>
{% endfor %}
<hr>
{% endfor %}
</ol>
