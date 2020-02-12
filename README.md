### Portfolio for Computational Musicology!

Topic: **What does it mean to be a "workout" playlist?** In this portfolio, I'll take several examples of workout playlists on Spotify and comparable playlists without the workout label. Is there a measurable difference between the groups? What are workout playlist classifiers? And when can a song be classified as a workout song?

So far, I compared the following "workout" playlists: Beast Mode, Motivation Mix and Top Hits Workout (all by Spotify). The "chill" playlists is JAEL & CHILL. First, I used more playlists for "chill", but the amount of songs became too large compared to the workout songs. Now the ratio is better: 294 chill songs compared to 328 workout songs. 

I combined all playlists using `rbind()`, and did all analyses for individual playlists using `group_by(playlist_name)`. Some means and standard deviations I wanted to calculate, contained "NA". Therefore I used the argument `na.rm = TRUE` while calculating the means and standard deviations.

There was no real difference in danceability, all means were about 0.65, and the standard deviations about 0.13. As measured by Spotify, the workout playlists score higher on energy *(M = 0.80, SD = 0.13)* than the chill playlists *(M = 0.55, SD = 0.18)*. This is not very surprising, since a workout playlist should motivate. Therefore a higher energy level might be more motivating! The chill playlists were, as measured by Spotify, much more acoustic *(M = 0.31, SD = 0.28)* than the workout playlists *(M = 0.10, SD = 0.15)*. This finding is also expected, assuming that acousticness lowers the degree of being suitable for a workout playlist. The difference in loudness can also be explained fairly well. The workout songs were, on average, louder *(M = -4.77, SD = 2.07)* than the chill songs *(M = -8.73, SD = 3.53)*. One might argue that a workout song requires more power than a chill song does, and the power of a song can be determined by the volume level. The last difference that was found is expected as well, it's the tempo. A higher tempo track seems more suitable for a workout playlist, than a lower tempo track. This is exactly what the Spotify data tells: workout playlists *(M = 126.94, SD = 21.79)* have a higher tempo than chill playlists *(M = 109.17, SD = 31.12)*. However, this might not be a significant difference when looking at the distributions. I plotted it in R using the following code:

`x <- seq(60,160,.01);
plot(x, dnorm(x, 127,22), type = "l", xlim = c(60,160));
points(x, dnorm(x,109,31), type = "l", col = "red")`

This shows that there is quite some overlap for the two playlist types in tempo. Therefore, it's questionnable whether the difference in tempo is substantive. 

Finally, I made some boxplots to see if there are any outliers for each playlist type on each variable. There are a few found. However, the outliers on one variable of a playlist type always fall within the "normal" range of the variable of the other playlist type. Therefore, it seemed reasonable not to exclude any outliers.

### Disney: Wednesday, February 5th

For the Disney exercise, we tried to find out wat was different about "Let It Go" from Frozen compared to other Disney hits from the Disney Hits playlist by Walt Disney Records. To get the information, I used `get_playlist_audio_features('128899670', '5NtjgKz4doejP5HJtKXFcS')`. However, there were no substantive differences found. The only variable that was different was key. However, this might be hard (if not impossible) to interpret. The code I used can be found below.

`disney <- get_playlist_audio_features('128899670', '5NtjgKz4doejP5HJtKXFcS');
disney_sub <- disney[,6:16];
letitgo <- get_track_audio_features("0qcr5FMsEO85NAQjrlDRKo")[,1:11];
cbind(describe(disney_sub)[,c(3,4)], describe(letitgo)[,c(3,4)])`
