---
layout: page
title: Employees
permalink: /employees/
---
{% for empl in site.data.employees %}
 {% assign name = empl[0] %}
 {% assign emp = empl[1] %}
 {% unless emp.former %}
 <a name="{{ name }}"></a>
 <h3>
 {% if emp.fullname %}
  {{emp.fullname}}
 {% else %}
  {% if emp.firstname %} {{emp.translate['en'].firstname}} {% endif %}
  {% if emp.patronymic %} {{emp.translate['en'].patronymic}} {% endif %}
  {% if emp.surname %} {{emp.translate['en'].surname}} {% endif %}
 	{% if emp.degree %} <i>, {{emp.translate['en'].degree}}</i> {% endif %}
 	{% if emp.position %} <i>, {{emp.translate['en'].position}}</i> {% endif %}
 {% endif %}
 </h3>

	{% if emp.image %} <p align="center"><img src="{{site.baseurl}}/img/employees/{{emp.image}}"></img></p> {% endif %} 
 {% if site.data.bio[name].plain %} <p>{{site.data.bio[name].plain }}</p> {% endif %} 
 {% if emp.email %}<p>e-mail <a href="mailto:{{emp.email}}">{{emp.email}}</a></p>{% endif %}
 {% if emp.homephone %} <p>тел. {{emp.homephone}} (home) </p> {% endif %}
 {% if emp.cellphone %} <p>тел. {{emp.cellphone}} (cell) </p> {% endif %}
 {% if emp.workphone %} <p>тел. {{emp.workphone}} (work) </p> {% endif %}
 {% if emp.fax %} <p>факс {{emp.fax}}</p> {% endif %}
 {% if site.data.bio[name].detailed %} 
 <h3>Bio</h3> 
  <p>{{site.data.bio[name].detailed}}</p>
 {% endif %} 
 ---
 {% endunless %}
{% endfor %}
