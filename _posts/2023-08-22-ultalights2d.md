---
layout: post
title:  "2D Lighting Engine"
image: /assets/images/lights.webp
altText: Screenshot of Ultra Lights 2D
image0: /assets/images/lights1.webp
image1: /assets/images/lightmesh.webp
image2: /assets/images/dithering.webp
image3: /assets/images/lights2.webp
image4: /assets/images/lights3.webp
image5: /assets/images/lights4.webp
---

<figure><img src="{{ page.image0 | relative_url }}" alt="Screenshot of Ultra Lights 2D"><figcaption>Screenshot of <em>Ultra Lights 2D</em></figcaption></figure>

## Overview 

This is a 2D fully dynamic real-time lighting engine I built that's capable of rendering shadows with penumbra and antumbra. Colors are mixed together in high dynamic range, and the results are tone mapped via an [ACES filmic tonemapping curve](https://knarkowicz.wordpress.com/2016/01/06/aces-filmic-tone-mapping-curve/). The result is a colorful and suprisingly accurate light and shadow renderer. The best part is that it's *very* fast. The scene above runs at thousands of frames per second on my machine, and it's targeted to support typical consumer-grade laptops. All of this took well over a year of development (2022-2023), and I'd like to refine it even further for potential commercial use.

## Details

The shadow system is based off of [Slembcke's lighting system](https://slembcke.github.io/SuperFastSoftShadows). I reverse-engineered his WebGL implementation for use in Game Maker: Studio 2, which is my preferred game engine. Most of this could theoretically be ported back into WebGL. I fixed an issue his version has with shadow geometry clipping, added [blue noise dithering](https://momentsingraphics.de/BlueNoise.html) for smoother gradients, and HDR colors and tone mapping.

<figure class="less-width"><img src="{{ page.image1 | relative_url }}" alt="Shadow geometry" loading="lazy"><figcaption>Shadow geometry</figcaption></figure>

To project shadows, an index of static geometry is pulled into memory. A vertex shader then projects new points from this, extruding them away from a light source out to infinity via homogenous coordinates. The image above was created with [RenderDoc,](https://renderdoc.org/) a program which allows for detailed graphics debugging.

<br/>

<figure class="less-width"><img src="{{ page.image2 | relative_url }}" alt="Infographic that demonstrates color banding and dithering" loading="lazy"><figcaption>This image exaggerates how dithering can resolve color banding</figcaption></figure>

One of the downsides of the shadow system is that they have to be drawn in 8-bit textures. This creates a percieved lack of detail dubbed "color banding". Thankfully, blue noise is a great solution to this issue. The image above shows the effect it can have on an obsolete version of the engine.

<br/>

## Gallery

<img src="{{ page.image3 | relative_url }}" alt="Screenshot of Ultra Lights 2D" loading="lazy">
<img src="{{ page.image4 | relative_url }}" alt="Screenshot of Ultra Lights 2D" loading="lazy">
<img src="{{ page.image5 | relative_url }}" alt="Screenshot of Ultra Lights 2D" loading="lazy">