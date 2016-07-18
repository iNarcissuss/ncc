---
layout: default
title: NCC Group Tools
id: tools
permalink: /tools/
---

<h1>Tools</h1>

For a complete selection of tools, <a href="https://github.com/NCCGroup/">visit our Github!</a>.  Here is a selection of our tools by year published:

<ul>
{% assign year = "" %}
{% for tool in site.data.tools %}
  {% if tool.expires %}
    {% capture nowtime %}{{ "now" | date: '%s' }}{% endcapture %}
    {% assign nowtime = nowtime | plus: 0 %}{% comment %} Cast back to int {% endcomment %}
    {% capture toolexpires %}{{ tool.expires | date: '%s' }}{% endcapture %}
    {% assign toolexpires = toolexpires | plus: 0 %}
    {% if nowtime >= toolexpires %}
      {% continue %}
    {% endif %}
  {% endif %}

  {% capture thistoolyear %}{{ tool.published | date: '%Y' }}{% endcapture %}
  {% if thistoolyear != year %}
	</ul>
	<h2>{{ tool.published | date: '%Y' }}</h2>
	{% capture year %}{{ tool.published | date: '%Y' }}{% endcapture %}
	<ul>
	{% endif %}

  <li><a href="{{ tool.link }}">{{ tool.title }}</a> {{ tool.description }}
  {% if tool.media_names %}
  <ul>
	  {% for i in (0..tool.media_names.size) %}
      {% unless forloop.last %}
      <li><a href="{{ tool.media_links[i] }}">{{ tool.media_names[i] }}</a></li>
      {% endunless %}
    {% endfor %}
  </ul>
  {% endif %}
  </li>
{% endfor %}
</ul>
