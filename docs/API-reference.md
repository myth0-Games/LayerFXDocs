# API Reference

The following page contains detailed information about the different settings and
fields available for configuring the render feature.

## Render Mode

- **Hidden Camera** (recommended): 

Automatically configures a lightweight internal camera to
render your selected layers. The internal camera will sync to the first correctly
tagged camera (see the **Camera Tag** field). 

This mode fully supports URP lighting, shadows, and post processing.

This mode fully captures selected layers regardless of whether any scene cameras
are already rendering the selected layers. To render specific objects with special
effects, it is recommended to disable these layers from any other scene cameras so
they do not render multiple times (e.g. Both from the scene camera **and** the 
LayerFX render feature).

This mode can be used for most rendering setups, and is the recommended mode for
most use cases.

- **Renderer List** (advanced): 

This mode functions nearly identically to the **Hidden Camera** mode, in that it
renders the selected layers. The key difference is that
it is slightly more performant, but does **not** support URP lighting, shadows and
post processing.

Use this mode when you want to render a layer or multiple layers with one or more
materials but do **not** care about rendering lighting effects on these layers.

**Key Limitations**: This mode requires the selected layers to be rendered from
an existing camera for the render feature to correctly capture them. Because objects must still 
be rendered by another camera, they cannot be completely isolated from 
the main scene. In most cases the additional rendering cost is small 
and is offset by the improved efficiency of Renderer Lists.

- **From External Texture** (advanced):

This mode is recommended for advanced use cases, such as isolating built-in URP
effects to specific layers. 

Unlike the workflow of the other two modes, this mode
does not give you the option to select specific layers to render. Instead, you
must input a valid Render Texture. The Render Feature will then render the selected
texture to the screen using the selected materials.

Performance on this mode can vary, depending on the selected texture's resolution.
Rendering an additional scene camera to a Render Texture will also add a 
performance cost.

## Pass Name

The selected name is given to the Render Graph passes
and can be used to identify a specific pass while debugging.

## Renderer Index

The Renderer Index determines which renderer to render the effect with. 
Your project's list of renderers can be found in the project's URP asset. 

## Rendering Order

Rendering Order determines where in the pipeline the effect will render. This can
be used to render the effect on top of or below other objects. 

For most 2D projects, set the field to BeforeRenderingOpaques to render beneath
other sprites. Set the field to AfterRenderingTransparents to render on top of
other sprites.

## Render Texture

If using the **From External Texture** rendering mode, this is the texture that
will be rendered to the screen using the selected materials.

## Materials

The Materials list determines what materials the feature will render with. As many
materials as desired can be selected, but each material will cost 
additional performance. 

Materials are applied sequentially. 
The output of one material pass becomes the input to the next.

Any valid material will be accepted. Invalid materials may cause issues, or not
render at all. 

To see the requirements for a valid material, visit the [Custom Shaders and
Materials](https://myth0-games.github.io/LayerMaskRendererDocs/custom-shaders-and-materials/)
documentation.

## Capture Layers

These are the layers that will be rendered by the render feature. If rendering objects using 
lit shaders, ensure a layer with a global light or other lighting is selected.
Otherwise, the layers may render completely black. 

## Downscaling

Increasing this value will cause the feature to be more performant at the cost of
visual quality. 

For many effects, a downscaling value of 2-4 will have little visual
impact but will massively improve performance.

Higher downscaling values will most likely have a negative visual effect, but can be
used to make pixelated effects. 

## Render in Scene View

This value determines whether or not the render feature will render in Scene View.

When using the **Hidden Camera** rendering mode, it is recommended to disable the
selected layers from the Scene View culling mask to prevent double-rendering in
Scene View.

When using the **Renderer List** rendering mode, the selected layers **must** be 
included in the Scene View culling mask due to Renderer List limitations.

When using the **From External Texture** rendering mode, the effect may not render
correctly in Scene View due to texture sizing. It is recommended to disable this 
setting when using the **From External Texture** mode.

## Color Buffer Format

Select HDR or LDR color formats.

If LDR is selected, the effect will render with **R8G8B8A8_SRGB**.

If HDR is selected, the effect will render with **R16G16B16A16_SFloat**.

## Filter Mode

Determines whether the effect will render with Point, Bilinear, or Trilinear
filtering.

## Camera Tag

When using the **Hidden Camera** rendering mode, the internal camera will sync
itself to the first camera to render with this tag. 

Match this field to the tag on the desired camera for the effect to render
correctly.