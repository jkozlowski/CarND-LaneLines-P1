# **Finding Lane Lines on the Road** 

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline used the same basic methodology as the quizzes, up until finding Hough lines.
Once I have the Hough lines, I partition them on the slope sign (positive slope = left, negative = right)
and use numpy's polyfit to fit a line to each of the lane's points.

I then calculate the intersection point of the 2 lanes and draw those lines up to the intersection point 
(minus some offset). 

### 2. Identify potential shortcomings with your current pipeline

1) The lane lines are not smooth.
2) If I do not discover any lines, no lanes are drawn.
3) There are a few points in the yellow lanes video there the algorithm gets completely lost.

### 3. Suggest possible improvements to your pipeline

1 and 2) I could keep a fixed buffer of previous coefficients and average them (with a weight factor, 
         so that newer slopes are more important)
3) I could filter segments more aggressively, based on how far the slope is from the average. 
