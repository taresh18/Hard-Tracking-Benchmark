# TrackingNet

# Sequences

1. **0043** : person diving into sea 
SV, app var (haze like condition due to blue water, shape changes in later frames)
2. **0119**: night scene of a street 
LR, illum var (intensity), night scene, POC 
GT bb should have been on bike instead of the person walking on street
3. **0137**: jet taking off 
SV, OPR, illum var (due to engine glowing), app var, ARC, **relatively easy**
4. **0176**: car drifting on a road 
app var (due to smoke), OPR, ARC
5. **0181**: person riding motorcycle 
illum var (multicolor), night scene (clutter due to similar background), SV, LR
6. **0238**: person on trampolin 
illum var (intensity + uneven), shape var (body shrunk to stretched etc)
7. **0241**: men holding a knife 
app var (reflections on the surface of knife), OPR so shape var (as side view is just a 1d line), **overall easy** (reflection area very less)
8. **0353**: gymnast doing stunts on pole 
articulation, shape var (body shrunk and stretched), SV, OPR
9. **0374**: boat in sea/river 
app var (app changes in later frames due to whilte trails of water occluding the white boat), clutter
10. **0399**: gymnast 
articulation, shape var. (body shrunk to stretched etc)
11. **0450**: man juggling with cup, glass bottle 
transparent object (glass bottle), IPR, FM, POC by colored cups 
GT bb should have been on the glass bottle instead of person

# Evalutaion metrics:

1. Precision
2. success rate (AUC)
3. Normalized precision : since precision is sensitive to resolution and size of bb, Pnorm is introduced which is l2 norm of (W * (Ctr - Cgt)), W = diag(BBx, BBy) (basically the area of bb)

# Dataset:

- Test set has same distribution as train set (as opposed to GOT-10k)
- some attributes (SV, ARC, FM, LR, OV) are automatically estimated while others are manully assigned.
- to check realtime perfomance, they conducted experiment where frames are skipped if a tracker is too slow.
- hard attributes : IPR, LR, FOC ; easy attributes : IV, POC, DEF
- Coarse annotations are provided by YT-BB at 1 fps. In order to increase
the annotation density, they rely on a mixture of state-of-the-art trackers to fill in missing annotations. they claim that any tracker is reliable on a small time lapse of 1 second. they densely annotated the 30,132 videos using a weighted average between a forward and a backward pass using the DCF tracker.

# Dataset analysis:

- some sequences could be made more challenging just by changing the target to be tracked (difficult subject is not taken as the target)
- Very less caeses of OV, FOC
- So many videos with knife, umbrella, skateboard as target (favours a particular set of classes)
- No hard sequences of smoke, fog etc.
- No hard sequences of illum var (multicolor, night etc)
- only one sequence of transparent target objects (that too doesnt have transparent object as the target)
- sequences with knife have very little reflection, more challenging case of reflection would be a bigger screen (like mirror etc.)
- TrackingNet shows a more natural motion distribution
- the arm and the legs are always included for the person class, regardless of the person’s pose. We argue that a tracker should be able to cope with deformable objects and to understand what it is tracking. In a similar fashion, the tails of animal are always included.
- easier than LaSOT