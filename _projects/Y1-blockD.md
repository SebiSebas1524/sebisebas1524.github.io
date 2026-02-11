---
layout: project
title: Souls Maze
description: SoulMaze is a first person Co-op game, based off of Pacman. A Gatherer and a Protector awake in a futuristic landscape. Fruit litters the ground and four spirits patrol this desolate maze. The Gatherer and the Protector must work together, synergizing their unique abilities,  to ward off spirits and collect all the fruit.  
image: /assets/vid/y1d/maze.gif
hide_image: true
hide_meta: true
tags:
  - unreal
  - graphics
  - tools
  - problem solving
team_size: 4 Programmers | 3 Designers | 4 Artists
duration: 8 Weeks
contributions:
  - Heavy fog on the floor
  - Make tools for designers
  - Problem solving 
main_category: University Projects
date: 2024-07-15
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <iframe
      style="width: 100%; height: 100%; border: 0;"
      src="https://www.youtube.com/watch?v=bTHQXMu_oAQ&t=31s"
      title="Project video"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </div>
</div>

<div class="project-meta" style="margin-bottom: 1rem;">
  {% if page.main_category %}
    <span class="category">{{ page.main_category }}</span>
  {% endif %}
  {% if page.engine %}
    <span><strong>Engine:</strong> {{ page.engine }}</span>
  {% endif %}
  {% if page.platform %}
    <span><strong>Platform:</strong> {{ page.platform }}</span>
  {% endif %}
  {% if page.team_size %}
    <span><strong>Team Size:</strong> {{ page.team_size }}</span>
  {% endif %}
  {% if page.duration %}
    <span><strong>Duration:</strong> {{ page.duration }}</span>
  {% endif %}
  {% if page.date %}
    <span><strong>Date:</strong> {{ page.date | date: "%B %Y" }}</span>
  {% endif %}
</div>