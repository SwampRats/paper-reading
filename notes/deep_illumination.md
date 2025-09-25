# Deep Illumination: Approximating Dynamic Global Illumination with Generative Adversarial Network

Published on 22 May 2018. Accessible at https://arxiv.org/abs/1710.09834.

## Purpose

The authors present a novel application of generative adversarial
networks (GANs) to efficiently compute global illumination elements (GI) such
as indirect illuminations and soft shadows
in 3D scenes using a deep learning approach. The inputs to the network
would be the G-buffers (color, normal, depth, position) of surfaces visible
to the camera, along with direct lighting information, and the output would be
colored pixels corresponding to the scene as seen from the camera with global
illumination applied. The goal of this approach is to produce effective GI
at a faster speed/runtime than current GI techqniques.

## Technical Details

The technique outlined by the authors employes a variant of GANs called
conditional generative adversarial networks (cGANs).
GANs are a type of neural network that consist of a generator and discriminator
network.

The
The generator network is trained with G-buffer and direct lighting information
captured from a scene as input, and the corresponding images of the scene with
GI applied using a computed GI technique as a ground truth/target.
The generator attempts to use the input data to generate images similar to the
target image, while the discriminator network is fed either images created by
the generator, OR actual target images from the dataset, and attempts to
identify which images are "real" and which are generated.

The final goal of the training is to have the generator able to generate images
that cannot be identified by the discriminator.

## Findings

The authors found that their approach was able to generate GI of comparable
quality to their ground truth images at a faster speed than traditional GI
methods. They also found that increasing the size of the training dataset
improved the quality of the results. While the majority of results were not
distinguishable from the ground truths in the eyes of the authors, there were
small errors discovered in some scenarios, such as when rendering partile
systems, or introducing new objects in the scene .

Notably they discovered that the GI technique used to train the network
played a role in the quality of the generated images, and the convergence
speed of the network.

## Limitations and Next Steps

One limitation of the approach is that it is trained on a per-scene basis, where
training data is collected different positions and orientations of the camera,
light sources, and scene objects. They outline some advantages to this
approach, in that it allows the network to better learn the stylization/
distinct features of the scene

The paper only discussed applications of indirect illumination and soft shadows
on diffuse materials. The authors would be interested to see how the approach
could be extended to other types of materials and GI effects.

## Relevance to the SWAMP

The approach discussed by the authors shows an example of another
neural network variant, cGANs, that may be relevant/applicable to our
project.

Their approach also uses a "one network for one scene" approach that
may be beneficial for our applications as well.

Finally, the authors' approach to gathering and training their model,
along with their fine-tuning of hyperparameters may be useful to work off
of for our training.
