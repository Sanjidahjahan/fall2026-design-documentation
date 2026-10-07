---
layout: default
title: Project Documentation
---

# Project Documentation

⋆⭒˚.⋆ This page holds my project documentation for Creative Embedded Systems this semester! ⋆⭒˚.⋆

## Project 1: Ocean Generative Art

### Artistic Vision

For this project, I wanted to create a small underwater environment that felt calm and playful but still had a moment of surprise. I designed the physical installation as an aquarium ocean exhibit ticket made from a paper envelope. The cutout in the ticket frames the TFT display, making the screen feel like a window into the ocean.

My goal was for the viewer to feel like they were looking through an aquarium ticket and seeing a small underwater world inside it. I wanted the animation to feel like a living environment rather than just objects moving randomly.

### Design Decisions

I chose to use a blue ocean gradient that becomes darker toward the bottom to create depth. I also added small moving wave lines at the top of the screen to make the water look like it's moving.

The fish were designed to be randomized in size, color, position, and speed so that the scene would feel less repetitive. I also added bubbles that slowly rise through the water.

The biggest design decision was the shark interaction. I wanted the shark to create a sudden change in the calm environment. When the shark gets close to the fish, they instantly turn around and swim away at a much faster speed. Once the shark leaves the screen, the fish return and the calm environment continues.

For the physical installation, I used a paper envelope with a cutout for the display. This made the screen feel like an aquarium window while the envelope itself became part of the design.

### Technical Process

I programmed the project using an ESP32 and TFT display in Arduino. I used the TFT_eSPI and SPI libraries to control the display.

The animation uses a sprite buffer so the ocean, fish, bubbles, and shark can be drawn before being pushed to the screen. This helped the animation look smoother since a lot of the elements were moving at the same time.

The fish are controlled using arrays for their position, size, speed, direction, and color. They normally swim across the screen and wrap around when they reach the edge. When the shark becomes active, the fish change direction and move faster.

### Technical Challenges

One challenge was getting multiple animated elements to move smoothly at the same time. I used a sprite buffer to draw the full scene before displaying it, which helped reduce visual flickering.

Another challenge was making the shark interaction noticeable. At first, simply having the shark swim across the screen did not make it feel like part of the environment. I changed the behavior so that the fish react when the shark gets close. They immediately turn around and swim away faster, making the shark feel like it actually affects the environment.

### Physical Installation

The TFT display is placed behind a cutout in a paper envelope so that the screen becomes the ocean portion of the aquarium ticket. The ESP32 and LiPo battery are kept behind the envelope. I decorated the front of the envelope to make it look like an aquarium ocean exhibit ticket.

### Visual Documentation

<h4>Final Module 1 Project Video</h4>

<div class="project-video">
  <video autoplay muted loop playsinline controls>
    <source src="video/demo.video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<h4>Installation Photos</h4>

<img class="project-image" style="width: 850px; max-width: 100%; height: 450px; object-fit: cover;" src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-full.png" alt="Full installation">

<img class="project-image" style="width: 850px; max-width: 100%; height: 450px; object-fit: cover;" src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-closeup.jpg" alt="Screen close-up">

<img class="project-image" style="width: 850px; max-width: 100%; height: 450px; object-fit: cover;" src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-wired.png" alt="Wired installation">

### Project Repository

[Click for Ocean Generative Art GitHub repository](https://github.com/Sanjidahjahan/Ocean-Generative-Art)
