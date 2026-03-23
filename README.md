# AeroSim - NACA Airfoil Smoke Visualization (Work in progress)

Simple real-time smoke visualization of airflow around a **NACA 4-digit airfoil**, written in **C++** with **SDL2**.

This project was created as an **educational and visual approximation** of airflow around an airfoil - **not** as a physically accurate CFD solver. The goal was to build something interactive, lightweight, and visually clear, while exploring airfoil geometry, flow behavior, wake formation, and stall-like effects.

## Preview

This application renders a 2D smoke field flowing around a selected NACA airfoil profile. You can change the airfoil, adjust the angle of attack, modify the inlet speed, and observe how the smoke pattern changes in real time.

## Features

- Real-time 2D smoke visualization
- Multiple **NACA 4-digit airfoil presets**
- Adjustable **angle of attack**
- Adjustable **inlet flow speed**
- Smoke speed slider
- Approximate **flow attachment** near the airfoil
- Dynamic **wake turbulence**
- Approximate **stall / flow separation effect** at higher AoA
- Lightweight UI overlay

## Controls

- **A / D** - decrease / increase angle of attack
- **W / S** - increase / decrease inlet speed
- **R** - reset smoke
- **Mouse** - select NACA preset
- **Mouse drag** - change smoke speed with the slider
- **ESC** - exit

## Included NACA presets

The project currently includes the following example airfoils:

- NACA 0012
- NACA 2412
- NACA 4412
- NACA 6412
- NACA 2424

## How it works

The simulation uses a simplified grid-based smoke advection model with a manually constructed velocity field.

### Airfoil geometry
The airfoil shape is generated from the standard **NACA 4-digit formulation**:
- thickness distribution
- camber line
- camber position

The resulting outline is rasterized into a solid mask used by the simulation.

### Static flow field
A base velocity field is built from:
- uniform inlet flow
- a simple circulation-like component around the airfoil
- an approximate attachment effect near the surface
- a mild wake behind the airfoil

### Dynamic flow field
Each frame adds time-dependent turbulence to the wake region and, at higher angles of attack, a stronger separation zone that imitates stall behavior.

### Smoke update
The smoke field is advected through the velocity field using backward sampling and then lightly smoothed for a cleaner visual result.

## Important note on realism

This is **not a CFD solver** and it is **not intended to produce physically accurate aerodynamic data**.

The simulation is based on simple heuristics and visual approximations designed for:
- education
- experimentation
- interactive visualization
- portfolio purposes

That was the intended design from the beginning.

It should be understood as:

> a real-time educational airflow visualization around NACA airfoils

and **not** as a high-fidelity aerodynamic analysis tool.

## Why I made this

I am interested in both **computer science** and **aviation**, so I wanted to build a project that combines:
- programming
- real-time rendering
- geometry
- simple simulation ideas
- aviation-related concepts

The goal was to create something technically interesting, visually understandable, and fun to experiment with.

## Technical highlights

- Written in **C++**
- Uses **SDL2** for rendering and input
- Uses **SDL_ttf** for text/UI
- Designed to stay simple and interactive

## Build

### Requirements

- C++
- CMake
- SDL2
- SDL2_ttf

### Example build commands

```bash
cmake -S . -B build
cmake --build build
./build/app
