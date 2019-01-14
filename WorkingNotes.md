# What

Documents progress and list of things to do.

## Setup on windows

1. Need to revert prompt toolkit with

   ```powershell
   pip install 'prompt-toolkit==1.0.15'
   ```

2. Need to install opencv with

   ```powershell
   pip install opencv-python
   ```

## OpenCV documentation

It seems the most obvious doc I can find is [this](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_core/py_basic_ops/py_basic_ops.html#basic-ops). 

## Progress

1. Get helper functions working

2. Tune the functions for better performace

   1. Masked image with rgb = [180,180,0] so we have less noise

   2. Tried two ways

      1. ```python
         # Is able to find long lines
         rho = 1
         theta = np.pi*2/180
         threshold = 5
         min_line_length = 200
         max_line_gap = 100
         ```

      2. ```python
         # Is able to find short segments but cannot combine them
         rho = 1
         theta = np.pi*2/180
         threshold = 5
         min_line_length = 10
         max_line_gap = 5
         ```

      3. 

3. Need to align segments now

   1. We have two very likely segments
   2. For the long lane, we need to extrapolate the lin
      1. If the line is straight, we can just define a `min y` and `max y`
      2. Then for long lane
   3. For the shorter lane, we need to interpolate the function
      1. First, assuming **lane line** is straight, then we just need to 1st get the long line by combining them end to end
      2. Then extrapolate to `miny` and `maxy`

4. Challenge

   1. Now the segments are not straight, how can I group them?
      1. Get a list of lines