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

<script src="/assets/js/pdfjs/pdf.js"></script>
<script>
  console.log("PDF.js script loaded"); // Debugging line

  // Set worker path
  pdfjsLib = window['pdfjs-dist/build/pdf'];
  pdfjsLib.GlobalWorkerOptions.workerSrc = '/assets/js/pdfjs/pdf.worker.js';

  // Debug: Check if PDF.js is initialized
  console.log("PDF.js initialized:", pdfjsLib);

  // Load the PDF
  pdfjsLib.getDocument('/files/your_resume.pdf').promise
    .then(function(pdf) {
      console.log("PDF loaded successfully, # of pages:", pdf.numPages);
      return pdf.getPage(1);
    })
    .then(function(page) {
      console.log("Rendering page 1");
      var scale = 1.5;
      var viewport = page.getViewport({ scale: scale });

      var canvas = document.createElement('canvas');
      var context = canvas.getContext('2d');
      canvas.height = viewport.height;
      canvas.width = viewport.width;
      document.getElementById('pdf-viewer').appendChild(canvas);

      page.render({
        canvasContext: context,
        viewport: viewport
      });
    })
    .catch(function(error) {
      console.error("PDF.js error:", error);
    });
</script>
