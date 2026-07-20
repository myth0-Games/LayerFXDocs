# **Performance**

Extensive performance testing has been conducted on the asset using integrated graphics to 
evaluate performance on lower-end hardware.
Tests were done with shadows turned off in the render feature settings.

As the data below indicates, when rendering a large amount of sprites, the render feature may render large numbers of sprites more efficiently than the main camera due to its simplified rendering settings.
Frame times may vary depending on the complexity of the selected material.

| Number of sprites on screen | Median frame time with sprites rendering from main scene camera (ms) | Median frame time with sprites rendering through the render feature using a simple material (ms) |
| --- | --- | --- |
| 100 | 2.089	| 2.174	|
| 200 | 2.474	| 2.554	|
| 500 | 3.19 | 2.671 |
| 1000 | 5.333 | 4.179 |
| 2000 | 9.498 | 5.742 |

Tests were conducted with the following specs.

 - **GPU:** Ryzen 7 5800H integrated graphics
 - **Resolution:** 1080p
 - **Unity Version:** Unity 6000.3.11f1
 - **Platform:** Windows 11

Your exact numbers may vary on different hardware, resolution, versions, or platforms.

## Boosting Performance

- **The #1 way to boost the performance of the render feature is by enabling Downscaling.** 
To change the Downscaling value, go to the render feature's settings and edit the Downscaling
field. For large performance gains with minimal visual change, set Downscaling to 2x. 
Values larger than 2x may reduce visual quality, but can provide significant additional 
performance improvements.

![Downscaling Slider](images/downscaling_slider.png)



- The selected material will also greatly impact performance. Optimize more intensive materials to ensure good performance. Less intensive materials will have negligible performance impact.
- Limit the number of instances of the render feature. Multiple instances **are** supported, however they will reduce performance.