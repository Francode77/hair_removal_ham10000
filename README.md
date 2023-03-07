
# Hair removal on HAM10000
This script eliminates hairs from images from the HAM10000 dataset. The algorithm can be tweaked with the variables

# Prerequisites 

- Python 3.x
- HAM10000 dataset must be loaded in folder `/data/HAM10000`
*The dataset can be downloaded from Kaggle: [Skin Cancer MNIST: HAM10000
](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)*

# Installation

This script requires the opencv library

`pip install opencv-python`

# Usage

Open the file `patch_hairs.ipynb` from a Jupyter notebook IDE<br>

Define variables if necessary<br>

Run all cells

*All necessary functions are stored in `functions.py`*

# Settings
The following parameters can be set:

#### Set width and height of the patches
r = 6

#### Set Canny parameters

| parameter | description |
| :-- | :--- | 
| canny_A  | threshold1 | 
| canny_B  | threshold2 | 
| aperture   | aperture size for the Sobel operator | 
| L2gradient | L2gradient  | 

#### Set HoughlinesP parameters

| parameter | description |
| :-- | :--- | 
| hough_method     |  'cv2.HOUGH_PROBABILISTIC' | 
| hough_resolution |    the resolution of rho in degrees | 
| hough_threshold  |    number of required votes | 
| hough_min_length |    the minimum line length | 
| hough_max_gap    |    maximum allowed gap | 
| hough_iter       |    number of iterations | 

#### Image patching thresholds
Parameters to decide whether the detections are ok to be processed

| threshold | description |
| :-- | :--- | 
| max_lines_cap  | Check density above this cap |
| max_density_cap  | Check density history variance above this cap |
| max_hist_variance_cap  |  Even distribution below this threshold |
| max_std_dev_cap  |  Even distribution below this threshold |
| max_variance_cap  |  Even distribution below this threshold |
| max_hist_variance  |  Maximum allowed density history variance |

# Method
1. Edge detection
2. Line detection
3. Coordinates
4. Distribution check:

**Max lines:**<br>
- Maximum number of lines for passing a density check

**On the density:**<br>
- Variance check<br>
- Standard deviation check<br>

**On the density histogram:**<br>
- Density histogram variance must<br>
 - never greater than max_hist_variance
 - never be greater than max_hist_variance_cap if max_density is higher than max_density_cap 

5. Patching

# Results

Currently the patching works best with a low amount of hairs. Though improving the patch function will lead to better results.

<p float="center">
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/OISIC_0024306.jpg" width="100" />
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/pISIC_0024306.jpg" width="100" /> 
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/ISIC_0024306.jpg" width="100" />
</p> 
*on the left: the unprocessed image, center: the detected lines, right: the patched image*

# Limitations
- Settings can be further improved for better results
- The algo does not patch at distances smaller than (r) from the edges
- The patch function can be improved

# Conclusion

The algorithm checks which images to patch, then it saves the patched image in the destination folder. 

# Contributors

Written by [Frank Trioen](https://www.linkedin.com/in/frank-trioen-21b71135) , February 2023
 