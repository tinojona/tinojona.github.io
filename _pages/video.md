---
layout: archive
title: "Videos"
permalink: /video/
author_profile: true
---

Relative vorticity on the sphere simulated with SpeedyWeather.jl using spherical harmonics. T682, 2048x1024 grid points (~20km horizontal resolution).
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/ortho_europe.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Kelvin-wave induced equatorial current that gets unstable. 3200x800 grid points at a resolution of 2.5km. Tracer is only injected on the western boundary.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/kelvin_instability.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Comparing 16 to 64-bit float arithmetic in ShallowWaters.jl at 3000x1500 grid points on Fujitsu's A64FX microprocessor.
The 16-bit model was scaled to minimize under and overflows and a compensated time integration to reduce rounding errors.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/a64fx_float16.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Solid particle advection from IndividualDisplacements.jl compared to the tracer advection of ShallowWaters.jl.
<img src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/test.gif" width="700px">

---

An MPI-parallelized non-linear 1D shallow water model.
<img src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/wave.gif" width="700px">

---

Using 16-bit posit arithmetic to simulate turbulence in a channel simulation at 10km resolution. The entire model is run with 16-bit posit arithmetic.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/tracer_posit_hr_single.mp4" controls="controls" style="max-width: 700px;">
</video>

---

A linear equatorial adjustment on β-plane with sudden westerly wind. The Rossby wave front propagates changes in wind forcing across the
basin and leaves the adjusted balanced state behind. 
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/rossby.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Turbulence topography in a channel simulation. Sea surface height is indicated with colour, zonal velocity with brightness (hill-shading).
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/turbtopo_hr.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Brownian motion-based particle mixing with gravity.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/brown_mixing.mp4" controls="controls" style="max-width: 700px;">
</video>

---

Brownian motion with a seed particle that freezes particle such that a ice crystal-like formation grows.
<video src="https://raw.githubusercontent.com/milankl/milankl.github.io/main/files/brown_fractal.mp4" controls="controls" style="max-width: 700px;">
</video>
