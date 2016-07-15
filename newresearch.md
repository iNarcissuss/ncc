---
layout: default
title: iSEC Research Publications
id: newresearch
permalink: /newresearch/
---

<h1>Upcoming Talks</h1>
<ul>

{% assign year = "" %}
{% for talk in site.data.upcoming_talks %}
	{% capture thistalkyear %}{{ talk.expires | date: '%Y' }}{% endcapture %}
	{% if thistalkyear != year %}
	</ul>
	<h2>{{ talk.expires | date: '%Y' }}</h2>
	{% capture year %}{{ talk.expires | date: '%Y' }}{% endcapture %}
	<ul>
	{% endif %}
  <li>{% if talk.link %}<a href="{{ talk.link }}">{% endif %}{{ talk.title }}{% if talk.link %}</a>{% endif %}{{ talk.subtitle }}
  {% if talk.location or talk.dates or talk.slides or talk.video or talk.more %}<ul>{% endif %}
  {% if talk.dates %}<li>{{ talk.dates }}</li>{% endif %}
  {% if talk.location %}<li>{{ talk.location }}</li>{% endif %}
  {% if talk.slides %}<li><a href="{{ talk.slides }}">[Slides]</a></li>{% endif %}
  {% if talk.video %}<li><a href="{{ talk.video }}">[Video]</a></li>{% endif %}
  {% if talk.more %}<li>{{ talk.more }}</li>{% endif %}
  {% if talk.location or talk.dates or talk.slides or talk.video or talk.more %}</ul>{% endif %}
  </li>
{% endfor %}
</ul>
