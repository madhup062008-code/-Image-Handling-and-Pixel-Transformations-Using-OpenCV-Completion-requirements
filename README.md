# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

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
- **Name:** MADHU .P  
- **Register Number:** 212225040215

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.jpg", cv2.IMREAD_GRAYSCALE
```

#### 2. Print the image width, height & Channel.
```
height, width = img.shape
print("Width :", width)
print("Height:", height)
print("Channels: 1 (Grayscale)")
```

#### 3. Display the image using matplotlib imshow().
```
plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
plt.title("Colour Image")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
color_img = cv2.imread("Eagle_in_Flight.jpg")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
color_img = cv2.imread("Eagle_in_Flight.jpg")
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
plt.title("Colour Image")
plt.axis("off")
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
crop = color_img[0:450,200:550]

plt.imshow(cv2.cvtColor(crop, cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```
resize = cv2.resize(crop, None, fx=2, fy=2)

plt.imshow(cv2.cvtColor(resize, cv2.COLOR_BGR2RGB))
plt.title("Resized Eagle")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()  
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
boy = cv2.imread("Boy.jpg")
```

#### 15. Adjust the brightness of the image.
```
matrix = np.ones(boy.shape,dtype="uint8")*50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(boy,matrix)
img_darker = cv2.subtract(boy,matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(12,4))

plt.subplot(131)
plt.imshow(cv2.cvtColor(boy, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(132)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker")

plt.subplot(133)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter")

plt.show()
```

#### 18. Modify the image contrast.
```
img_lower = cv2.convertScaleAbs(boy, alpha=0.8, beta=0)
img_higher1 = cv2.convertScaleAbs(boy, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(boy, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(12,4))

plt.subplot(141)
plt.imshow(cv2.cvtColor(boy, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(142)
plt.imshow(cv2.cvtColor(img_lower, cv2.COLOR_BGR2RGB))
plt.title("Lower")

plt.subplot(143)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Higher 1.1")

plt.subplot(144)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Higher 1.2")

plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
B,G,R = cv2.split(boy)

plt.figure(figsize=(12,4))

plt.subplot(131)
plt.imshow(B, cmap='gray')
plt.title("Blue")

plt.subplot(132)
plt.imshow(G, cmap='gray')
plt.title("Green")

plt.subplot(133)
plt.imshow(R, cmap='gray')
plt.title("Red")

plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged = cv2.merge((B,G,R))

plt.figure(figsize=(8,4))

plt.subplot(121)
plt.imshow(cv2.cvtColor(boy, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(122)
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.title("Merged RGB")

plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv = cv2.cvtColor(boy, cv2.COLOR_BGR2HSV)

H,S,V = cv2.split(hsv)

plt.figure(figsize=(12,4))

plt.subplot(131)
plt.imshow(H, cmap='gray')
plt.title("Hue")

plt.subplot(132)
plt.imshow(S, cmap='gray')
plt.title("Saturation")

plt.subplot(133)
plt.imshow(V, cmap='gray')
plt.title("Value")

plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge((H,S,V))

rgb = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)

plt.figure(figsize=(8,4))

plt.subplot(121)
plt.imshow(cv2.cvtColor(boy, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(122)
plt.imshow(rgb)
plt.title("Merged HSV")

plt.show()
```

## Output:
- **i)** Read and Display an Image. 1.Read 'Eagle_in_Flight.jpg' as grayscale and display: 

![alt text](<Screenshot 2026-07-31 084351.png>)

- **ii)** Save image as PNG and display:

![alt text](<Screenshot 2026-07-31 084404.png>)

- **iii)** Cropped image:

![alt text](<Screenshot 2026-07-31 084413.png>)

- **iv)** Resize and horizontally:

![alt text](<Screenshot 2026-07-31 084433.png>)

- **v)** Read 'Apollo-11-launch.jpg' and Display the final annotated image:

![alt text](<Screenshot 2026-07-31 084444.png>)

- **ii)**Adjust Image Brightness.

1.Create brighter and darker images and display:

![alt text](<Screenshot 2026-07-31 084504.png>)

- **iii)** Modify Image Contrast.

1.Modify contrast using scaling factors 1.1 and 1.2:

![alt text](<Screenshot 2026-07-31 084516.png>)

- **iv)** Generate Third Image Using Bitwise Operations.

1.Split 'Boy.jpg' into B, G, R components and display:

![alt text](<Screenshot 2026-07-31 084527.png>)

2.Merge the R, G, B channels and display:

![alt text](<Screenshot 2026-07-31 084535.png>)

3.Split the image into H, S, V components and display:

![alt text](<Screenshot 2026-07-31 084546.png>)

4.Merge the H, S, V channels and display:

![alt text](<Screenshot 2026-07-31 084559.png>)

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

