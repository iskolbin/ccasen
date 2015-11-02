---
layout: page
title: Сотрудники
permalink: /employees/
---
{% for empl in site.data.employees %}
 {% assign name = empl[0] %}
 {% assign emp = empl[1] %}
 <a name="{{ name }}"></a>
 <h2>
 {% if emp.fullname %}
  {{emp.fullname}}
 {% else %}
  {% if emp.firstname %} {{emp.firstname}} {% endif %}
  {% if emp.patronymic %} {{emp.patronymic}} {% endif %}
  {% if emp.surname %} {{emp.surname}} {% endif %}
 {% endif %}
 </h2>
 {% if emp.image %} <p align="center"><img src="{{site.baseurl}}/img/employees/{{emp.image}}"></img></p> {% endif %} 
 {% if site.data.bio[name].plain %} <p>{{site.data.bio[name].plain }}</p> {% endif %} 
 {% if emp.email %}<p>e-mail <a href="mailto:{{emp.email}}">{{emp.email}}</a></p>{% endif %}
 {% if emp.homephone %} <p>тел. {{emp.homephone}} (дом.) </p> {% endif %}
 {% if emp.cellphone %} <p>тел. {{emp.cellphone}} (моб.) </p> {% endif %}
 {% if emp.workphone %} <p>тел. {{emp.workphone}} (раб.) </p> {% endif %}
 {% if emp.fax %} <p>факс {{emp.fax}}</p> {% endif %}
 {% if site.data.bio[name].detailed %} 
 <h3>Биография</h3> 
  <p>{{site.data.bio[name].detailed}}</p>
 {% endif %} 
 <h3>Публикации</h3>
 <ol>
  {% for pubid in emp.publications %}
   {% assign pub = site.data.publications[pubid] %}
   <li>
	 {% for auth in pub.authors %}
    {% if site.data.employees[auth] %}
     {% assign author = site.data.employees[auth] %}
     <a href="#{{ name }}"> 
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
   {% endfor %}
    «{{pub.name}}». — {{pub.origin}}: {{pub.journal}}, {{pub.year}}. — c.{{pub.pages | join: '-'}}
   </li>
  {% endfor %}</ol>
{% endfor %}
