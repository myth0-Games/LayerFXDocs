# Package Contents

The LayerFX package contains the following:

- The **LayerFX Render Feature**, supporting 3 different rendering modes and a wide
variety of customization options. Full source code is included, allowing advanced
users to inspect, debug, and customize the render feature if needed.
- A **custom editor script** for the render feature to make configuring LayerFX settings easy
and manageable.
- **Demo Content** including:
    - A preconfigured 2D Renderer set up with LayerFX.
    - 7 sample shaders, set up for easy use with LayerFX, including both an HLSL
    shader and Shader Graphs.
    - Preconfigured materials for each included shader.
    - A demo scene allowing the user to cycle between effects for demonstration
    purposes.
    - 3 simple sprites used in the demo scene.
    - 2 scripts used for demo scene functionality.

All demo content is optional and can be safely removed from your project.

# Folder Structure

```
Assets
└── LayerFX
    ├── Editor
    │   └── Scripts
    │       └── LayerFXInspector.cs
    │
    ├── Runtime
    │   └── Scripts
    │       └── LayerFXRenderFeature.cs
    │
    ├── Samples
    │   ├── Materials
    │   ├── Scenes
    │   ├── Scripts
    │   ├── Settings
    │   ├── Shaders
    │   └── Sprites
    │
    ├── Documentation
    │
    └── README.txt
```

# Directory Overview

## Runtime

Contains the LayerFX Render Feature and all 
runtime code required for LayerFX to function.

✅ **Required**

## Editor

Contains editor scripts necessary for functionality such as inspector warnings, 
inspector organization, and easy material stack reordering.

✅ **Required**

## Samples

Contains sample content such as the demo scene, preconfigured materials, and more.

❌ **Not required and can be deleted**

Contents include:

- **Materials** – Preconfigured materials demonstrating the included effects.
- **Scenes** – Demo scene showcasing all included effects.
- **Scripts** – Scripts used exclusively by the demo scene.
- **Settings** – Example 2D Renderer configured with LayerFX.
- **Shaders** – Example Shader Graphs and HLSL shaders.
- **Sprites** – Sprites used by the demo scene.

Once you have finished exploring the sample content, the entire 
**Assets/LayerFX/Samples** folder can be safely deleted. 
None of the files in this folder are required for LayerFX to function.

## Documentation

Contains full offline markdown documentation.

## README.txt

Contains links to online documentation.

## File Organization

All LayerFX files can be moved to different locations within the Assets 
folder without affecting functionality, provided the 
**Runtime** and **Editor** folders remain intact.