# Oil-Spill-Classification on SAR Images using Image Segmentation techniques
---


### Introduction

---

Oil pollution in the water and its effects on the marine ecology are caused by an increase in daily ship traffic and some normal ship operations including tank cleaning and engine effluent discharge. The Synthetic Aperture Radar (SAR) sensors are not affected by nighttime or adverse weather circumstances, and they are able to distinguish features between oil spills and the surrounding sea with more clarity than optical satellite sensors. A combination of image processing techniques can be used to classify the Oil Spills in these images and get an approximation on the intensity and extent of the spill. This will aid the authorities in the mitigation of the spill.

SAR images are shaped by the constant interaction of the transmitted high-frequency radar waves with target areas. This constant interaction causes random constructive and destructive noisiness that result in salt and pepper noise all over image. Our processing techniques improve the quality of image up to the mark where a oil spill can be marked distinctly on the image. Different combinations of techniques have been implemented which work the best together.

### Methodology

---

For the dataset, Oil Spill pictures captured by the SENTINEL-1 satellite were used. We selected 3 images which showed the most variations from each other and hence each required a different set of methods for the spill to be classified.

1. **`Image Type 1: Noisy with saturated Oil Spill`**
    - The image had a lot of salt and pepper noise, hence median filter was used to reduce it. Salt and pepper noise is basically black and white noise where black would be least and white would be the L – 1.
    - Median filter eliminates the min & max values by taking the median value which results into the removal of salt and pepper noise without blurring the images much.
    - Histogram was plotted and compared after and before using median filter and marginal difference was seen.
    - Next, as the oil spill was darker than the surrounding (sea) which was lighter, the image was inverted i.e., black to white and vice versa. This was done for further morphological operations.
    - From the plotted histogram the threshold was identified for basic segmentation i.e., prominently separating the oil spill from the sea (spill is white whereas sea is black).
    - After completing thresholding, the image had a lot of small objects surrounding the actual spill. To get rid of these objects opening morphological operation was used.
    - Opening is useful for removing small objects and thin lines from an image while preserving the shape and size of larger objects in the image.
    - Opening operation erodes an image and then dilates the eroded image, using the same structuring element for both operations.
    - Now to properly mark the edges for easy identification vertical and horizontal edge detection was used. This gave a marked oil spill on the image.
2. **`Image Type 2: Smooth image with distributed spills`**
    - This image was used as a variation test case for the operations used on image 1. The same operations gave a good result even when the spill was distributed, and the image was smoother.
3. **`Image Type 3: Low contrast with no marginal difference between spill and sea.`**
    - This image had very low contrast and the spill was hardly distinguishable from the sea. After plotting the histogram skewness was noticed to the left.
    - To combat this issue, histogram equalization method was used to increase the contrast.
    - Histogram equalization improves contrast by effectively spreading out the most frequent intensity values i.e. stretching out the intensity range of the image.
    - This method usually increases the global contrast of the images when its usable data is represented by close contrast values.
    - This allows for areas of lower local contrast to gain a higher contrast.
    - After equalization and plotting the histogram again, the threshold was identified to be 40. Using this threshold, thresholding was done which gave us a black and white image of the sea and the spill.
    - Thresholding basically converts all values below threshold to black and above threshold to white.
    - Some small objects were still present outside the spill which were cleared using opening morphological operation.
    - Finally both vertical and horizontal edge detection was done to mark the spill.

### Result & Analysis

---

- **`Image Type 1`**
    
    ![image](https://user-images.githubusercontent.com/43881544/206901712-564cd93c-1181-4203-9fa0-54e7d6372bea.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901725-8c4244cb-b00f-498f-a019-85423a35080e.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901735-c3f58316-0735-4bf5-adf5-93ec502e78de.png)
    
- **`Image Type 2`**
    
    ![image](https://user-images.githubusercontent.com/43881544/206901747-082fd38b-c363-4cd1-8301-964ec640c9d3.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901752-10867337-06ad-475a-8a98-d7f54d91cb0b.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901756-0967dda3-c8d2-4ab7-9014-1f62c448d70a.png)
    
- **`Image Type 3`**
    
    ![image](https://user-images.githubusercontent.com/43881544/206901762-912c9e98-e1f8-43cf-afa5-8f138ac1307b.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901771-2d3364b4-a781-4bb0-8b0c-2399da0df8d7.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901779-d2097849-b433-45da-ba43-5760ec2609d6.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901784-41a6db0f-f8bc-41e2-be95-872ff01b5811.png)
    
    ![image](https://user-images.githubusercontent.com/43881544/206901790-e6a29034-5108-49e4-8131-f1666d011118.png)
    

### Conclusion

---

A combination of techniques were implemented on 3 types of SAR images which have oil spills using the following techniques:

- Median Filtering
- Average Filtering
- Histogram Equalization
- Intensity Thresholding
- Edge Detection
- Opening Morphological Operation

We were able to successfully classify the oil spills in these images.
