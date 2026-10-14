---
layout: page
permalink: /media/
title: media
description: Talks, podcasts, and press coverage of my work.
nav: true
nav_order: 4
---

{% assign talks = site.data.media.talks %}
{% assign podcasts = site.data.media.podcasts %}
{% assign press = site.data.media.press %}

{% if talks.size > 0 %}

## talks

<div class="row">
{% for item in talks %}
  <div class="col-md-6 mb-4">
    <div class="embed-responsive embed-responsive-16by9 rounded z-depth-1 mb-2">
      <iframe class="embed-responsive-item" src="https://www.youtube-nocookie.com/embed/{{ item.youtube_id }}" title="{{ item.title | escape }}" loading="lazy" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
    <h6 class="mb-1"><a href="https://www.youtube.com/watch?v={{ item.youtube_id }}">{{ item.title }}</a></h6>
    <p class="small mb-1" style="color: var(--global-text-color-light);">{{ item.venue }}{% if item.date %} &middot; {{ item.date | date: "%B %Y" }}{% endif %}</p>
    <p class="small">{{ item.description }}</p>
  </div>
{% endfor %}
</div>
{% endif %}

{% if podcasts.size > 0 %}

## podcasts

{% include media_list.liquid items=podcasts icon_size=64 %}
{% endif %}

{% if press.size > 0 %}

## press

{% for group in press %}

<h5 class="mt-4 mb-2">{{ group.group }}</h5>

{% if group.intro %}<p>{{ group.intro | markdownify | remove: '<p>' | remove: '</p>' }}</p>{% endif %}

{% include media_list.liquid items=group.items %}
{% endfor %}
{% endif %}
