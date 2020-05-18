---
layout: page
title: Projects
permalink: /projects/
---
<br>
<div align="center"> A list of projects I have done in the past with brief explanations. </div>

<div>
{% for projects in site.projects reversed %}
  <br>
  {% if projects.date > site.time %}
    {% if forloop.first %}
      <h2 class="projects-section" id="upcoming">Upcoming</h2>
    {% endif %}
  {% else %}
    {% assign currentyear = projects.date | date: "%Y" %}
    {% if currentyear != previousyear %}
      <h2 class="projects-section" id="y{{ projects.date | date: "%Y"}}">{{ currentyear }}</h2>
      {% assign previousyear = currentyear %}
    {% endif %}
  {% endif %}


    <div class="projects">
      <span class="post-title"><strong><big> {{ projects.title }} </big></strong></span>
      <br>
      {% if projects.description %}
      <span class="post-date projects-description">{{ projects.description }} </span>
      {% endif %}
      <br>

      <i class="fa fa-comments-o" aria-hidden="true"></i>
      {% if projects.event-url %}
      <a href="{{ projects.event-url }}"
       title="{% if projects.event-fulltitle %}{{ projects.event-fulltitle }}{% else %}{{ projects.event }}{% endif %}
{{ projects.event-url }}">
      {% endif %}

      {{ projects.event }}{% if projects.event-fulltitle %}: {{ projects.event-fulltitle }}{% endif %}
      {% if projects.event-url %}</a>{% endif %}
      <br>

      <span class="location">
        <i class="fa fa-map-marker" aria-hidden="true"></i>
        {{ projects.location }}
      </span>
      <br>

      <i class="fa fa-calendar" aria-hidden="true"></i> {{ projects.date | date: "%B %-d, %Y" }}
      <br>

      {% if projects.report %}
        <span class="projects-resource">
          <i class="fa fa-file-pdf-o" aria-hidden="true"></i>
          {% if projects.report contains ".pdf" %}
            <a href="{{ site.pdfs }}/{{ projects.report }}">
          {% else %}
            <a href="{{ projects.report }}">
          {% endif %}
          Report</a>
        </span>
      {% endif %}
      
      {% if projects.video %}
        &nbsp; &nbsp;
        <span class="projects-resource"><i class="fa fa-file-video-o" aria-hidden="true"></i> <a href="{{ projects.video }}">Video</a></span>
      {% endif %}
      
      {% if projects.post %}
        &nbsp; &nbsp;
        <span class="projects-resource">
          <i class="fa fa-file-text-o" aria-hidden="true"></i>
          <a href="{{ site.url }}{{ projects.post }}">Post</a>
        </span>
      {% endif %}
  
      {% if projects.featured %}
        &nbsp; &nbsp;
        <span class="projects-resource"><i class="fa fa-file-text-o" aria-hidden="true"></i> <a href="{{ projects.featured }}">Featured</a></span>
      {% endif %}
    </div>
{% endfor %}
</div>

