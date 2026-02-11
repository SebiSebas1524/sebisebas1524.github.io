---
layout: project
title: Wasp Engine
description: Wasp Engine is a team-built game engine and demo project focused on creating a solid toolchain for level production and gameplay systems. The goal is to make iteration fast for designers while keeping the runtime systems robust and scalable.
image: /assets/vid/y2c/wasp.gif
hide_image: true
hide_meta: true
tags:
  - engine
  - tools
  - gameplay
  - physics
  - problem solving
  - featured
team_size: 6 Programmers
duration: 8 Weeks
contributions:
  - Blender pipeline add-on (tags, paths, collision)
  - Interactable system (buttons, doors, audio points)
  - Pickup integration and behaviors
  - Collision import fixes and Jolt integration
  - Level blockouts and demo maps
  - Definition of Done checks for PRs
main_category: University Projects
date: 2025-04-08
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <video controls style="width: 100%; height: 100%; object-fit: cover;">
      <source src="/assets/vid/y2c/demo.mp4" type="video/mp4">
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
- Took ownership of the Blender pipeline add-on, refining exports for tags, paths, interactables, and collision.
- Added interactable tags and behavior (button, door, audio point, pickup) so designers can explicitly connect gameplay objects.
- Unified pickups into the interactable system and expanded pickup behaviors.
- Fixed collision import issues by rescaling mesh data and adding world-positioned Jolt bodies.
- Built and iterated on blockout maps and demo levels to validate features.
- Checked Definition of Done criteria before submitting PRs.