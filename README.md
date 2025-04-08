# Enterprise Architecture Diagram – Enhanced Interactive Version

This project contains a single HTML file that implements an interactive enterprise architecture diagram using D3.js. The diagram visually represents various layers (e.g., Client, Frontend, App, Backend, etc.) along with the connections between them. Users can interact with the diagram through zooming, panning, keyboard shortcuts, and dynamic detail panels.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Installation and Usage](#installation-and-usage)
- [Customization](#customization)
- [Interactivity & Keyboard Shortcuts](#interactivity--keyboard-shortcuts)
- [Developer Notes](#developer-notes)
- [License](#license)

## Overview

The diagram is built using HTML, CSS, and JavaScript. Its goal is to provide a dynamic and interactive visualization of enterprise architecture by letting users:
- **View** detailed information about each layer and connection.
- **Interact** with the diagram via drag-and-drop node movement.
- **Adjust** connection parameters (offsets and path mode) using a user-friendly sidebar.
- **Animate** data flow along connections to simulate network or system activity.
- **Control** the diagram using keyboard shortcuts and on-screen controls.

## Features

- **Interactive Nodes and Links:** The diagram contains nodes that represent different system layers. Each node and the connections between them are rendered on an SVG canvas.
- **Zoom and Pan:** Users can zoom in/out and pan across the diagram using both mouse and on-screen control buttons.
- **Dynamic Detail Panel:** Clicking on a node or connection displays detailed information in a sidebar panel. The sidebar shows properties such as responsibilities, technologies, connection protocols, and business impact.
- **Editable Settings:** When unlocked, users can edit layer positions, dimensions, and connection properties using intuitive forms. All changes are immediately reflected in the diagram.
- **Keyboard Shortcuts:** Arrow keys are mapped for precise adjustments of node positions and connection offsets. The space bar toggles the connection path mode between “straight” and “orthogonal.”
- **Animated Data Flow:** The connections simulate a data flow animation by displaying moving arrows along each connection path.
- **Export Configuration:** Users can save the current state (including node positions, connection offsets, and zoom level) as a JSON file.

## Project Structure

Even though this is a single HTML file project, the code is organized into clear sections:

- **HTML Structure:**  
  The `<body>` consists of the diagram area (`#diagram`), a fixed sidebar (`.connection-details`) for details and editing controls, and top controls (for zooming, resetting, etc.).
  
- **CSS Styling:**  
  The `<style>` section contains all the styles including layout (e.g., diagram container, sidebar, top controls), typography, node/link styling, and responsive behavior.

- **JavaScript:**  
  The `<script>` section is divided into multiple parts:
  - **Color & Gradient Definitions:** A color map and gradient definitions for nodes and connection arrows.
  - **Data Definitions:**  
    - `layerDetails`: Contains metadata about each layer (description, responsibilities, technologies, challenges).
    - `connectionDetails`: Contains properties for each connection (protocol, data flow, technical stack, business impact).
  - **Node & Link Classes:** Custom JavaScript classes for creating and managing nodes and links. These classes include methods for rendering, dragging, updating paths, and applying changes.
  - **Diagram Class:**  
    This class initializes the diagram, handles zoom/pan behaviors, creates legends, implements data flow animations, and manages user interactions (clicks, keyboard shortcuts, and form controls).
  - **Event Handlers & Initialization:**  
    Final code sets up the diagram instance, locks editing by default, and connects event listeners for user inputs and UI controls.

## Dependencies

- **D3.js (v7.8.5):**  
  The diagram uses the D3.js library for SVG manipulation, transitions, and handling drag/zoom events. The script is loaded via a CDN:
  ```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js"></script>
  ```
- **Modern Web Browser:**  
  The project is designed to work in any modern web browser with support for HTML5, CSS3, and JavaScript (ES6).

## Installation and Usage

1. **Download or Clone the Project:**  
   Save the HTML file (e.g., `index.html`) to your local machine.

2. **Open in a Web Browser:**  
   Simply double-click the file or open it with your preferred browser. No server is required because the file is self-contained.

3. **Interact with the Diagram:**  
   - **Nodes:** Click on any node to view and edit its details. You can drag the nodes to rearrange the diagram.
   - **Connections:** Click on any connection (labeled C1-C14) to open the detail panel. Edit connection offsets or toggle between path modes.
   - **Top Controls:** Use the buttons to zoom in, zoom out, reset zoom/layout, save configuration, or toggle between locked/unlocked editing.
   - **Sidebar:** Use the right-hand sidebar to view details and modify settings.
   - **Keyboard:** When editing is unlocked, use arrow keys for adjusting positions and offsets. Hold `Shift` to modify target connection offsets or modify node positions faster.

4. **Saving the Current Configuration:**  
   Click the “Save Config” button to export the current diagram state (node positions, connection settings, and zoom level) as a JSON file.

## Customization

- **Modify Layers or Connections:**  
  Edit the `nodeData` and `linkData` objects inside the script section to add, remove, or modify nodes and links.

- **Adjust Styling:**  
  Tweak the CSS styles in the `<style>` section to change the appearance of nodes, edges, legends, or the overall page layout.

- **Enhance Functionality:**  
  The JavaScript classes (`Node`, `Link`, and `Diagram`) are written in a modular way so you can extend their capabilities. For instance, you might add tooltips, adjust animations, or integrate additional UI features.

- **Update Gradients and Colors:**  
  Change the `colorMap` and `gradientDefinitions` objects to fit your own color scheme or corporate identity.

## Interactivity & Keyboard Shortcuts

- **Zoom Controls:**  
  Use the on-screen buttons to control zoom level, or use mouse scroll (with D3’s built-in zoom behavior).

- **Editing Mode:**  
  By default, editing is locked. Click the lock/unlock button (top controls) to enable editing mode.

- **Keyboard Shortcuts:**  
  - **Node Movement:**  
    - Arrow keys move the selected node by 1 pixel (or 10 pixels with the Shift key).
  - **Connection Adjustment:**  
    - When a connection is selected, arrow keys (without Shift) adjust source offsets.
    - With the Shift key held, the arrow keys adjust the target offsets.
    - Press the **Space bar** to toggle connection path mode between straight and orthogonal.
  
A panel summarizing these shortcuts is displayed (or hidden when locked) in a fixed overlay on the page.

## Developer Notes

- **Event Handling:**  
  All interactions are designed to avoid conflicts, using event propagation control (`event.stopPropagation()`) to prevent unwanted behaviors.

- **Data Flow Animation:**  
  The code sets up an animated data flow on each link by creating and transforming SVG arrow elements. The animation uses `requestAnimationFrame` for smooth updates.

- **State Management:**  
  The global `diagramInstance` object allows various parts of the code (e.g., keyboard shortcuts, sidebar forms) to interact with the current state of the diagram.

- **Debugging and Testing:**  
  For further improvements, consider adding logging to monitor changes in node positions or connection settings. Also, test in different browsers to ensure consistent performance.


