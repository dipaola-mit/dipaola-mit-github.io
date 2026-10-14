---
layout: page
permalink: /publications/
title: publications
nav: true
nav_order: 2
# topic filter buttons; names must match the abbr={...} values in papers.bib
# (button colors come from _data/venues.yml)
topics:
  - AI Literacy
  - Social Robotics
  - Ethics and Policy
  - HCI
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

<!-- {% include bib_search.liquid %} -->

<div class="topic-filter mb-4" role="group" aria-label="Filter publications by topic">
  <button type="button" class="topic-btn active" data-topic="all" aria-pressed="true">All</button>
  {% for topic in page.topics %}
    <button type="button" class="topic-btn" data-topic="{{ topic }}" aria-pressed="false" style="background-color: {{ site.data.venues[topic].color }};">{{ topic }}</button>
  {% endfor %}
</div>

<div class="publications">

{% bibliography %}

</div>

<style>
  .topic-filter { display: flex; flex-wrap: wrap; gap: 8px; }
  .topic-btn {
    border: 2px solid transparent;
    border-radius: 999px;
    padding: 4px 14px;
    font-size: 14px;
    color: #000;
    background-color: transparent;
    cursor: pointer;
  }
  .topic-btn[data-topic="all"] { color: var(--global-text-color); border-color: var(--global-divider-color); }
  .topic-btn.active { border-color: var(--global-text-color); }
</style>

<script>
  document.addEventListener("DOMContentLoaded", () => {
    const buttons = document.querySelectorAll(".topic-btn");
    const topicOf = (li) => li.querySelector(".abbr abbr")?.textContent.trim() || "";

    buttons.forEach((btn) =>
      btn.addEventListener("click", () => {
        const topic = btn.dataset.topic;
        buttons.forEach((b) => {
          const on = b === btn;
          b.classList.toggle("active", on);
          b.setAttribute("aria-pressed", on);
        });

        document.querySelectorAll(".publications ol.bibliography").forEach((list) => {
          let shown = 0;
          list.querySelectorAll(":scope > li").forEach((li) => {
            const match = topic === "all" || topicOf(li) === topic;
            li.style.display = match ? "" : "none";
            if (match) shown++;
          });
          // hide the year heading when none of that year's papers match
          list.style.display = shown ? "" : "none";
          const heading = list.previousElementSibling;
          if (heading && heading.matches("h2.bibliography")) heading.style.display = shown ? "" : "none";
        });
      })
    );
  });
</script>
