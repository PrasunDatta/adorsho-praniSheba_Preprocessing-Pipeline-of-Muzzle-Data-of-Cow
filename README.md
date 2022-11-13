## Preprocessing Notebook.ipynb
In this notebook, a data preprocessing stage has been designed. At first, the images are read using OpenCV. Afterwards, they are passed through a sharpening filter where the blurry effect of images have been removed. Finally, to enhance the quality of these images, "Contrast Adaptive Histogram Equalization(CLAHE)" have been applied over those sharpened images. 
## Sharpening
For sharpening of images of muzzle, this sharpening kernel has been utilized. 

<img src = "https://editor.analyticsvidhya.com/uploads/22570Capture.PNG"  align ="center" />
 
 ### Python Implementation: 
 To sharpen an image in Python, we are required to make use of the filter2D() method. This method takes in several arguments, 3 of which are very important. The arguments to be passed in are as follows:

- src: This is the source image, i.e., the image that will undergo sharpening.

- ddepth: This is an integer value representing the expected depth of the output image. We will set this value to be equal to -1. In doing this, we tell the compiler that the output image will have the same depth as the input image.
- kernel: Since we wish to sharpen an image our kernel will be as the one presented above.
### Orginal Image vs Sharpened Image
<img src ="https://github.com/PrasunDatta/adorsho-praniSheba_Preprocessing-Pipeline-of-Muzzle-Data-of-Cow/blob/main/Images/Original%20vs%20Sharpened%20Image.png" width ="600" align = "center" />

## Histogram Equalization
A histogram of an image is the graphical interpretation of the image’s pixel intensity values. It can be interpreted as the data structure that stores the frequencies of all the pixel intensity levels in the image.

OpenCV has a function to do this, cv.equalizeHist(). Its input is just grayscale image and output is our histogram equalized image.

### Original Image vs Normal Histogram Equalized Image
<img src ="https://github.com/PrasunDatta/adorsho-praniSheba_Preprocessing-Pipeline-of-Muzzle-Data-of-Cow/blob/main/Images/Original%20vs%20Histogram%20Equalized%20Image.png" align ="center" width = "500" />

In addition to the ordinary histogram equalization, there are two advanced histogram equalization techniques called -

- Adaptive Histogram Equalization
- Contrastive Limited Adaptive Equalization
### Contrastive Limited Adaptive Equalization
Contrastive limited adaptive equalization (CLAHE) can be used instead of adaptive histogram equalization (AHE) to overcome its contrast overamplification problem. In CLAHE, the contrast implication is limited by clipping the histogram at a predefined value before computing the CDF. This clip limit depends on the normalization of the histogram or the size of the neighborhood region. The value between 3 and 4 is commonly used as the clip limit.

In CLAHE,image is divided into small blocks called "tiles" (tileSize is 8x8 by default in OpenCV). Then each of these blocks are histogram equalized as usual. So in a small area, histogram would confine to a small region (unless there is noise). If noise is there, it will be amplified. To avoid this, contrast limiting is applied. If any histogram bin is above the specified contrast limit (by default 40 in OpenCV), those pixels are clipped and distributed uniformly to other bins before applying histogram equalization. After equalization, to remove artifacts in tile borders, bilinear interpolation is applied.
### Original vs CLAHE Applied Image
<img src ="https://github.com/PrasunDatta/adorsho-praniSheba_Preprocessing-Pipeline-of-Muzzle-Data-of-Cow/blob/main/Images/Original%20vs%20CLAHE%20%20image.png" width ="500" align ="center" />

### Canny Edge Detector
The Canny edge detector is an edge detection operator that uses a multi-stage algorithm to detect a wide range of edges in images. It was developed by John F. Canny in 1986. Canny also produced a computational theory of edge detection explaining why the technique works. (Wikipedia)

The Canny edge detection algorithm is composed of 5 steps:

- Noise reduction;
- Gradient calculation;
- Non-maximum suppression;
- Double threshold;
- Edge Tracking by Hysteresis.
 ### Canny Edge Detector Result
<img src ="https://github.com/PrasunDatta/adorsho-praniSheba_Preprocessing-Pipeline-of-Muzzle-Data-of-Cow/blob/main/Images/Output%20of%20Canny%20Edge%20Detector.png" align = center width ="500" />

## Summary of Whole Preprocessing Pipeline 
<img src = "https://github.com/PrasunDatta/adorsho-praniSheba_Preprocessing-Pipeline-of-Muzzle-Data-of-Cow/blob/main/Images/Total%20Preprocessing.png" align = "center" />

