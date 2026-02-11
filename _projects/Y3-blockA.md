---
layout: project
title: Minimap Tool System for Godot Engine
description: Public Godot Engine addon (GDExtension in C++) for tile-based minimaps. It supports dynamic tile loading for large maps, basic blip markers, and a full map view for waypoints and navigation.
image: /assets/vid/y3a/godot.gif
hide_image: true
hide_meta: true
tags:
  - godot
  - gdextension
  - tools
  - minimap
  - gameplay
  - featured
team_size: Solo
duration: 8 Weeks
contributions:
  - Core addon architecture and Minimap node
  - Dynamic tile loading and threading
  - Visible tile culling
  - Full map view mode
  - Basic blip system
  - Demo scene integration
main_category: University Projects
date: 2025-09-16
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <video controls style="width: 100%; height: 100%; object-fit: cover;">
      <source src="/assets/vid/y3a/demo.mp4" type="video/mp4">
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


### My contributions
- Built the core addon architecture and `Minimap` control node.
- Implemented dynamic tile loading with background threads and safety checks.
- Added visible-tile culling to keep performance stable on large maps.
- Implemented full map view with zoom-to-fit behavior.
- Created the basic blip system and tile capture visualizer.
- Delivered a playable demo scene and tested integration in a second game.