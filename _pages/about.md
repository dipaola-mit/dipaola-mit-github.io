---
layout: about
title: about
permalink: /
subtitle: AI + ethics + education expert, researcher, educator

profile:
  align: right
  image: prof_pic.jpg
  image_circular: true # crops the image to make it circular
  more_info: 

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

<p class="bio-toggle">
  <a href="#short-bio" data-bio="bio-short" aria-current="true">short bio</a> |
  <a href="#long-bio" data-bio="bio-long">long bio</a>
</p>

<div id="bio-short" markdown="1">
I study how young people interact with AI, and how curricula and educational policy can support its responsible use. I recently completed my PhD at the [MIT Media Lab](https://www.media.mit.edu/events/daniella-dipaola/), where my research showed that AI literacy is necessary for civic participation. My hands-on AI learning experiences have reached thousands of K–12 learners worldwide through initiatives like [Day of AI](https://dayofai.org) and [Everyday AI](https://everyday-ai.org/), and I most recently designed [Student Voices in AI](https://dayofai.org/units/student-voices-in-ai), a youth council model that gives students a formal role in shaping AI use in their schools. 
  
I am currently a Postdoctoral Associate at the [MIT Media Lab](https://www.media.mit.edu/people/dipaola/overview/) and a joint Research Fellow at Harvard's [Allen Lab for Democracy Renovation](https://ash.harvard.edu/programs/allen-lab-for-democracy-renovation/) and [Democratic Knowledge Project](https://www.democraticknowledgeproject.org/). 
</div>

<div id="bio-long" markdown="1" hidden>
My research explores how young people interact with AI, how we can design curricula to support responsible AI use and creation, and how educational policy can guide the integration of AI into schools. While much AI-literacy work emphasizes workforce preparation, my work shows that AI literacy is also necessary for civic participation. I recently completed my PhD, ["AI Literacy as Civic Literacy: Developing Youth as Responsible Citizens in a World with AI"](https://www.media.mit.edu/events/daniella-dipaola/) at the MIT Media Lab, where I was advised by Professor Cynthia Breazeal.

I have created hands-on learning experiences that introduce K–12 students to the responsible use of AI. These programs have reached thousands of learners worldwide through initiatives like [Day of AI](https://dayofai.org), [Project STEM](https://projectstem.org/middle-school-cs2-demo/cse2-scope-and-sequence), [Edward M. Kennedy Institute](https://emkinstitute.org/offerings-6-8/), and [Everyday AI](https://everyday-ai.org/). Most recently, I designed [Student Voices in AI](https://dayofai.org/units/student-voices-in-ai), a youth council model that gives students a formal role in shaping AI use in their schools.


I am currently a Postdoctoral Associate at the [MIT Media Lab](https://www.media.mit.edu/people/dipaola/overview/), and a joint Research Fellow in the [Allen Lab for Democracy Renovation](https://ash.harvard.edu/programs/allen-lab-for-democracy-renovation/) at the Harvard Ash Center for Democratic Governance and Innovation and the [Democratic Knowledge Project](https://www.democraticknowledgeproject.org/) at the Harvard Graduate School of Education. I have a Bachelor's in Human Factors Engineering from Tufts University and a Master's in Media Arts and Sciences from MIT. Prior to my graduate work, I worked as a design researcher at Jibo, Inc., which was recognized as Time Magazine's Invention of the Year in 2017.
</div>

<script>
  (function () {
    var links = document.querySelectorAll(".bio-toggle a");
    function show(id) {
      links.forEach(function (link) {
        var active = link.dataset.bio === id;
        document.getElementById(link.dataset.bio).hidden = !active;
        if (active) link.setAttribute("aria-current", "true");
        else link.removeAttribute("aria-current");
      });
    }
    links.forEach(function (link) {
      link.addEventListener("click", function (event) {
        event.preventDefault();
        show(link.dataset.bio);
        history.replaceState(null, "", link.getAttribute("href"));
      });
    });
    if (location.hash === "#long-bio") show("bio-long");
  })();
</script>
