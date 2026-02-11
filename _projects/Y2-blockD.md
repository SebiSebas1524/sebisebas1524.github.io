---
layout: project
title: Going Bonkers
description: Going Bonkers! is a local co-op game following two clowns, with a knack for bonking, as they fight their way through hordes of salarymen to brighten a dreary city in this twin stick bonk-em-up!
image: /assets/vid/y2d/trailer.gif
hide_image: true
hide_meta: true
tags:
  - unreal
  - ci-cd
  - tools
  - leadership
  - problem solving
  - featured
team_size: 3 Programmers | 6 Designers | 12 Artist
duration: 2024-2025 Block D
contributions:
  - PR lead planning, QA process, and risk tracking
  - CI/CD setup with Jenkins and itch.io deployment
  - Level streaming and level stitching workflow
  - Checkpoint save/load prototype
  - Build and Perforce tech support
main_category: University Projects
date: 2025-07-15
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <iframe
      style="width: 100%; height: 100%; border: 0;"
      src="https://www.youtube.com/watch?v=-iL51jJXd2k"
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

## Overview

Going Bonkers is a team project where I served as programmer lead. I focused on improving build reliability and team workflow while delivering technical features that helped the game scale across multiple levels.

## Contributions
- Set up Jenkins CI/CD with scheduled builds and itch.io deployment for reliable team testing.
- Implemented level streaming and stitched multiple levels into a continuous main level.
- Prototyped checkpoint save/load to restart from gate checkpoints.
- Provided tech support for build errors, Perforce issues, and critical bugs.
- Led programmer planning with scope breakdowns, QA processes, and risk tracking.