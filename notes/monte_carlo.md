# Monte Carlo Path Tracing from Stanford Graphics Lecture Notes

Accessible at https://graphics.stanford.edu/courses/cs348b-01/course29.hanrahan.pdf. Accompanying slides: https://graphics.stanford.edu/courses/cs348b-10/lectures/path/path.pdf

## Purpose

The lecture notes introduces the theory behind Monte Carlo Path tracing. Much of the material is synthesized from the following paper: https://www.cse.chalmers.se/edu/year/2011/course/TDA361/2007/rend_eq.pdf

## Technical Details

The notes begin by presenting the reflection equation which states that the incoming radiance received along a ray from reflection can be calculated by integrating the incoming radiance over a hemisphere around the point where the ray intersects the object. In general the light intensity received along a ray is a function of the integral of light intensities coming from other directions. As the light bounces, we are left with a high dimensional integral which Monte Carlo Path Tracing aims to solve. The algorithm is as follows. From the camera, extend a ray, and when it intersects with a surface, randomly decide whether to add the the light emitted from the surface or choose a new ray (which goes through the hemisphere) which we will calculate the reflectance from. Notice that the amount of computation will not be infinite since there is a chance that a path will end when it intersects a surface. Each pixel of our final image is calculated by taking multiple rays from the camera. The paper then goes on to justify that creation of the path by sending rays from the camera is the same as sending rays from the light sources (which is the what happens in the real world).

## Relevance to the SWAMP

This paper provides knowledge on Monte Carlo Path Tracing which is common for ray tracing algorithms. The key points are that in Monte Carlo ray tracing, the RGB output of a pixel is dependent on multiple samples of the corresponding ray. The path generated from each ray will be of variable length and are non deterministic. When we implement our neural network shader, we will still need to calculate the path generated from a ray. Then starting at the leaf node, we will apply the neural network to the inputs and work our way up the path.
