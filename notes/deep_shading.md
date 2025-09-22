# Deep Shading: Convolutional Neural Networks for Screen-Space Shading

Published on 3 Aug 2016. Accessible at https://arxiv.org/abs/1603.06078.

## Purpose

The authors aimed to simulate screen-space shaders using neural networks.
Screen-space shaders take as input per-pixel attributes, including positions,
normals, and reflectance and output RGB values for each pixel. The authors
wanted to create neural networks that can simulate effects such as
ambient occlusion, anti-aliasing, sub-surface scattering, motion blur,
and more.

## Technical Details

The authors used convolutional neural networks to learn each of their desired
shaders. Their training data consisted of 61,000 pairs of:

- deffered shading buffers: computing using OpenGL rasterization and
  containing per-pixel geometry, material and lighting information.
- corresponding shaded reference images: what the image specified
  by the deffered shading buffer should look like after shading.

Their convolutional neural network had up to 12 steps, where each
step consists of a convolution and activation function. Their
typical networks consisted of about 130,000 learnable parameters.

Their neural networks take as input the deferred shading buffer and
output the RGB value for each pixel in the shaded image.

## Findings

The authors found that their neural networks produced accurate
models for screen-space shaders. They also produced arbitrary
combinations of them at acceptable quality and speed. Some
of their images had artifacts, but the authors say they
are much more pleasant than those resulting from human
made shaders.

## Limitations and Next Steps

The main limitation is inherent to screen-space shading
techniques, which is missing information from objects not
contained in the image due to occlusion, clipping, or
culling. The author hopes that in future refinements,
their networks can fill this missing information in.
Furthermore, they want future work to work with a
different screen representation, such as surfels, patches,
or directly in the domain of light paths.

## Relevance to the SWAMP

This paper shows how neural networks can be used to learn
shading information. It also shows the type of training
data and how much of it we may need. The use of convolutional
neural networks should be considered in SWAMP given its
success in this paper.
