# RoboSub 30A ESC Current Sensor

<img width="1049" height="841" alt="image" src="https://github.com/user-attachments/assets/6af2140a-0680-4e72-9644-64b6490f8242" />


## Overview
A custom-designed, high-current printed circuit board (PCB) engineered to monitor up to 30 Amps of continuous current draw from Electronic Speed Controllers (ESCs) in an Autonomous Underwater Vehicle (AUV). Designed from schematic capture to fabrication using **Altium Designer**.

This module utilizes the Allegro ACS712 Hall-effect linear current sensor to provide precise analog feedback to the vehicle's central control system while maintaining complete galvanic isolation between the high-power propulsion loops and sensitive logic circuits.

## Key Specifications
* **Max Continuous Current:** 30A
* **Sensing Technology:** Hall-Effect (ACS712)
* **Input Connectors:** Vibration-resistant Wago Spring-Clamp Terminals
* **Output:** Scaled analog voltage (proportional to current flow)
* **PCB Specs:** 2-Layer, 2 oz Copper, 1.6mm FR4

## Hardware Design Highlights
As this board handles high continuous currents and inductive loads from ESCs, several specific hardware design principles were implemented to ensure thermal stability and electrical safety:

* **High-Current Polygon Routing:** Standard traces were discarded in favor of massive, direct-connect (zero thermal relief) copper polygon pours on both the Top and Bottom layers to drastically reduce $I^2R$ power losses and heat generation.
* **Via Stitching:** The top and bottom current-carrying polygons are heavily stitched together using a dense via grid to halve the electrical resistance and improve thermal dissipation.
* **Thermal Management via Solder Mask Retraction:** The solder mask over the high-current paths was intentionally exposed (removed) in the Gerber generation. This allows for the physical build-up of thick silver solder or solid copper wire reinforcement during assembly to handle extreme transient current spikes.
* **Galvanic Isolation / Creepage:** A strict physical routing keep-out zone was enforced between the high-voltage/high-current domain (Wago terminals and Pins 1-4) and the low-voltage logic domain (Pins 5-8) to prevent high-voltage arcing.
* **Custom Footprints:** Custom Altium library footprints were designed for PCB-mount Wago spring-clamp terminals to guarantee fail-safe, vibration-proof connections that standard screw terminals cannot provide in mobile robotics.

![Schematic Screenshot]([Insert link to a screenshot of your Altium schematic here])

## Repository Structure
* `/Altium_Source`: Contains the raw Altium Designer project files (`.PrjPcb`, `.SchDoc`, `.PcbDoc`).
* `/Fabrication`: Contains the manufacturing-ready Gerber files, NC Drill files, and Pick & Place files.
* `BOM.csv`: The complete Bill of Materials.

## Fabrication
This board is fully DRC-compliant and ready for manufacture. The `.zip` file located in the `/Fabrication` directory can be uploaded directly to standard fabrication houses (e.g., JLCPCB, PCBWay) using a 2-Layer, 2oz Copper specification.
