# An Improved Illumination Model for Shaded Display

Published in 1980, Accessible at https://www.cs.drexel.edu/~deb39/Classes/CS586/Papers/p343-whitted.pdf

## Purpose

The purpose of the paper is to present different ray tracing algorithms which are used in order to display a 3D scene on a 2D image.

## Technical Details

In general for ray tracing, each pixel of the 2D display is mapped to a ray extending from the viewer to the surface. Which then splits into a tree for reflection, refraction, shadows, etc. A shader traverses this tree to determine the intensity of light received by the user.

A simple shader can calculate the intensity of light as the dot product between the normal of the surface (that intersects with our ray) and the the light source direction of the scene. This does not consider any reflection or shadow.

An improved shader will consider reflection and transmission (light coming through a transparent object) when calculating the light received by the viewer's ray. Then the intensity of light received from the viewer is a function of the light intensity coming from 2 other directions. This can branch up until a max depth limit is reached.

The paper then goes on to explain how their improved shader accounts for anti aliasing and some ways to optimize computation that are not very relevant to us.

## Findings

The authors were able to apply their formula to render reflective surfaces.

## Limitations and Next Steps

The authors mention that their formula "does not provide for diffuse reflection from distributed light sources, nor does it gracefully handle specular reflections from less glossy surfaces". In addition ray tracing is slow.

## Relevance to the SWAMP

HOW IS THIS PAPER RELEVANT TO SWAMP'S RESEARCH, IF AT ALL? WHAT ARE THE
KEY POINTS FOR US TO UNDERSTAND/KNOW?

This paper explains the theory behind ray tracing and how the shader interacts with the rays. In general, a ray is emitted from the viewer which when intersecting with a surface, can be represented as a function of the light coming from various other directions and the material properties of the surface. This generates a tree which will stop branching when it does not intersect with an object, or if a max depth limit is reached.
