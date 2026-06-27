# **Quick Start Guide**

Setting up a custom render pass is simple. Follow these steps to get started!

# 1. Scene Setup

We'll start off with a simple scene in the editor. The player sprite is very dark against the background, so in this guide, we'll set up a blur pass on the background to make the player pop.

![DemoScene](images/demo_scene.png)

This scene contains the default Unity Main Camera, as well as a Global Light 2D. There is also the player game object, some walls and platforms, and the background sprites.

- Firstly, we should switch the background sprites to a separate Layer Mask. Select the parent game object, click on the layer dropdown, and change it to the desired layer mask. 
Here, we added a layer called 'Background'. 

![ChangeLayerMask](images/change_layer_mask.png)

The editor will prompt you to ask if you also want to change child layer masks. We **do** want all children to also be on the blurred background layer, so click 'Yes, change children.'

- Also change your GlobalLight2D to a separate layer, so we can capture it in the render pass. Here, we made another new layer called 'Lighting'. 

- You will also want to deselect your desired layers from the Main Camera's culling mask. This prevents the desired layers from rendering twice (both on the Main Camera and from the Render Feature). 

- Here, we deselected the 'Background' mask, but kept the 'Lighting' mask enabled because we want the lights to affect both the blurred layers and the main layers.

![CullingMask](images/culling_mask.png)

# 2. Renderer2D Setup

Now we need to configure the render feature on the renderer. 

## Locating the Renderer2D asset

Find your project's Renderer2D asset. It is usually found at 'Assets/Settings/Renderer2D'.

If you can't find it, first find your Universal Render Pipeline asset. This can be found by going to Edit > Project Settings > Quality > Render Pipeline Asset.
Once you have located your Universal asset, you can find your 2D Renderer in the Renderer list at the top of the Inspector window.


## Adding the Render Feature

Scroll to the bottom of the Inspector window of your Renderer2D asset, and click 'Add Render Feature'.

![AddRenderFeature](images/add_render_feature.png)

Select **'Layer FX Render Feature'.**

![AddLayerFXRenderFeature](images/add_layerfx_render_feature.png)

## Configuring the Render Feature

Now we must configure the settings of the render feature.

- **Pass Name:** Set to whatever you want. This internally names the render pass for debugging purposes. Here we'll name it 'BackgroundBlurPass'.
- **Renderer Index:** This selects what 2D renderer the render feature should render to. To prevent recursive rendering issues, set this number to a **different** index than the renderer that the render feature is attached to.
Here we will set it to 1, as 2D renderer we are using is at index 0.
- **Rendering Order:** This determines at what point during the rendering process the feature will render at. Select **BeforeRenderingOpaques** to render behind the main scene layers, or
**AfterRenderTransparents** to render on top of the main scene. As we are trying to blur the background, we will set it to **BeforeRenderingOpaques**.
- **Tex:** Here, you can select a texture to render from as an alternative to rendering from a Layer Mask. This is useful for rendering layers with post processing effects. Leave this field
blank to render from the selected layers. In this tutorial, we will leave it blank as we want to render from the Background Layer Mask.
- **Materials:** Select 1 or more materials to render the desired layers with. Selecting more than one materials will stack the materials in the listed order.
This allows for fancy effects that combine other effects, or multi-pass effects. In this tutorial, we are creating a 2-pass blur to save performance.
We will add two blur materials, one that blurs horizontally and one that blurs vertically.
- **Capture Layers:** This is where we select the layers that the effect should be applied to. Here we will select the 'Background' and 'Lighting' layers.
Not selecting the lighting layers will cause it to render only black if you have selected a Sprite-Lit material!
- **Downscaling:** Downscales the texture to save performance. In this guide, we will select 2x, because there will be minimal visual impact due to blurring the layers.
- **Render In Scene View**: Enable this to render the effect in scene view.
- **Hidden Layers:** If Render In Scene View is enabled, this determines what layers will **not** render in scene view.

These are the final configured settings:

![FinalSettings](images/final_settings.png)

Now hit Play and watch the effect! Our blur effect turned out really well, and now the player is much more visible against the noisy background. 

![BlurEffect](images/blur_effect.png)
