# NN_behav-analysis
Analysis of behavioural data from a near-threshold intensity paradigm with Yes/No detection and 2-alternative-forced-choice localisation task 

Experiment:

Electrical stimuli are applied at near-threshold intensity (50% detection rate) to the index (F2) or ring finger (F1) of the left hand. Only 1 finger at a time is stimulated. Each trial contains a visual cue & a stimulus, followed by a Y/N detection task ("Did you feel the stimulus? Yes or No") and 2AFC localisation task ("Where was the stimulus applied? Ring or index finger"). Every participant completed 5 experimental blocks. All blocks had the same number of trials, trial numbers between ring and index finger were balanced, order of stimulation was randomised. Every 12 trials participants adjusted the position of the left hand (anatomical or crossed). Within every sub-block there were 2 catch trials where no stimulation was applied.

############################################################################################################################

Analysis:

01_yc_prepro
-add columns for det and loc task with sdt labels (hit, miss, correct rejection, false alarm)\n
-filter out trials where on either task no button was pressed or response time was > 5 s or < 0.15 s

02_yc_excl
-for every block calculate: detection rate of F1 and F2 in anatomical hand position, overall false alarm rate
-exclude blocks where for either finger detection rate is < 20 % or > 80 %, difference between detection rates is > 40 %, false alarm rate is > 40 %
-descriptive statistics of IDs left after pre-processing

03_yc_det-perf
-for every block calculate detection performance by finger (both/F1/F2) x position (overall/anatomcial/crossed)
-take within-subject mean detection performances by finger x position

04_yc_det-sdt
-for every block calculate detection sensitivity d' and response bias c by finger x position
-take within-subject mean d' and mean c by finger x position
          
05_yc_loc-perf
-for every block calculate localisation performance by position, based on all trials/only detected/only undetected
-take within-subject mean detection performances by detection x position
                 
06_yc_loc-sdt
-for every block calculate localisation sensitivity d' and response bias c (based on F1) by detection x position
-take within-subject mean d' and mean c by detection x position

07_yc_det-analysis
-Plot:
  -F1 vs F2 detection performance grouped by position
  -F1 vs F2 detection sensitivity d' grouped by position
  -F1 vs F2 detection response bias c grouped by position
  -F1 + F2 detection performance, d' and c by position
  -Stats, performed a) on within-ID averaged data, and b) on blocks of all IDs pooled together:
    a) -repeated measures two-way ANOVA: effect of finger x position on detection performance
       -repeated measures two-way ANOVA: effect of finger x position on detection sensitivity d'
       -repeated measures two-way ANOVA: effect of finger x position on detection response bias c 
       -paired t test/ wilcox test: compare means of F1+F2 detection performance/d'/c between anatomical and crossed
    b) -GLMM: effect of finger x position on detection performance
       -repeated measures two-way ANOVA: effect of finger x position on detection sensitivity d'
       -repeated measures two-way ANOVA: effect of finger x position on detection response bias c 
       -paired t test/ wilcox test: compare means of F1+F2 detection performance/d'/c between anatomical and crossed
       
08_yc_loc-analysis
-Plot:
  -localisation performance grouped by detection & position
  -localisation sensitivity d' grouped by detection & position
  -localisation response bias c grouped by detection & position
  -Stats, performed a) on within-ID averaged data, and b) on blocks of all IDs pooled together:
    a) -paired t test/ wilcox test: compare means of localisation performance/d'/c between anatomical and crossed
        (outliers excluded)
       -one sample t tests: localisation performance of undetected trials sign. > 50 %? d' sign. > 0?
    b) -paired t test/ wilcox test: compare means of localisation performance/d'/c between anatomical and crossed
        (outliers excluded)
       -one sample t tests: localisation performance of undetected trials sign. > 50 %? d' sign. > 0?

09_yc_resptimes


10_yc_det-loc_correlation


