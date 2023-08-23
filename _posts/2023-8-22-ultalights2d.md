---
layout: post
title:  "2D Lighting Engine"
image: /assets/images/lights.jpg
---

![]({{ page.image | relative_url }})

This is a 2D fully dynamic real-time lighting engine I built that's capable of rendering shadows with penumbras. Colors are mixed together in high-dynamic range, and the results are tone-mapped via an ACES filmic tonemapping curve. The result is a colorful and suprisingly accurate light and shadow renderer. The best part is that it's *very* fast. The scene above runs at thousands of frames per second on my machine, and it's targeted to support typical consumer-grade laptops.

The shadow system is based off of [Slembcke's lighting system](https://slembcke.github.io/SuperFastSoftShadows). I reverse-engineered his WebGL implementation for use in Game Maker: Studio 2, which is my preferred game engine. I fixed an issue his version has with shadow geometry clipping, added [blue noise dithering](https://momentsingraphics.de/BlueNoise.html) for smoother gradients, and HDR tone-mapping. All of this took well over a year of development (2022-2023), and I'd like to refine it even further for potential commercial use.