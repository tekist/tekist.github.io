---
layout: post
title:  "2D Lighting Engine"
image: /assets/images/lights.jpg
---

<figure><img src="{{ page.image | relative_url }}"><figcaption>Screenshot of <em>Ultra Lights 2D</em></figcaption></figure>

### Overview 

This is a 2D fully dynamic real-time lighting engine I built that's capable of rendering shadows with penumbra and antumbra. Colors are mixed together in high dynamic range, and the results are tone mapped via an [ACES filmic tonemapping curve](https://knarkowicz.wordpress.com/2016/01/06/aces-filmic-tone-mapping-curve/). The result is a colorful and suprisingly accurate light and shadow renderer. The best part is that it's *very* fast. The scene above runs at thousands of frames per second on my machine, and it's targeted to support typical consumer-grade laptops.

### Details

The shadow system is based off of [Slembcke's lighting system](https://slembcke.github.io/SuperFastSoftShadows). I reverse-engineered his WebGL implementation for use in Game Maker: Studio 2, which is my preferred game engine. Most of this could theoretically be ported back into WebGL. I fixed an issue his version has with shadow geometry clipping, added [blue noise dithering](https://momentsingraphics.de/BlueNoise.html) for smoother gradients, and HDR colors and tone mapping. All of this took well over a year of development (2022-2023), and I'd like to refine it even further for potential commercial use.