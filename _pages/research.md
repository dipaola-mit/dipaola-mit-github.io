---
layout: page
permalink: /research/
title: research
nav: true
nav_order: 1
---

<div class="research-areas">
  {% for area in site.data.research.areas %}
  {% assign tag = site.data.venues[area.venue] %}
  <button type="button" class="research-area" data-area="{{ area.title | slugify }}" aria-pressed="false" style="--tag-color: {{ tag.color }}; --tag-text: {{ tag.text }};">{{ area.title }}</button>
  {% endfor %}
</div>

{% for area in site.data.research.areas %}
{% if area.questions %}
<section class="research-theme" data-area="{{ area.title | slugify }}" aria-label="{{ area.title }}" hidden>
  <h2>Key research questions</h2>
  <ul class="research-questions">
    {% for question in area.questions %}
    <li style="--i: {{ forloop.index0 }}">{{ question }}</li>
    {% endfor %}
  </ul>
</section>
{% endif %}
{% endfor %}

<div class="row row-cols-1 row-cols-md-3 research-grid">
  {% for project in site.data.research.projects %}
  {% assign area = site.data.research.areas | where: "title", project.area | first %}
  {% assign tag = site.data.venues[area.venue] %}
  <div class="col mb-4" data-area="{{ project.area | slugify }}" style="--i: {{ forloop.index0 }}">
    <div class="card h-100 research-card">
      {% if project.image %}
        {% assign project_image = project.image | prepend: 'assets/img/' %}
        {% include figure.liquid path=project_image sizes="300px" alt=project.name class="card-img-top" zoomable=false %}
      {% else %}
        <div class="research-photo-placeholder" aria-hidden="true"><i class="ti ti-photo"></i></div>
      {% endif %}
      <div class="card-body">
        <span class="research-tag" style="background-color: {{ tag.color }}; color: {{ tag.text }};">{{ project.area }}</span>
        <h3 class="card-title">{{ project.name }}</h3>
        <p class="card-text">{{ project.tagline }}</p>
        {% if project.links %}
        <p class="research-links">
          {% for link in project.links %}
            <a href="{{ link.url }}">{{ link.label }}</a>{% unless forloop.last %} <span aria-hidden="true">&middot;</span> {% endunless %}
          {% endfor %}
        </p>
        {% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<script>
  (function () {
    var buttons = document.querySelectorAll(".research-area");
    var filtered = document.querySelectorAll(".research-grid > .col");
    var sections = document.querySelectorAll(".research-theme");
    var active = null;
    function show(area) {
      active = area;
      buttons.forEach(function (button) {
        button.setAttribute("aria-pressed", button.dataset.area === area ? "true" : "false");
      });
      filtered.forEach(function (card) {
        card.hidden = area !== null && card.dataset.area !== area;
      });
      sections.forEach(function (section) {
        section.hidden = section.dataset.area !== area;
      });
    }
    buttons.forEach(function (button) {
      button.addEventListener("click", function () {
        var area = button.dataset.area === active ? null : button.dataset.area;
        show(area);
        history.replaceState(null, "", area ? "#" + area : location.pathname);
      });
    });
    var linked = location.hash.slice(1);
    buttons.forEach(function (button) {
      if (button.dataset.area === linked) show(linked);
    });
  })();
</script>
