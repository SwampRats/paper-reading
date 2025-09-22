# A Learned Shape-Adaptive Subsurface Scattering Model

Published in July 2019. Accessible at https://rgl.epfl.ch/publications/Vicini2019Learned.

## Purpose

This paper introduces a novel method of rendering subsurface scattering. Existing methods of subsurface scattering rendering are either computationally expensive (e.g. brute-forcing paths of many photons through the interior of an object) or rely on assumptions (such as planar surface geometry) that aren't true for most rendering situations.

## Technical Details

This paper introduces a learned BSSRDF model (the BSSRDF describes a distribution for how a photon might exit an object after internal scattering given how it enters). It applies ML to learn how to sample from the distribution of exit points for a given photon entering an object (instead of using brute-force path tracing). The model's imput includes local geometry (encoded by a polynomial) of the point of entry of a photon, as well as material properties. It passes the input through a feature network (which preprocesses the input). It then puts the preprocessed input through a scatter network, which outputs an outgoing location for the photon, as well as an absorption network, which calculates the probability of the photon being absorbed. The scatter network is based on an variational autoencoder. The model was exported as a plugin in the Mitsuba renderer, and the trained neural networks were manually implemented in C++.

## Findings

The model introduced in this paper performs better (produces less error) in the same amount of rendering time when rendering a scene with objects of varying geometry compared to other methods such as path tracing or other BSSRDF models. It also experiences less degradation when the material being rendered becomes less dense.

## Limitations and Next Steps

Future work includes implementing this method with improved shape descriptors (currently, they use polynomials to describe the geometry in a neighbourhood of a photon's entry point, which can be inaccurate), as well as performance optimizations.

## Relevance to the SWAMP

This paper describes training a neural network to learn how to sample from a distribution of possible outputs for a given input, which might be applicable to rendering scenarios we might encounter in our project (maybe not). The authors were also able to performantly implement a trained neural network by hand, which SWAMP will probably need to look into in the future.
