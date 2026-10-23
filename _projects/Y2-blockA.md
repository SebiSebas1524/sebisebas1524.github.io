---
layout: project
title: BEE Engine
description: A solo C++ engine project built on the Bee starter engine from BUas. It runs on PC and PS5, and I extended it with a particle system powered by EnTT, an ImGui editor, JSON saving, a resource manager, a GLTF loader and a tile-based level editor.
image: /assets/vid/y2a/engine.gif
hide_image: true
hide_meta: true
tags:
  - cpp
  - engine
  - tools
  - ecs
engine: Custom C++ engine (OpenGL)
platform: PC | PS5
team_size: Solo
duration: 8 Weeks
contributions:
  - Particle system with EnTT (ECS)
  - ImGui editor with docking, gizmos and debug tools
  - Saving and loading with Cereal (JSON)
  - Resource manager and GLTF loader
  - Tile-based level editor
  - Cross-platform code for PC and PS5
main_category: University Projects
date: 2024-11-01
---

<div style="display: flex; justify-content: center; margin: 1.25rem 0;">
  <video src="/assets/vid/y2a/engine-demo-level.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: min(100%, 900px); border-radius: 6px;"></video>
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

In this project I worked alone on an engine for 8 weeks. The school gave us a starter engine called Bee, and each week had a deliverable: a particle system, an editor, saving and loading, a resource manager, and a level editor. I wrote each of these systems myself. The engine runs on both PC and PS5, and the demo is a separate project.

The video above is the final demo. A particle emitter moves through a city level put together with the level editor, and you can fly around it with the camera.

## Engine and app

I kept the engine and the demo as two separate projects. The engine is a library, and the demo only uses it, so the engine does not depend on the game. The demo shows this well: its `main` only needs two lines, one to load the map and one to load a particle.

The `Engine` class owns the systems and gives access to them. Some of the systems are low level (device, input, file IO, audio), some are small tools (timer, resource manager), and some work with ECS (particles, GLTF models, the grid). The diagram shows how they connect.

<figure style="margin: 1.5rem 0;">
  <img src="/assets/img/y2a/engine-flowchart.webp" alt="Diagram of the engine, its systems and the app" loading="lazy" style="width: 100%; max-width: 800px; border-radius: 6px;">
  <figcaption><em>How the engine is organized</em></figcaption>
</figure>

I also tried to keep the classes simple. For example, the `Camera` only has public functions for the things that other code needs: update it, and get the view matrix, the projection and the position. Everything else is private, so nobody can break how the camera works from the outside.

## Running on PC and PS5

The engine compiles and runs on both platforms. I did this with platform macros and with the Pointer to Implementation method for classes like `Input` and `Device`. The rest of the engine talks to one interface, and the PC and PS5 versions live in separate platform folders.

The same idea helped with time. I made a `Timer` class that gives the engine a dynamic time step or a fixed one.

<figure style="margin: 1.5rem 0;">
  <video src="/assets/vid/y2a/engine-timestep.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; max-width: 500px; border-radius: 6px;"></video>
  <figcaption><em>Dynamic and fixed time step</em></figcaption>
</figure>

## Particle system

In the particle system, every emitter and every particle is an entity in EnTT. Each one only gets the components it needs, like position, color, life and size, and the system loops over the entities that have them. I first made a simple version without EnTT to understand how particles work. Then I moved it to ECS. I changed my entity structure three times before I found one that I liked.

Emitters have a cone angle, direction, spawn rate, lifetime, size, speed and a start and end color. I added mass and the two colors as extras, and the particles react to gravity.

<figure style="margin: 1.5rem 0;">
  <video src="/assets/vid/y2a/engine-particle-types.mp4#t=0.1" autoplay muted loop playsinline style="width: 100%; max-width: 900px; border-radius: 6px;"></video>
  <figcaption><em>Three types of particles</em></figcaption>
</figure>

## Editor

The `Interface` class is the editor, built with ImGui. I wanted one place for all the UI, so it is easy to add new tools later. It has a viewport and a menu that you can dock, a gizmo to move things around, and controls for the light, the camera and the emitters. For debugging, I can pause the game, step one frame, and draw the direction and velocity of the particles.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-editor-ui.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Changing emitter settings in real time</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-editor-docking.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>The editor with docking, a viewport and a menu</em></figcaption>
  </figure>
</div>

## Saving and loading

Emitters and levels are saved as JSON files with the Cereal library. For a particle, I save its settings. For a level, I save the file path and the transform of every model, and when I load it I go through the list and load them again. After a restart, the level comes back with the same layout.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-save-particle.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Saving a particle and loading it again</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-level-save.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Saving a level and loading it after a restart</em></figcaption>
  </figure>
</div>

## Resource manager and GLTF loader

The resource manager is one template class that loads, removes and clears resources, and counts how many times each one is used. If I ask for a model that is already loaded, I get the same one back and the count goes up. This stops the engine from loading the same model many times. I used the Zero Rule from the lecture and ideas from my peers to make it work for any type of resource.

The GLTF loader uses the resource manager and puts each model into the ECS as an entity. It works with models that have a hierarchy, like a car made of several parts, and with models that do not.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-gltf-hierarchy.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Loading a model with a hierarchy and one without</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-resource-manager.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Loading and unloading models, with reference counts</em></figcaption>
  </figure>
</div>

## Level editor

The level editor uses a grid made of AABB boxes. You pick a model from the list, select a tile on the grid, and press `X` to place it. At first I checked the boxes one by one to find the selected tile. A peer suggested casting a ray from the camera instead. It worked well, and once I understood it, I started using it myself.

I added some extras. Holding `Ctrl` snaps a model to the grid, and `R`, `G` and `T` switch the gizmo between rotate, scale and translate.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin: 1.5rem 0;">
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-tile-load.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Placing a model on a tile</em></figcaption>
  </figure>
  <figure style="flex: 1 1 320px; margin: 0;">
    <video src="/assets/vid/y2a/engine-tile-snap.mp4#t=0.1" controls preload="metadata" muted playsinline style="width: 100%; border-radius: 6px;"></video>
    <figcaption><em>Grid snapping and gizmo keybinds</em></figcaption>
  </figure>
</div>

## Code quality

Both the PC and PS5 builds compile with warning level 4 and warnings as errors, and the code passes clang-tidy with the C++ Core Guidelines settings on both platforms. Most of the fixes were small things: using `const` where I could, setting a value on every variable before using it, and avoiding conversions that can lose data. One warning only showed up on PS5. It came from a deprecated allocator in the EnTT library, and I fixed it by changing the allocator type.

## What I learned

- An engine and an application are different things. I learned to keep the engine as a library and to show only what the outside needs.
- In ECS, how you split your entities and components matters a lot. I changed mine three times before I found a structure that worked.
- To support two platforms, hide the differences behind one interface and keep the platform code in its own place.
- Casting a ray from the camera is a more effective way to pick a tile than checking the boxes one by one. I found this by asking a peer.
- New libraries like ImGuizmo took me time to understand. Looking at examples and asking peers helped me the most.