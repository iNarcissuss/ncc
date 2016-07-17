---
layout: default
title: iSEC Research Publications
id: research
permalink: /research/
---

<h1>Security Presentations</h1>
<ul>

{% assign year = "" %}
{% for talk in site.data.talks %}
	{% capture thistalkyear %}{{ talk.expires | date: '%Y' }}{% endcapture %}
	{% if thistalkyear != year %}
	</ul>
	<h2>{{ talk.expires | date: '%Y' }}</h2>
	{% capture year %}{{ talk.expires | date: '%Y' }}{% endcapture %}
	<ul>
	{% endif %}
  <li>{% if talk.link %}<a href="{{ talk.link }}">{% endif %}{{ talk.title }}{% if talk.link %}</a>{% endif %}{{ talk.subtitle }}
  {% if talk.location or talk.dates or talk.media_names %}<ul>{% endif %}
  {% if talk.dates %}<li>{{ talk.dates }}</li>{% endif %}
  {% if talk.location %}<li>{{ talk.location }}</li>{% endif %}
  {% if talk.media_names %}
	  {% for i in (0..talk.media_names.size) %}
      {% unless forloop.last %}
      <li><a href="{{ talk.media_links[i] }}">{{ talk.media_names[i] }}</a></li>
      {% endunless %}
      {% endfor %}
  {% endif %}
  {% if talk.location or talk.dates or talk.media_names %}</ul>{% endif %}
  </li>
{% endfor %}
</ul>
