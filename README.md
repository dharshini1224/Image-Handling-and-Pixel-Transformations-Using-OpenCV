

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** Dharshini.S
- **Register Number:** 212224230061

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img =cv2.imread('Eagle_in_Flight.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```
img.shape

```

#### 3. Display the image using matplotlib imshow().
```
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray,cmap='grey')
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
img=cv2.imread('Eagle_in_Flight.jpg')
cv2.imwrite('Eagle.png',img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img=cv2.imread('Eagle_in_Flight.jpg')
cv2.imwrite('Eagle.png',img)

```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(img)
plt.show()
img.shape
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
img=cv2.imread('Apollo-11-launch.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()  

```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```
img =cv2.imread('boy.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```


#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)  
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)  
```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
 **i)** Read and Display an Image.
  <img width="572" height="418" alt="image" src="https://github.com/user-attachments/assets/5dd2f63e-22d6-4474-ad7d-1f36e83ec92f" />

 **ii)** 2.Save image as PNG and display:
  <img width="577" height="445" alt="image" src="https://github.com/user-attachments/assets/c689c16c-52a9-4e0b-90d8-400e3b22904a" />


 
**iii)** .Cropped image
  <img width="346" height="421" alt="image" src="https://github.com/user-attachments/assets/e9abab0a-3f9c-4aed-987a-f0a5e1992439" />


**iv)** Resize and flip Horizontally:
<img width="404" height="412" alt="image" src="https://github.com/user-attachments/assets/2abed3f7-0e31-469a-b621-a2c11a38e3ed" />

**v)**.Read 'Apollo-11-launch.jpg' and Display the final annotated image:
<img width="566" height="352" alt="image" src="https://github.com/user-attachments/assets/92aea34f-336f-4df2-b476-022d5d986a99" />


ii)* Adjust Image Brightness.

1.Create brighter and darker images and display:

<img width="827" height="244" alt="420662698-f34966ee-21f9-4441-bdd4-36c3da71b89d" src="https://github.com/user-attachments/assets/d7a818e7-aa85-424e-8b02-6b48f900f27a" />


iii) Modify Image Contrast.

1.Modify contrast using scaling factors 1.1 and 1.2

<img width="835" height="228" alt="420662827-998698a5-0d84-4f73-96d6-68421a529951" src="https://github.com/user-attachments/assets/0987ad9c-537e-499e-83e8-5b29a2198d30" />


iv) Generate Third Image Using Bitwise Operations.

1.Split 'Boy.jpg' into B, G, R components and display:

<img width="818" height="239" alt="420663150-54d59ef6-9800-4ff4-af13-f15fd602d334" src="https://github.com/user-attachments/assets/3e7e1c76-4c3b-41cf-a6b0-851363d2fe9a" />


2.Merge the R, G, B channels and display:

<img width="406" height="327" alt="421166243-6db4d2a2-8b21-43e5-976a-8f199eebc8cc" src="https://github.com/user-attachments/assets/dde89662-682a-47fb-8b0c-503c2a174f17" />


3.Split the image into H, S, V components and display:

<img width="793" height="211" alt="421166198-e5a79c38-d998-4ced-82d2-d750d465572d" src="https://github.com/user-attachments/assets/c75025ba-962c-4540-ae3b-152e2641fe72" />


4.Merge the H, S, V channels and display:

<img width="788" height="329" alt="421166035-2e2034ed-8cc3-4855-a8cb-87632e161c80" src="https://github.com/user-attachments/assets/a4e8651c-b78b-4fcf-a2c3-f346dc9fd03d" />

## Result:

Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

