---
layout: default
title: Project Documentation
---

# Project Documentation

<p class="intro-text">⋆⭒˚.⋆ This page holds my project documentation for Creative Embedded Systems this semester! ⋆⭒˚.⋆</p>

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

<div class="project-media">
  <img src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-full.png" alt="Full installation">
</div>

<div class="project-media">
  <img src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-closeup.jpg" alt="Screen close-up">
</div>

<div class="project-media">
  <img src="https://raw.githubusercontent.com/Sanjidahjahan/Ocean-Generative-Art/main/images/installation-wired.png" alt="Wired installation">
</div>

### Project Repository

[Click for Ocean Generative Art GitHub repository](https://github.com/Sanjidahjahan/Ocean-Generative-Art)

---

## Project 2: Digital Etch A Sketch

### Artistic Vision

For this project, I wanted to recreate the nostalgic experience of using an Etch A Sketch but give it a digital twist. I liked the idea of taking a familiar childhood drawing toy and turning it into an interactive experience using physical controls and a computer screen.

I wanted the design to feel recognizable, so I kept the classic red frame and round control knobs as inspiration. I used a soft pink drawing screen with gold details to give the interface its own visual style while still keeping the appearance of the original toy.

My goal was to make drawing feel simple and playful. Instead of using a mouse, users control the drawing with a physical joystick. They can also change the brush size, switch colors, and clear the screen using the other physical components. I wanted the project to combine the feeling of a traditional drawing toy with the flexibility of digital interaction.

### Important Design Decisions

One of my main design decisions was keeping the familiar appearance of the original Etch A Sketch while creating a digital version. I chose a deep red frame, a soft pink drawing area, and gold details to make the interface feel like a redesigned version of the original toy.

I also decided to use physical controls instead of having users interact with the screen using a mouse. The joystick controls the drawing movement, while clicking the joystick cycles through three brush sizes: 4, 7, and 10. I added a potentiometer to let users switch between five drawing colors and a separate yellow button to clear the screen.

Another decision was adding a small on-screen indicator showing the selected brush size and color. This makes it easier for users to understand which settings they are using without having to guess.

Throughout the process, I adjusted the interface and controls based on testing. I wanted the different brush sizes and colors to be noticeable, while keeping the overall design simple and close to the original Etch A Sketch experience.

### Technical Implementation

The project uses an ESP32 TTGO T-Display connected to a joystick, push button, and potentiometer. I used Arduino IDE to read the sensor inputs and Processing to create the digital drawing interface.

The Arduino code continuously reads the joystick's X and Y positions, the joystick click, the yellow push button, and the potentiometer value. It sends these five values to Processing through serial communication as a comma-separated line. Processing reads this information and uses it to control the drawing experience.

One of the most important parts of my Processing code is how the joystick controls the drawing cursor:

```java
float speedX = map(joyX, 0, 4095, -6, 6);
float speedY = map(joyY, 0, 4095, -6, 6);

if (abs(joyX - 2048) < 350) speedX = 0;
if (abs(joyY - 2048) < 350) speedY = 0;

penX = constrain(penX + speedX, 0, screenW - 1);
penY = constrain(penY + speedY, 0, screenH - 1);
```

This code maps the joystick readings into drawing movement on the screen. The dead zone prevents the cursor from drifting when the joystick is not being touched, and `constrain()` keeps the cursor within the drawing area.

I also used a PGraphics drawing layer to keep the lines on the screen as the interface updates. This allows the drawing to remain visible while the rest of the interface is redrawn.

One challenge I encountered was getting all the physical components to communicate correctly with Processing. I had to troubleshoot the serial connection between the ESP32 and my Mac, as well as the potentiometer readings. I also adjusted the brush sizes after testing because the original difference between the sizes was difficult to notice. I eventually used three sizes, 4, 7, and 10, and added an on-screen indicator showing the selected brush size and color.

Working through these issues helped me understand how sensor inputs, serial communication, and Processing work together to create an interactive experience.

### AI Support Used

I used ChatGPT (GPT-6) throughout this project for coding assistance and troubleshooting. It helped me better understand parts of my Arduino and Processing code, work through hardware and serial connection issues, and make improvements to the drawing interface.

Some examples of prompts I used include:

- "Why does my Mac show the cu.usbserial port as disconnected, even though my ESP32 was connecting and working before?"
- "How can I make the different brush sizes in my Processing sketch more visible while keeping the drawing experience the same?"
- "How can I add an indicator on the screen that displays the currently selected brush size and color without changing the original Etch A Sketch-inspired design?"

I used ChatGPT to help me understand problems, explore possible solutions, and make improvements as I developed the project. I tested changes with my actual hardware and Processing sketch and adjusted the design based on what worked. 

### Visual Documentation

Here are videos demonstrating my Digital Etch A Sketch project and its main features.

**Project Demonstration**

<video controls width="100%" src="Demo-esp32.mp4"></video>

**Drawing Interface and Controls**

<video controls width="100%" src="Etch-a-sketch-demo.mov"></video>

**Changing Colors and Brush Sizes**

<video controls width="100%" src="Etch-a-sketch-colors-brush.mov"></video>

**Hardware Setup**

![ESP32 breadboard setup](ESP32_breadboard.jpg)

### Project Repository

You can find the Arduino and Processing code, README, GIF demonstration, and circuit diagram in my GitHub repository:

[Digital Etch A Sketch – GitHub Repository](https://github.com/Sanjidahjahan/digital-etch-a-sketch)
