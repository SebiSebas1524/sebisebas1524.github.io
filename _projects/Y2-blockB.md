---
layout: project
title: Level Streaming in C++
description: I developed a dynamic level streaming system for the Bee engine (CMGT Engine) that asynchronously loads and unloads GLTF models based on player proximity and camera frustum culling. I implemented multithreaded loading using std::promise and std::future, created debug visualization tools including a minimap and memory profiler, and optimized the system through performance profiling.
image: /assets/vid/y2b/prev.gif
hide_image: true
hide_meta: true
tags:
  - C++
  - Custom Engine
  - Assets Streaming
  - featured
team_size: Solo
duration: 8 Weeks
contributions:
  - Level streaming system
  - Multithreaded loading
  - Debug tools and profiling
main_category: University Projects
date: 2025-01-27
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <video controls style="width: 100%; height: 100%; object-fit: cover;">
      <source src="/assets/vid/y2b/demo.mp4" type="video/mp4">
    </video>
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