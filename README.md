# Level_segmentation_Kmeans
This is my first segment level. In this level, i have segmented by this funnel:
- Filter user first open (to ensure every one start at the same point) (in 30 days)
- Caculate all the metrics like winrate, drop, exit_drop, arpu, adrw_per_user, booster_per_user
- Then segment level by Kmeans

The purpose of this segment level is to help gd arrange level properly 

In this project, i've tryed many case/experiment to find the best model
- exper 1: all metrics
- exper 2: winrate, drop, exit_drop, arpu (adrw_per_user, booster_per_user has correlation with many metrics)
- exper 3: drop, exit_drop, arpu, ( at this case, i think that winrate is not influenced how i see level good or bad) -> expept winrate is proper
- exper 4: drop, arpu (at the previous case, i see that exit_drop influenced the cluster, but this metrics i think is not too important, it's pretty same drop)
- exper 5: drop, arpu filter level >= 15 (at the previous case, many level from 1 to 12 has the same cluster and both the high drop cluster, the reason is users of the first days are very easy to drop, so i filter 15 first level to avoid noise point/level
- exper 6: drop, arpu filter level >= 20 (at the previous case, i'm not satisfied with the result and i try one more time, now i'm so satisfy)

Next, i've just clusified but not know especifically this level is good or bad at that cluster. 
So i want to create formula like: grade = x*drop + y*arpu + intercept. there are 2 ways
- way 1: deterfine cluster 1 is the best -> find x & y by Logistic Regression
- way 2: deterfine cluster 1> cluster 0 > cluster 2 -> find x & y by Linear Regression
