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
  - ui
  - problem solving
engine: Unreal Engine
team_size: 4 Programmers | 3 Designers | 4 Artists
duration: 8 Weeks
contributions:
  - Fog as a post-process effect (depth fog and ground fog)
  - Material settings for designers
  - Main menu, gamepad navigation and graphics settings menu
  - Problem solving
main_category: University Projects
date: 2024-07-15
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <div style="width: min(100%, 900px); aspect-ratio: 16 / 9;">
    <video
      src="/assets/vid/y1d/trailer.mp4"
      controls
      playsinline
      preload="metadata"
      title="Souls Maze trailer"
      style="width: 100%; height: 100%; object-fit: contain; border-radius: 6px;"
    ></video>
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

Souls Maze is a two player co-op game made by Team Coriander in my first year at BUas. I was one of the four programmers. My work was in three areas:

- **Fog.** This was my research topic for the block. I built the depth fog and the ground fog as a post-process material, with settings the designers can change.
- **Menus.** I made the main menu, the gamepad navigation and the graphics page of the settings menu.
- **Scrum.** I wrote the user story and tasks for my work, and I ran some stand-ups as "Scrum Master".

You can play the game on [itch.io](https://buas.itch.io/team-coriander).

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 280px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-main-menu.webp" alt="Souls Maze main menu" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Main menu</em></figcaption>
  </figure>
  <figure style="flex: 1 1 280px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-role-select.webp" alt="Role select screen with the Gatherer and the Protector" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Role select</em></figcaption>
  </figure>
  <figure style="flex: 1 1 280px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-gameplay.webp" alt="Gameplay in the maze" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Gameplay. Art and level design by the rest of the team.</em></figcaption>
  </figure>
</div>

## Fog

Each programmer picked a research topic for the block. I picked fog.

### What the game needed

Most fog in games is used to make a scene scary or mysterious. Souls Maze needed something different. The designers wanted a warm, light fog that does not cover the ground, because the enemies leave footprints there. It also had to help players see the fruit. I looked at distance fog, height fog and mist, and we agreed on a simple depth fog plus a ground fog.

### Building it as a post-process

Almost everything I found online was about the volumetric fog that is already in Unreal. I found very little about fog as a post-process material, so I built it from scratch. I also lost some time at the start because I thought the engine fog already worked as a post-process. It did not.

### Depth fog

I tried two ways to get the depth. The first was my own calculation, using the distance between the camera and the world position of each pixel. The second was the depth function that Unreal already has. Both worked, but the engine version looked better, so I kept it. I also added a branch so the fog does not touch the sky or the far away areas.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y1d/soulmaze-fog-depth.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Depth fog on</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-fog-compare.webp" alt="The same game without fog" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Fog off</em></figcaption>
  </figure>
</div>

### Ground fog

The ground fog uses the world Z position of each pixel to decide where the fog ends, with a noise texture on top. Making that texture move was the hard part.

My first try used a panner. The texture stuck to the camera and moved with it. My second try used the Triplanar Camera Vector function. The texture stayed in place far away, but it looked wrong right under the camera. What worked was the World Aligned Texture function, animated on the world X and Y axes.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y1d/soulmaze-fog-ground-attempt-1.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Failed attempt</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y1d/soulmaze-fog-ground-attempt-2.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Another failed attempt</em></figcaption>
  </figure>
</div>

### Settings for the designers

I made a material instance for each fog type, so designers and artists can change the fog without opening the material graph. The ground fog has settings for emissive, height end, panner speed, texture size, texture and color. The depth fog has color intensity, maximum density, start distance and color. A designer asked for easier controls, so I also added sliders for the depth fog.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-fog-ground-params.webp" alt="Ground fog material instance settings" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Ground fog settings</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-fog-depth-params.webp" alt="Depth fog material instance settings" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Depth fog settings</em></figcaption>
  </figure>
</div>

### Result

After the designers approved it, the fog went into the main game. It is subtle on purpose. The designers told me it gave the game the atmosphere they wanted. The in-game clip below uses exaggerated settings so the fog is easy to see.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y1d/soulmaze-fog-poc.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Proof of concept in Unreal</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y1d/soulmaze-fog-ingame.mp4" autoplay muted loop playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>In the game, with exaggerated fog</em></figcaption>
  </figure>
</div>

At the end of the block I wrote a research document with a reflection on each stage. If I worked on the fog again, I would interpolate between two noise textures (an idea from a peer), add exponential fog, and make the ground fog move up and down.

## Menus

### Main menu and gamepad navigation

I made the main menu with Blueprints. The first version only worked with a mouse. With a gamepad, Unreal's focus function did not do what I needed: the button was not focused and did not change color. I fixed it by keeping all the buttons in an array. Up and down input changes an index, and the button at that index acts as the focused one.

<figure style="margin: 1.5rem 0;">
  <video src="/assets/vid/y1d/soulmaze-menu-gamepad.mp4" autoplay muted loop playsinline style="width: 100%; max-width: 800px; border-radius: 6px;"></video>
  <figcaption><em>First version of the menu, moving with a gamepad</em></figcaption>
</figure>

### Options menu

Later, another programmer made a base class for the menu widgets, with the functions for moving between buttons. I used it for the rest of the menus in the game. Then I built the options menu together with another programmer. I made the graphics page and they made the volume page.

The graphics page has window mode, resolution, anti-aliasing, post process, shadows, lighting, texture, effects, upscale and frame generation. The constructor of the widget defines each category and loads the current settings from the game, and the Apply button applies all of them. The designers sketched the UI first, and I checked the layout with a designer and a visual artist while I built it.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-settings-first.webp" alt="First version of the options menu" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>First version</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <img src="/assets/img/y1d/soulmaze-settings-final.webp" alt="Final graphics settings page" loading="lazy" style="width: 100%; border-radius: 6px;">
    <figcaption><em>Final graphics page</em></figcaption>
  </figure>
</div>

<figure style="margin: 1.5rem 0;">
  <video src="/assets/vid/y1d/soulmaze-settings-menu.mp4" autoplay muted loop playsinline style="width: 100%; max-width: 800px; border-radius: 6px;"></video>
  <figcaption><em>The final options menu</em></figcaption>
</figure>

The menu works well, but we needed it quickly, so some of the code is longer than it should be. If I worked on it again, I would split it into functions to make it easier to read and change.

## Working with the team

We used Scrum, and I took part in all of it. I wrote a user story and tasks for the fog and added tasks to the board every sprint. I helped write the team contract, joined the sprint reviews and retrospectives, and ran some stand-ups as Scrum Master.

I also helped outside my own tasks. I helped a designer with a problem with the turn points in a maze layout, which gave us more maps to playtest. I gave advice on sound editing, and new sounds went into the game.

## What I learned

- How to build a custom post-process material in Unreal when the engine has no ready solution.
- How to build menus in Blueprints that work with both mouse and gamepad, and how to use a shared widget base class.
- To check what already exists before building something from scratch. I would have saved time on the fog if I had done that first.
- To break big tasks into smaller ones, which made the work easier to finish and to review with the team.
