---
layout: page
title: Papers
use-site-title: false
---

{% assign items = site.data.mypapers | sort: 'year' | reverse %}


<div class="paper-list">
  {% for pt in site.data.papertypes %}
  <h2> {{ pt.title }}</h2>
  {% for paper in items %}
  {% if pt.type == paper.type %}
  <article class="paper-preview">
	<strong>{{ paper.title }}</strong><br>
	{% for a in paper.author %}
	{{ a.given }} {{ a.dropping-particle }} {{ a.family }}, 
	{% endfor %}<br>
	{% if paper.container-title %} {{ paper.container-title }}. {% endif %}
	{% if paper.editor %}
	Editors
	{% for e in paper.editor %}
	{{ e['given'] }} {{ e['dropping-particle'] }} {{ e['family'] }}{% if forloop.last %}.{% else %}, {% endif %} 
	{% endfor %}<br>
	{% endif %}
	{% if paper.collection-title %} {{ paper.collection-title }}, {% endif %}
	Volume {{ paper.volume }}{% if paper.issue %} ({{ paper.issue }}){% endif %},
	{% if paper.page %} {{ paper.page }}, {% endif %}
	{{ paper.year }}.
	{% if paper.URL %} <a href="{{ paper.URL }}" target="new"><i class="fa fa-link"></i></a> {% endif %}
   </article>
  {% endif %} 
  {% endfor %}
  {% endfor %}  
</div>