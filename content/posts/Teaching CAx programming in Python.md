---
title: Teaching CAx programming in Python
date: 2026-07-01
tags:
  - CAD
categories:
  - Teaching
BookPostThumbnail: rotor-blade-thumb.png
---
*This first appeared as a [LinkedIn post](https://www.linkedin.com/feed/update/urn:li:share:7478044494572216320/) on 1 July 2026.*

The first semester of my newly designed course on parametric CAx programming in Python has wrapped up.

In this course, computational and mechanical engineering students learn the topological and geometrical foundations of CAD and apply them using modern open-source libraries to generate designs entirely through code. And because CAx goes beyond CAD, we also explored the full design-to-simulation pipeline, including mesh generation and simple FEM examples, all with open-source tools.

**The final project**

As a final project demonstrating this end-to-end workflow, the students built a fully parametric wind turbine rotor blade: they generate the aerodynamic outer shape from airfoil profiles, create the internal structure, generate the mesh, and run a static FEM simulation under a simplified load. The animation at the end of this post shows the blade bending under load – scaled from 0 to ±1 for visual effect, colored by von Mises stress.

**Standing on open source**

None of this would be possible without the open-source libraries we built upon: [OCCT](https://dev.opencascade.org/), [CadQuery](https://github.com/CadQuery/cadquery), [build123d](https://github.com/gumyr/build123d), [OCP CAD Viewer](https://github.com/bernhard-42/vscode-ocp-cad-viewer), [PyVista](https://pyvista.org/), [Gmsh](https://gmsh.info/), and [scikit-fem](https://github.com/kinnala/scikit-fem), to name only the most important ones. Many thanks to the maintainers and communities behind these amazing tools!

**What came out of it**

Building this course required quite a bit of learning on my part, too. It was far from perfect, but the first run showed me where to refine it for the next one. Over the summer break, I also turned the teaching materials into an open-source book, [CAD as Code](/docs/cad-as-code/), which will be published through our university library. Hopefully it can be a useful resource for others trying to bridge the gap between software and mechanical engineering.

The slides and code examples for the course are [openly available](https://davidstraub.de/teaching-materials/cax-programmierung/).

<figure>
<img src="/posts/rotor-blade.gif" alt="Parametric wind turbine rotor blade bending under load, colored by von Mises stress">
<figcaption>The parametric rotor blade from the final project, bending under a static load and colored by von Mises stress. The deflection is scaled up to make it visible, and the load is a rough stand-in for aerodynamic forces, with no CFD behind it. The example is sized to fit into one lesson and demonstrate the complete workflow; the results are not meant to be realistic.</figcaption>
</figure>
