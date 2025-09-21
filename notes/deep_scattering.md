# Deep Scattering: Rendering Atmospheric Clouds with Radiance-Predicting Neural Networks
Published on 2017-09-15. Accessible at http://arxiv.org/abs/1709.05418.

## Purpose

Clouds have multiple light scatters. Monte Carlo integration is used for a single scatter. Multiple scatters can be predicted with a neural network. The RTE (Radiative Transfer Equation, accounting for how light scatters inside a medium) is expensive for Monte Carlo because there are many scatterings per photon path inside a cloud. The authors sought to reduce this rendering time significantly while maintaining accurate renderings.

## Technical Details

So instead, the authors fed the neural network JUST the indirect in-scattering radiance (multi-scattering) for approximation and keep the direct single in-scattering as a MC integral.

This indirect in-scattering radiance depends on local density of the point, cloud structure, and light source relative to the viewer.

To do this, they made a hierarchical 3D stencil to sample density: a 5x5x9 grid in the light direction, x2 volume each level, 10 levels. Scaled to find the mean free path, and sent one level at a time to training model.

## Findings

Rendering with RPNNs was up to 1000× faster than volumetric path tracing under directional illumination.
Outperformed flux-limited diffusion (FLD) by 1–2 orders of magnitude lower bias.

## Limitations and Next Steps

Neural networks trained only on clouds and performed poorly on non-cloud shapes (overestimates subsurface brightness in such cases).
Underestimates contrast for backlit stratus clouds. 
Under complex environment maps, residual noise persists because Monte Carlo is still used for sampling single scattering and directions.
Hierarchical stencil is compact but can’t capture distant hard shadows.

Expand environment maps into spherical harmonics (or other bases) and feed coefficients into the network, instead of MC sampling directions.
Apply post-process denoisers to clean up noise from Monte Carlo single scattering sampling.
Networks could be retrained or fine-tuned for specific cloud types, scenes, or lighting (~12 hours).
Explore progressive networks (Rusu et al., 2016) to make retraining more efficient and allow reusing knowledge from previous training.
Investigate larger or alternative descriptors (e.g., CNNs with bigger inputs) to better capture long-range effects.

## Relevance to the SWAMP

This paper is relevant to SWAMP because it shows how neural networks has been trained to mimic scattering, which is something that the SWAMP RATS should look into for creating their neural network for atmosphere shading. In particular, the 3D stencil is a novel format to consider. This paper also highlights possible extensions for the SWAMP RATS to look into.

