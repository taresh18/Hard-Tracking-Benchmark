# LaSOT

# Sequences

1. **airplane-9** : SV, ARC, OPR, long, shape var (shape in intermediate frames become quite different)
2. **book-19**: ARC, color variation , app var
opens a book such that appearance on cover page is different from inside pages. 
3. **car-2**: SV, Illum. var (intensity), reflection(due to rain) 
could be even more challenging if it was night scene + citylights (like in OTB-100)
4. **chamelion-3**: color variation 
could be harder if background was difficult instead of completely white (looks synthetic)
5. **crocodile-10**: app var (crocodile not clearly visible through the dirt and blue water), SV 
there is some part in video with no GT bb even though target in not out of view, we can add GT bb there too.
6. **cup-4**: transparent glass cup (background changes as man’s hand appear behind the cup) could be harder if cup was also moved etc.
7. **cup-7**: app var 
as hot water is poured into cup, app on surface of cup changes
8. **drone-2**: SV, ARC, night scene, app var (app changes due to SV, OPR) 
could be harder if in citylights instead completely black bg so more illum. var
9. **drone-13**: app. var (due to SV, OPR), occ, clutter (background similar to target in some frames), ARC, FM
10. **flag-9**: shape var (flag constantly changes shape), ARC 
could be harder if background was more difficult, may be taken as an idea
11. **frog-20**: app var, occ, SV, ARC
frog turned upside down + legs stretched so colour var + shape var
12. **gecko-1**: SV, motion blur + illum var (little)
very hard to locate the lizard in some frames but GT bb not provided for harder part
13. **goldfish-8**: illum var, clutter due to identical fish, occ
good case of reflections on water surface / fish
14. **hand-3**: FM, motion blur,  bb is small throughout
15. **horse-1**: illum var (intenisty + uneven), FOC, POC, SV, abrupt motion
16. **kangaroo-5**: SV, clutter (due to identical targets overlapping) 
identical kangaroos fighting, app in initial bb is very different
17. **kite-6**: shape var, ARC, OPR, SV 
as kite flies, shape becomes very different from first frame + due to OPR, target in some frames is only a 1d line
18. **leopard-12**: app. var, illum var (little), occ 
leopard disappears into muddy water so app. var, GT bb in some frames is only the head unlike the whole body in initial frames
19. **motorcycle-18**: illum var (multi color), SV, OPR, occ, IPR
20. **racing-10**: SV, app. var, occ 
appearance in some frames becomes very different e.g. in some frames target becomes the tyre of car unlike the whole car in initial frames.
21. **rubikcube-14**: color varication, shape variation
22. **sepia-8**: color change, SV, OV, ARC 
fish changes color, when target is out of frame, identical target appears in the frame so bb can shift to wrong object
23. **surfboard-12**: SV, occ / clutter due to white water trails, ARC
bb very small, board barely visible between white trails of water
24. **tank-14**: app var (smoke + dust), SV, occ 
nice case of smoke, dust causing app var
25. **turtle-16**: SV, ARC, some frames are very hazed (due to blue sea water) so turtle barely visible
26. **yoyo-7**: FM, motion blur, clutter due to similar background color
yoyo not properly visible in certain frames due to motion blur

# Evalutaion metrics:

1. Precision
2. Normalized precision : since precision is sensitive to target size and resolution, authors introduced normalized precision which ranks tracker based on AUC b/w 0 and 0.5
3. Success rate

# Dataset analysis:

- Dataset is densely annotated i.e. each frame is manually annotated (unlike others where interpolation etc is used)
- contains large number of categories and each category contain equal number of videos thus reducing category bias of trackers
- most challenging attributes - FM, OV, FOC
- also includes a qualitative analysis of trackes based on certain attributes
- No sequences / hard sequences of gymnasts / sports
- No hard sequences of illum. var (e.g. city lights scene, night scene etc)
- in billiards sequences, could have been harder if GT bb was on coloured balls rather than white so more clutter
- Gametarget sequences are synthetic
- Chamelion sequences could be made more challenging (one containing color variation is synthetic)
- Relative more challenging than other datasets and covers a variety of cases of appearance variation.
