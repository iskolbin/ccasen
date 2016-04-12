---
layout: page
title: Сотрудники
permalink: /employees/
---
{% for empl in site.data.employees %}
 {% assign name = empl[0] %}
 {% assign emp = empl[1] %}
 <a name="{{ name }}"></a>
 <h3>
 {% if emp.fullname %}
  {{emp.fullname}}
 {% else %}
  {% if emp.firstname %} {{emp.firstname}} {% endif %}
  {% if emp.patronymic %} {{emp.patronymic}} {% endif %}
  {% if emp.surname %} {{emp.surname}} {% endif %}
 {% endif %}
 </h3>
 {% if emp.degree %} <i>, {{emp.degree}}</i> {% endif %}
 {% if emp.position %} <i>, {{emp.position}}</i> {% endif %}

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
 ---
{% endfor %}
