# Interactive Bézier Curve with Physics & Sensor Control

## Project Overview

This project implements an **interactive cubic Bézier curve** that behaves like a **springy rope** responding to real-time user input. The implementation is done **entirely from scratch**, covering Bézier mathematics, tangent computation, spring–damping physics, and real-time rendering.

The goal of the project is to demonstrate understanding of:

* Parametric curves (Bézier curves)
* Vector math and derivatives
* Simple physics simulation
* Real-time interaction and rendering

This submission uses a **Web (HTML + JavaScript + Canvas)** implementation controlled via **mouse input**.

---

## Features Implemented

* Manual implementation of **cubic Bézier curve math**
* Smooth curve rendering using sampled points
* **Dynamic control points** with spring-damping physics
* **Tangent vector visualization** using analytical derivatives
* Real-time interaction at ~60 FPS
* Clean separation of math, physics, input, and rendering logic

---

## Bézier Curve Mathematics

The curve is defined using four control points:

* **P₀, P₃** → fixed endpoints
* **P₁, P₂** → dynamic control points

The cubic Bézier equation used is:

[ B(t) = (1−t)^3P_0 + 3(1−t)^2tP_1 + 3(1−t)t^2P_2 + t^3P_3 ]

The curve is sampled from **t = 0 to 1** with small increments (`Δt = 0.01`) and rendered as connected line segments.

---

## Tangent Computation

Tangent vectors are computed using the derivative of the cubic Bézier function:

[ B'(t) = 3(1−t)^2(P_1−P_0) + 6(1−t)t(P_2−P_1) + 3t^2(P_3−P_2) ]

For visualization:

* Tangents are calculated at fixed intervals along the curve
* Each tangent vector is **normalized**
* Short line segments are drawn to indicate direction and curvature

This provides a clear visual understanding of how the curve changes dynamically.

---

## Physics Model (Spring–Damping)

The dynamic control points (**P₁ and P₂**) follow target positions using a spring-damping model:

[ a = -k(x - x_{target}) - d \cdot v ]

Where:

* `k` is the spring constant
* `d` is the damping coefficient
* `v` is velocity

This results in:

* Smooth motion
* Natural oscillation
* Gradual settling (rope-like behavior)

The physics is updated every animation frame.

---

## Interaction Model

* Mouse movement sets **target positions** for the dynamic control points
* Control points do **not snap** to the cursor
* Instead, they smoothly follow using spring physics

This produces an intuitive and physically believable interaction.

---

## Rendering & Performance

* Rendering is done using **HTML5 Canvas**
* Animation loop uses `requestAnimationFrame`
* Maintains approximately **60 FPS**

The following elements are rendered:

* Bézier curve path
* Control points (as circles)
* Tangent vectors along the curve

---

## Project Structure

* **Math**: Bézier point & derivative calculations
* **Physics**: Spring-damping motion logic
* **Input**: Mouse event handling
* **Rendering**: Canvas drawing functions

All logic is implemented manually without using:

* UIBezierPath
* SVG/D3.js
* Physics or animation libraries

---

## How to Run

1. Open the `index.html` file in any modern web browser
2. Move the mouse across the screen
3. Observe the curve reacting dynamically

No build tools or dependencies are required.

---

## Screen Recording Demonstration

The screen recording shows:

* Initial static curve and control points
* Mouse-driven interaction
* Springy oscillation and damping behavior
* Tangent vectors updating in real time

---

## Design Choices

* Spring physics was chosen for simplicity and realism
* Tangent visualization helps verify derivative correctness
* Fixed endpoints ensure curve stability
* Minimalistic visuals keep focus on math and motion

---

## Conclusion

This project demonstrates a complete, low-level implementation of an interactive Bézier curve system with real-time physics and visualization. All mathematical and physical behavior is explicitly coded, meeting the assignment requirements without reliance on external libraries or APIs.
# FlamApp_assignment
