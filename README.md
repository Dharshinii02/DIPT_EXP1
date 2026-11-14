# EXP.NO-1: Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## NAME: Dharshini J
## REG NO: 212224240036

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
Split the image into B, G, R components and display the channels

## Program Developed By:
- **Name:** Dharshini J
- **Register Number:** 212224240036

## Ex. No. 01

#### 1. Read the image using OpenCV imread() as a grayscale image.
```python
import cv2
import matplotlib.pyplot as plt
img=cv2.imread('Ip2.jpg')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
# Convert RGB to GRAY
image_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread('Ip2.jpg')
cv2.imwrite('Ip2.png',img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
# Read the image using OpenCV
img = cv2.imread('Ip2', cv2.IMREAD_COLOR)
# Change it to colour image
img=cv2.imread('Ip2.jpg')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
img shape
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)
# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image.
```python
# Read the image using OpenCV
img_app = cv2.imread('Ip2.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()  

```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image.
```python
img =cv2.imread('Ip2.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)  
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
### **i)** Read and Display an Image.

#### 1.Read 'Eagle_in_Flight.jpg' as grayscale and display:

<img width="322" height="405" alt="image" src="https://github.com/user-attachments/assets/d6488a69-4c8f-4363-8f68-f5ede9343876" />

#### 2.Save image as PNG and display:
<img width="330" height="412" alt="image" src="https://github.com/user-attachments/assets/fdbbd79d-a2a5-4441-b2ff-67cedad324b4" />

#### 3.Cropped image:

<img width="413" height="420" alt="image" src="https://github.com/user-attachments/assets/b5b5b39c-313f-4e65-9af6-de76c2f5a32f" />

#### 4.Resize and flip Horizontally:

<img width="311" height="412" alt="image" src="https://github.com/user-attachments/assets/bb2f1ad1-4070-4069-a4e4-d452eabb8a78" />




### **ii)** Adjust Image Brightness.

 1.Create brighter and darker images and display:  

<img width="1060" height="448" alt="image" src="https://github.com/user-attachments/assets/2ca6cd26-7720-4eb1-8f49-af57d81cbf4c" />

### **iii)** Modify Image Contrast.

1.Modify contrast using scaling factors 1.1 and 1.2:

<img width="1063" height="457" alt="image" src="https://github.com/user-attachments/assets/c76473b5-f853-4527-a810-fd99893f7daa" />

### **iv)** Generate Third Image Using Bitwise Operations.

1.Split 'Boy.jpg' into B, G, R components and display:

<img width="1125" height="458" alt="image" src="https://github.com/user-attachments/assets/43bd53a2-f599-45f1-9db5-9e3eb1113130" />


2.Merge the R, G, B channels and display:

<img width="447" height="557" alt="image" src="https://github.com/user-attachments/assets/8f1f1d51-e1f8-4527-8534-4eb3f28acf88" />


3.Split the image into H, S, V components and display:

<img width="1045" height="437" alt="image" src="https://github.com/user-attachments/assets/9108a84a-084b-4d2b-bd9d-dc59088f74d9" />


4.Merge the H, S, V channels and display:

<img width="851" height="555" alt="image" src="https://github.com/user-attachments/assets/f71d9970-953b-4192-bf8c-af4b396b21d5" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
