====================================================================
Extending HyVR
====================================================================

The HyVR package is a work in progress. It has been implemented in Python in order to make it accessible for researchers, easily customisable, and hopefully somewhat easy to extend to suit the needs of future research. In this section I have included some tips on ways to extend the HyVR source code.


------------------------------------------------------------------------
Adding more geometries
------------------------------------------------------------------------

HyVR has been set up in such a way to facilitate the implementation of additional hydrofacies assemblage geometries. 

In order to generate new types of geometries a new function needs to be written in the ``hyvr`` module that will be called from ``hyvr.run()`` where individual architectural elements and hydrofacies are simulated (around line 288 of ``hyvr.run()`` - search for ``ADD NEW GEOMETRIES HERE``). 

Any new geometry function needs to return a ``count`` integer value (for keeping track of individual hydrofacies assemblage identifiers) and a ``props`` dictionary containing the following properties:

* ``ha_array`` (numpy array) -  hydrofacies assemblages
* ``hat_array`` (numpy array) - types of hydrofacies assemblage 
* ``azim`` (numpy array) - azimuth
* ``dip`` (numpy array) - dip 
* ``fac`` (numpy array) - hydrofacies

When adding geometries, we suggest reviewing the code for the existing geometries to see how it is currently implemented. This should provide a reasonable idea of how to put a new geometry together.

------------------------------------------------------------------------
The HyVR wish list
------------------------------------------------------------------------

Any modelling project will have 'areas for growth' (as opposed to weaknesses). I have identified some things that I would like HyVR to have, but that are outside of the scope of my PhD research (and funds...). Perhaps you have the time and need to complete these yourself?

* Extensions in ``C`` or ``Cython`` to speed up bottlenecks in simulations, particularly in ``hyvr.planepoint``.
* Some level of conditioning, or improved interfacing with multiple-point geostatistical packages.
* Interaction of extruded parabolas, as well as more complex/realisitic configurations of channel deposits (e.g. point bars).
* Utilities for deriving HyVR simulation parameters from transitional probability geostatistics.
* Simulation of chemofacies.
