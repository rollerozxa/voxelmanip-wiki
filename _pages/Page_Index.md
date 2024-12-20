---
title: Page Index
---

This page contains a list of all pages.

<ul>
	{%- for page in site.pages -%}
		<li><a href="{{ page.url }}">{{ page.title }}</a></li>
	{%- endfor -%}
</ul>
