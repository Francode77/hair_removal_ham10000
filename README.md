
# Hair removal on HAM10000
This script eliminates hairs from images from the HAM10000 dataset. The algorithm checks which images to patch, then it saves the patched image in the destination folder. The algorithm can be tweaked further with the settings.

# Prerequisites 

- Python 3.x
- HAM10000 dataset must be loaded in folder `/data/HAM10000`<br>
*The dataset can be downloaded from Kaggle: [Skin Cancer MNIST: HAM10000
](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)*

# Installation

This script requires the opencv library.

`pip install opencv-python`

# Includes

`patch_hairs.ipynb` - runs the script
`functions.py` - necessary functions

# Usage

1. Open the file `patch_hairs.ipynb` from a Jupyter notebook IDE<br>
2. Run all cells

The algorithm can be tweaked if necessary<br>


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

See my [article on medium](https://medium.com/@francode77/hair-removal-from-the-ham-dataset-2e884a423335) for more explanation

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
- Density histogram variance check<br> 
  
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

# Contributors

Written by [Frank Trioen](https://www.linkedin.com/in/frank-trioen-21b71135) , February 2023
 