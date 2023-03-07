
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

#### Declare width and height of the patches
r = 6

#### Canny thresholds
canny_A=100 <br>
canny_B=100

#### Image processing thresholds
max_lines_cap=99 # Check density above this cap<br>
max_density_cap=123 # Check density history variance above this cap<br>
max_hist_variance_cap=5 # Even distribution below this threshold<br>
max_std_dev_cap=0.30 # Even distribution below this threshold<br>
max_variance_cap=0.10 # Even distribution below this threshold<br>
max_hist_variance=30 # Maximum allowed density history variance

# Results

Currently the patching works best with a low amount of hairs. Though improving the patch function will lead to better results.

<p float="center">
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/OISIC_0024306.jpg" width="100" />
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/pISIC_0024306.jpg" width="100" /> 
  <img src="https://github.com/Francode77/hair_removal_ham10000/blob/main/assets/ISIC_0024306.jpg" width="100" />
</p> 
*on the left: the unprocessed image, center: the detected lines, right: the patched image*

# Limitations

 
# Conclusion

While this script is by all means not intended to predict the price of a crypto asset, it clearly demonstrates the power of the tsfresh automated feature extraction library.

# Contributors

Written by [Frank Trioen](https://www.linkedin.com/in/frank-trioen-21b71135) , February 2023
 