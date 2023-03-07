
# Hair removal on HAM10000
This script eliminates hairs visible on images from the HAM10000 dataset. 

# Prerequisites 

- Python 3.x
- HAM10000 dataset 
*The dataset can be downloaded from Kaggle: [Skin Cancer MNIST: HAM10000
](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)*

# Installation

This script requires the opencv library
`pip install opencv-python`

# Usage

Open the file `patch_hairs.ipynb` from a Jupyter notebook IDE<br>

Define variables if necessary<br>
Run all cells
All necessary functions are stored in `functions.py`

# Method
1. Edge detection
2. Line detection
3. Coordinates
4. Density distribution
5. Patching

# Choose the variables
The following variables can be chosen freely:

#### Set width and height of the patches
r = 6

#### Set canny thresholds
canny_A=100 <br>
canny_B=100

#### Set HoughlinesP parameters
hough_method     = 'cv2.HOUGH_PROBABILISTIC' <br>
hough_resolution = 720   # the resolution of rho in degrees) <br>
hough_threshold  = 35    # number of required votes) <br>
hough_min_length = 1     # the minimum line length) <br>
hough_max_gap    = 15    # maximum allowed gap) <br>
hough_iter       = 16    # number of iterations)

#### Image patching thresholds
max_lines_cap         = 99      # Check density above this cap<br>
max_density_cap       = 123     # Check density history variance above this cap<br>
max_hist_variance_cap = 5       # Even distribution below this threshold<br>
max_std_dev_cap       = 0.30    # Even distribution below this threshold<br>
max_variance_cap      = 0.10    # Even distribution below this threshold<br>
max_hist_variance     = 30      # Maximum allowed density history variance

# Settings
The script checks for parameters to know whether the detections are ok to be processed

**On the density:**<br>
- Variance<br>
- Standard deviation<br>

**On the density histogram:**<br>
- Density histogram variance<br>
 - never greater than max_hist_variance
 - if max_density is higher than max_density_cap : max_hist_variance_cap


# Results

Currently the patching works best with a low amount of hairs. Though improving the patch function will lead to better results.

<p float="center">
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/OISIC_0024306.jpg" width="100" />
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/pISIC_0024306.jpg" width="100" /> 
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/ISIC_0024306.jpg" width="100" />
</p> 
*on the left: the unprocessed image, center: the detected lines, right: the patched image*

# Limitations
- Function parameters can be further improved for better sensitivity
- The algo does not patch at distances smaller than (r) from the edges
- The patch function is very basic and can be improved

# Conclusion

The script can check if it's worth to remove and patch the hair regions, then it can save the patched image in the destination folder. 

# Contributors

Written by [Frank Trioen](https://www.linkedin.com/in/frank-trioen-21b71135) , February 2023
 