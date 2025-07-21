---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

<!--

{% include base_path %}

Education
======
* Ph.D in Version Control Theory, GitHub University, 2018 (expected)
* M.S. in Jekyll, GitHub University, 2014
* B.S. in GitHub, GitHub University, 2012

Work experience
======
* Spring 2024: Academic Pages Collaborator
  * GitHub University
  * Duties includes: Updates and improvements to template
  * Supervisor: The Users

* Fall 2015: Research Assistant
  * GitHub University
  * Duties included: Merging pull requests
  * Supervisor: Professor Hub

* Summer 2015: Research Assistant
  * GitHub University
  * Duties included: Tagging issues
  * Supervisor: Professor Git
  
Skills
======
* Skill 1
* Skill 2
  * Sub-skill 2.1
  * Sub-skill 2.2
  * Sub-skill 2.3
* Skill 3

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams

-->

<div id="pdf-viewer" style="width:100%; min-height:800px; background:#f5f5f5;"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.10.377/pdf.min.js"></script>
<script>
  pdfjsLib.GlobalWorkerOptions.workerSrc = 
    'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.10.377/pdf.worker.min.js';

  pdfjsLib.getDocument('/files/resume.pdf').promise
    .then(pdf => pdf.getPage(1))
    .then(page => {
      const container = document.getElementById('pdf-viewer');
      const viewport = page.getViewport(1.0);
      
      const canvas = document.createElement('canvas');
      const context = canvas.getContext('2d');
      canvas.width = container.offsetWidth;
      canvas.height = (container.offsetWidth / viewport.width) * viewport.height;
      
      container.appendChild(canvas);
      
      page.render({
        canvasContext: context,
        viewport: page.getViewport(canvas.width / viewport.width)
      });
    })
    .catch(err => {
      console.error(err);
      document.getElementById('pdf-viewer').innerHTML = `
        <p>Error loading PDF. <a href="/files/resume.pdf">Download instead</a></p>
      `;
    });
</script>
