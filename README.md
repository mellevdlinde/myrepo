### Disney: Wednesday, February 5th

# Portfolio for Computational Musicology

Topic: What does it mean to be a "workout" playlist? Find several examples of workout playlists on Spotify and comparable playlists without the workout label. Is there a measurable difference between the groups?

So far, I compared the following "workout" playlists: Beast Mode, Motivation Mix and Top Hits Workout (all by Spotify). The "chill" playlists are: JAEL & CHILL (Jael), real good shit (Tom Misch) and Lo-Fi Beats (Spotify). I combined all playlists using `rbind()`, and did all analyses for individual playlists using `group_by(playlist_name)`. Some means and standard deviations I wanted to calculate, contained "NA". Therefore I used the argument `na.rm = TRUE` while calculating the means and standard deviations.

There was no real difference in danceability, all means were about .65, and the standard deviations about .12. As measured by Spotify, the workout playlists score higher on energy *(M = 0.81, SD = 0.12)* than the chill playlists *(M = 0.45, SD = 0.17)*. This is not very surprising, since a workout playlist should motivate. Therefore a higher energy level might be more motivating! The chill playlists were, as measured by Spotify, much more acoustic *(M = 0.39, SD = 0.28)* than the workout playlists *(M = 0.10, SD = 0.13)*. This finding is also expected, assuming that acousticness lowers the degree of being suitable for a workout playlist. The same holds for instrumentalness: chill playlists *(M = 0.38, SD = 0.29)* score notably higher than workout playlists *(M = 0.05, SD = 0.10)*. The last difference that was found is expected as well, it's the tempo. A higher tempo track seems more suitable for a workout playlist, than a lower tempo track. This is exactly what the Spotify data tells: workout playlists *(M = 124.84, SD = 18.32)* have a higher tempo than chill playlists *(M = 109.14, SD = 30.99)*. However, this might not be a significant difference when looking at the distributions. I plotted it in R using the following code:

`x <- seq(60,160,.01);
plot(x, dnorm(x, 124,18.32), type = "l", xlim = c(60,160));
points(x, dnorm(x,109,31), type = "l", col = "red")`

This shows that there is a big overlap for the two playlists in tempo. Therefore, it's questionnable whether the difference in tempo is substantive. 

Finally, I made some boxplots to see if there are any outliers for each playlist on each variable. There are some for particular playlists. However, there is always another playlist that has this outlier as well, or it falls in the "normal" range of another playlist. Therefore, I decided not to exclude any outliers.


