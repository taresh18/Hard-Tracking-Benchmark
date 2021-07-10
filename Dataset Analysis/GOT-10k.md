# GOT-10k

# Sequences

1. **video-6** : Penguin baby 
FM, POC, FOC, shape var (due to fast OPRs and POCs)
2. **video-24**: car passing through mud water 
app var due to mud water occ the car + OPR  (but very easy)
after passing through mud water, different view point of car appears (may be taken as an idea)
3. **video-30**: dog running through water 
SV, OPR, app change (due to water splashes / trails)
4. **video-36**: fish in blue sea water 
very hard to see the fish in hazy blue water in some frames (relatively easy than similar videos in LaSOT due to very less movement, short video length)
5. **video-66**: flying squirrel 
motion blur, SV, ARC, shape var (shape changes considerably as it closes its wings)
6. **video-67**: same as video-66 + night scene + clutter (due to dark background)
7. **video-84**: shape var (due to OPR + as wings open / close) + little dust towards the end of video could have been harder if video was continued further in the ‘dust’ part  
8. **video-111**: Gymnast 
articulation, shape variation, could be harder if more than one gymnasts so clutter  (relatively very easy than similar cases of articulation in trackingNet)

# Evaluation metrics:

1. No precision metric
2. One shot evaluation protocol: object classes in test and train data are completely different so tracker does not favour any particular object class seen in training except for ‘person’ class(but here too, motion classes are different between the test and train).
3. mean average overlap: avg overlap between GT and predicted bb, to keep it class balanced, they normalized it
4. mean success rate: % of successfully tracked frames where the overlap > threshold, also normalized

# Dataset:

- Instead of manually choosing the object classes, they used word-net proposed object classes such that there is an unbiased population of object classes. Also, motion classes were choosen similarly.
- Labels used : object classes, motion classes, absence indicator, object visible ratio
- hope the labeling of visible ratios can facilitate the tracking community to develop occlusion- aware tracking methods
- Attributes : they calculated the degree of each attribute based on its labels and if it is greater than some threshold, video is classified under that attribute. (Instead to manually assigning the attributes)
- They believe that class imbalance of training data imposes meaningful challenges to encourage for more practical trackers (dataset is somewhat class imbalanced)
- As no. of object classes increased, scores on some trackers improved indicating the importance of diversity in object classes.
- class imbalance vs. class balance : the scores improved only marginally
- seen vs. unseen : perfomance degraded on unseen classes promoting the importance of one shot evaluation protocol.

# Dataset analysis:

- Many cases of identical ojects crossing the target object.
- So many sequences of wildlife (class imbalance)
- No hard sequnces of illum. var (city lights, night etc)
- No hard sequences of smoke, fog etc.
- No sequence of transparent target objects.
- So many sequences are similar (basically 1 sequence is cut into 3-4 short sequences).
- Doesn't have different cases of appearance variation.
- Short and much easier sequences than lasot + not very different object classes (mostly wildlife).
- Categories are not rigorously balanced as number of videos varies a lot across different categories. (e.g. person class has more number of videos)
- show experimentally that enlarging the scale and diversity of test data significantly improves the reliability of the evaluation.
- observe a discernible decline in tracking performance for attributes fast motion, aspect ratio variation, scale variation and illumination variation when difficulty increases. This indicates that tracking under fast object state (position, scale, and orientation) and appearance (pose and illumination conditions) changes are still challenging for current trackers.