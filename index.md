---
layout: page
title: 清风
tagline: Supporting tagline
---
{% include JB/setup %}


<ul class="posts" >
	{% for post in site.posts %}
	<li class="repo-list-item">
		<h3 class="repo-list-name">
		  <a href="{{ post.url }}">{{ post.title }}</a>
		</h3>
		<p class="repo-list-description">
			{{ post.excerpt | strip_html | strip }}
		</p>
		<p class="repo-list-meta">
			<span class="meta-info">
			  <span class="octicon octicon-calendar"></span> {{ post.date | date: "%Y/%m/%d" }}
			</span>
			{% for cat in post.categories %}
			<span class="meta-info">
			  <span class="octicon octicon-file-directory"></span>
			  <a href="/categories/#{{ cat }}" title="{{ cat }}">{{ cat }}</a>
			</span>
			{% endfor %}
		</p>
	</li>
	{% endfor %}
</ul>

