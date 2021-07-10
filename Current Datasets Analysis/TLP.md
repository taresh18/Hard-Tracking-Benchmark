# TLP

# Sequences from TLP

1. **Jet1**: Scale var, Appearance var (shape), Clutter, smoke
         but length of video is unnecessarily too long 
2. **Jet2**: Scale var, Appearance var (shape), OPR, aspect ratio change, clouds
         but length of video is unnecessarily too long 
3. **Jet 5**: Fast motion, Scale var, Appearance var (shape, smoke), aspect ratio change
          but length of video is unnecessarily too long 
4. **Sam**: illum. var (intensity, multi color), OPR, scale var, partial occlusion
         only the last 50-60 sec. comes under appearance variation
5. **Violonist**: Illum. var (intensity, multi color, uneven) 

                        Nice case of illumination variation.

# Evalutaion metrics:

1. Precision plots
2. Succes rate (AUC + conventional # frames with IOU > 0.5)
3. LSM: Ratio of longest continuously tracked subsequence to total length of the sequence. 

              Useful for cases where a tracker loses the target but coincidently starts tracking it again if target passes through the same location, LSM penalizes such cases by taking only the longest continuous tracked subsequence.

# Dataset analysis:

- even if there is no apparent major challenge or target disappearance, tracking consistently for a long period of time is an extremely challenging task.
- Long sequences are harder to track because of drift which becomes more significant in longer videos as the error gets accumulating over time.
- If not accounting for length, the sequences are relatively easy.
- In cases of full occlusion/out of view, the target reappears from the same location (thus not really a hard case of full occlusion/out of view).
- No sequence with Transparent object, complex object shape, articulation etc.
- No sequence with rain, fog. Only some Jet videos have a little smoke.
- Very few cases of appearance variation are covered.
- length of sequences are unnecessarily too long
- No separate attribute for out of view (only FOC)
- since high frame video reduces appearance variation per frame, it is possible to achieve state of the art performance using substantially simpler tracking algorithms.
- variation in bounding box size and aspect ratio with respect to the initial frame is significantly larger in TLP and the variations are also well balanced.
- Out of view appears to be the most difficult challenge hindering the performance of the trackers followed by background clutter, scale variation and partial occlusions. Most of the trackers seem to perform relatively better on sequences with illumination variation and fast motion
