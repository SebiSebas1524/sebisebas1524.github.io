---
layout: project
title: Custom Engine in C++ with OpenGL
description: My first custom engine that I learned a lot on how to make a proper engine.
image: /assets/vid/y2a/demo.gif
hide_image: true
hide_meta: true
tags:
  - Engine
  - Tools
  - EnTT
  - ImGui
  - Cereal
  - GLTF
  - PS5
  - Rubric
  - Evidence
team_size: Solo
duration: 8 Weeks
contributions:
  - Engine-game separation with fixed and dynamic timestep
  - Timer system for delta time management
  - EnTT particle system with emitters and component-driven updates
  - ImGui tooling for live particle control and visualization
  - Cereal JSON serialization for emitters and assets
  - Cross-platform abstractions for input and device layers
  - GLTF resource manager with reference counting
  - Tile-based level editor with grid snapping and ImGuizmo tools
main_category: University Projects
date: 2024-09-20
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <video controls style="width: 100%; height: 100%; object-fit: cover;">
      <source src="/assets/vid/y2a/demo.mp4" type="video/mp4">
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