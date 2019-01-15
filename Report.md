# Report

## What

This report documents the pipeline built to annontate lane lines given an unannoted video and renders and overlay on the video

## Pipeline

The current pipeline achieves annotating the lane line with the following pipeline

1. Masking out colors greater than `180,180,0` to identify possible white line and yellow line segments
2. Convert the iamge to grey scale
3. Run the image through a gaussian filter and detect edges with a Canny transform
4. Mask out only the bottom part which is most likely the road
5. Find line segments with hough lines algorithm
6. Extrapolate segments and filter out unlikely candidates based on slope and end points. Group the remaining lines in left and right group
7. Average out the left and right into two thick lines. Render them onto the existing image   

## Shortcomings and improvements

1. The current lane end is hard coded to a number. 

   Possible improvement can be calculating a lane end point with the farthest lane segment detected

2. The current lane detection does not handle the challenge video which include curved lines and noisy elements like trees, colored roads etc.