---
layout: page
title: Lessons
permalink: /lessons/
---
<br>
<div align="center"> Some lessons, realizations, and thoughts </div>

<div>
{% for lessons in site.lessons reversed %}
  <br>
  {% if lessons.date > site.time %}
    {% if forloop.first %}
      {% assign lesson_num = 1 %}
      <h2 class="lessons-section" id="upcoming">Upcoming</h2>
    {% endif %}
  {% else %}
    {% assign currentyear = lessons.date | date: "%Y" %}
    {% if currentyear != previousyear %}
      <h2 class="lessons-section" id="y{{ lessons.date | date: "%Y"}}">{{ currentyear }}</h2>
      {% assign previousyear = currentyear %}
      {% assign lesson_num = lesson_num + 1 %}
    {% endif %}
  {% endif %}


    <div class="lessons">
      
      <span class="post-title"><strong><big> {{ lessons.title }} </big></strong></span>
      <br>
      {% if lessons.description %}
      <strong> Description: </strong>
      <span class="post-date lessons-description">{{ lessons.description }} </span>
      {% endif %}
      <br>

    </div>
{% endfor %}
</div>

