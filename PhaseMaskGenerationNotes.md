# Notes, 18Jul2026

Modifications on Jupyter notebook:

1. Merged first section into a single one called "Standard Library Imports. SLM and CAMERA Loading". Note that when SLM is part of the main experiments this script should run without the diagnostics camera. Leaving the camera loading for now.

2. By default the source property in the slm object does not exist.
Currently, in the 'SpotsFF_PhasesAndIntensities_v2' function I use the argument AMPslm = cp.array(fs_setup.slm.source["amplitude"]) to define the padded SLM phase mask

   zeroMatGPS[rDimOff:-rDimOff,rDimOff:-rDimOff] =\
        cp.multiply(AMPslm, cp.exp(1j*PHIslm)) # Padded matrix with SLM phase.
   
I will remove the reference to AMPslm when '"amplitude" in fs_setup.slm.source' is False. This requires following changes:

rDimOff = int((slmPDim - slm.shape[0])/2)    # index offset for padded arrays.
