# Cartoonizer with OpenCV
This Python project applies a **cartoon effect** to any input image using OpenCV. It uses a combination of **bilateral filtering** and **adaptive thresholding** to produce a smooth, edge-highlighted, cartoon-like output.

## 📌 Steps Involved in Cartoonizing an Image:
### 1. Downsampling the Image
The image is downsampled using a Gaussian pyramid to **reduce its size**, making the filtering operations faster and more efficient.

### 2. Bilateral Filtering
A bilateral filter is applied multiple times to **smooth the colors** while **preserving the edges**.
This helps in achieving a **painted or cartoonish look**.

### 3. Upsampling the Image
The filtered image is then **upsampled back** to the original size.
This retains the smoothing effects from the smaller resolution.

### 4. Creating the Edge Mask
**a) Convert to Grayscale**<br/>
```img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)```
<br/>
Converts the original image to grayscale to simplify edge detection.

**b) Apply Median Blur**<br/>
```img_blur = cv2.medianBlur(img_gray, 3)```
<br/>
Removes small noise while keeping important edge details.

**c) Adaptive Thresholding**<br/>
```img_edge = cv2.adaptiveThreshold(img_blur, 255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY, 9, 2)```
<br/>

Detects edges in the image using adaptive thresholding.Produces a black and white sketch-like map of the image.

### 5. Combining the Edges with the Smoothed Image
**a) Resize and Convert Edge Image**<br/>
```img_edge = cv2.resize(img_edge, (y, x))```

```img_edge = cv2.cvtColor(img_edge, cv2.COLOR_GRAY2RGB)```

Ensures the edge image has the same dimensions and color format as the smoothed color image.

**b) Bitwise AND Operation**<br/>
```final_cartoon = cv2.bitwise_and(img_color, img_edge)```
Combines the smooth color image with the edge map to get the final

## 🚀 How to Run
1.Clone the repository.<br/>
2.Install dependencies:<br/>
```pip install opencv-python```<br/>
**Run the script:**<br/>
```python cartoonizer.py```
Output will be saved as Cartoon version.jpg.<br/>

## 📁 Dependencies
Python<br/>
OpenCV (cv2)
