---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

An list of projects that I worked on. Reach out if you want to collaborate!


Relative vorticity on the sphere simulated with SpeedyWeather.jl using spherical harmonics. T1023 on an octahedral Clenshaw-Curtis grid at about ~10km horizontal resolution.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/vorticity_clouds_T1023.mp4" controls="controls" style="max-width: 700px;">
</video>





## Differentiable atmospheric modelling: Learning from data between Earth’s and exoplanetary climates

_supervised together with [Tad Komacek](https://www.physics.ox.ac.uk/our-people/komacek) (Oxford)_

Atmospheric general circulation models are the backbone of climate models, being used to understand and predict climate change on Earth.
Founded in physical laws, general circulation models can be generalised to exoplanetary atmospheres. While many atmospheric processes on
Earth are well understood and accurately simulated as evident through the success of weather forecasting, some processes such as cloud
formation and precipitation are less certain. Societally-relevant surface climate and extreme events like heat waves, however, strongly
depend on those. At the same time, observations can constrain such uncertainties, improving climate predictions on Earth. On exoplanets
this will reveal insights about the parameter regimes in which planetary habitability is possible. How to make atmospheric models
automatically learn from observational data? 

This project will build on top of SpeedyWeather, an atmospheric general circulation model written in the Julia programming language.
SpeedyWeather is easy to use and extend, inspired by modern software engineering, covering functionality from data visualisation to
high-performance computing. The candidate will continue to develop its differentiability through the automatic differentiation
framework Enzyme. Differentiating through SpeedyWeather, we can optimise the unknown or less certain parameters determining the
planetary surface climate and resulting habitability in the same way as neural networks are trained towards observations.
And we can add neural networks to SpeedyWeather forming a hybrid physics and data-driven model. 

For exoplanets, observations of gas giants down to hot terrestrial planets are currently used to constrain their atmospheric composition
and thermal structure. Critically, upcoming space missions such as the Large Interferometer for Exoplanets and Habitable Worlds Observatory
will have the ability to measure the thermal emission and reflected light of Earth-like exoplanets, enabling a direct test of our Earth-based
understanding of planetary climate. This SpeedyWeather/Enzyme framework will enable novel rapid inverse characterization of exoplanetary
atmospheres with a 3D model that can be applied to exoplanet observations.

Part 2 of this project will scale up the same method to the Earth’s atmosphere, increasing data and complexity. For earth, the current surface
climate is observable, but a model may still mispredict frequencies and intensities of extreme events like heat waves under global warming.
But with automatic differentiation we can train the model to correct for the missing physics of heat waves towards a more reliable generalisation
into future climates, assessing the Earth’s habitability under global warming.

This PhD project will bridge several fields: The applicant is expected to have a strong background on the spectrum between physics,
mathematics, and computer science, with enthusiasm for computer science and machine learning. Prior experience with Julia is not
required, but experience with another programming language like Python, Matlab, C(++), or Fortran is preferred.

Posted here [https://www.physics.ox.ac.uk/study/postgraduates/dphil-atmospheric-oceanic-and-planetary-physics/climate-physics](https://www.physics.ox.ac.uk/study/postgraduates/dphil-atmospheric-oceanic-and-planetary-physics/climate-physics)

## Downscaling and bias correction with online machine learning

_this is a draft of a project description, to be updated with more details_

We know climate models aren’t right and instead of correcting them by hand one could also correct things automatically on the fly.
For example precipitation: Given a simulated precipitation field after a time step inside the model one could bias correct / downscale them
(via diffusion, consistency models, or maybe to start a simple quantile mapping) and feed that back into the model so that the model actually
feels that correction “ah okay I’m not supposed to rain here but here”. “Feels” means that the tendencies for temperature/humidity would be
adjusted corresponding to the output from the bias correction, so it doesn’t dry out where it’s not supposed to rain or the land surface model
actually receives additional soil water if a diffusion model says not medium but actually heavy precipitation. And the downscaled fields would
then be subject to output so while a model runs at a relatively low resolution, the downscaling turns, say a cheaper 100km model effectively
into a 10km simulation. Something similar could be done with surface winds / storms: While models struggle to simulate the correct intensity
of storms, ML downscaling could be very helpful here, taking a low resolution wind field and turning it into a bias corrected higher-resolution
version, which, inside the model would then affect e.g. surface fluxes, so that a storm that was now injected into the simulation with ML can
actually pull out more heat from the ocean. A lot of ML papers till now work on post-processing model outputs (=offline), but doing things
online means you get a better model without losing the meaningful components that general circulation models have.

## Machine learning in atmospheric models with generalization in space and time

_this is a draft of a project description, to be updated with more details_

If you were to take Graphcast and push the world outside of its climate distribution (think global warming) the models likely produce garbage
because in their latent space they have a hardcoded representation of, say, surface temperatures in the tropics being warmer than in mid-latitudes.
Meaning any experiment to investigate causes and consequences of global warming wouldn’t work with these models as ML architecture
would try to sample from the distribution it has seen during training. NeuralGCM addresses this problem by using a single-column ML correction that
therefore can learn, say, from the winter climate of Spain and apply it to the summer climate of the UK — because it does not actually know where
things are on the planet. Theoretically this allows for a generalisation of ML across space, diffusion/consistency models would struggle with that,
but no one has ever actually shown this, e.g. take NeuralGCM and Graphcast, flip the hemispheres, or rotate them, and see whether they
produce garbage or not. More generally this points to a shortcoming of the image-inspired ML approaches: Whereas we would like to use ML in a way that
in a climate model it adds some general truth, that generalisation is very questionable if it just has learned that region A has to be
warmer/rainer/stormier than region B.

NeuralGCM is a hybrid physics-ML atmospheric model that relies on sea surface temperatures as boundary conditions. Meaning that ramping up those
to represent global warming it will also warm the atmosphere. Great, but you technically include “forbidden” knowledge because with global warming
we actually do not know how the oceans will warm exactly. For that reason SpeedyWeather comes with simple representations of the physical processes
(clouds, precipitation, surface fluxes, …) that do give you a “knob” to actually simulate global warming by increasing CO2 in the radiation scheme —
NeuralGCM has learned all physics, so you can technically infer again that is has learned daytime heating, but there’s no way to disentangle the
different processes as they are all handled by the same neural network. This whole approach would be so that a model can be corrected with
machine learning without losing the physical model’s ability to generalise in time, meaning that you get a realistic future climate if you ramp up CO2.

## Learning the ocean for seasonal forecasts

_this is a draft of a project description, to be updated with more details_

For sub-seasonal to seasonal forecasts, having an active ocean is important because of the memory the ocean provides,
essentially integrating the atmospheric state over the past. Atmospheric heat waves can warm up the surface ocean
increasing surface latent and sensible heat fluxes at a later time. Or a storm can cool down the surface ocean 
due to the enhanced heat fluxes out of the ocean lowering the surface boundary conditions for the atmosphere
in weeks or even months to come. None of the current machine-learned weather prediction models have an active ocean,
and so it might be even a cool project to learn an active ocean based on ML, coupled to an atmospheric model like SpeedyWeather.
A slab ocean is easy to define, and as a starting point could be calibrated towards surface temperature observations.
The next step would be to see whether one could include a mean surface circulation of the ocean, for example defined through
transport matrices. Such a circulation could be taken from data, but also learned from observations of sea surface temperature.
While such an ocean circulation would still be passive (not responding to the atmosphere), temperature anomalies from the
slab ocean could still be moved around following some idealised circulation. Interesting here would be how much
one can idealise the surface ocean circulation for a good seasonal forecast. A next step could be to update the transport matrices
given past surface fluxes of heat and momentum. Alternatively, or in combination, such an approach could be compared
to coupling SpeedyWeather with Oceananigans, a fully dynamic ocean general circulation model.
