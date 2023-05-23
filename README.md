# Number_plate_recognition_system
About
A system built for detecting vehical licence plate. Implemented using tensorflow,keras,opencv .CNN and chatracter segmentation is used for detecting.
# How to implement
# 1
 Finding Contours
In this, the image is first preprocessed and then sent for finding contours.
Image preprocessing contains the following steps:
- **Resizing the image**: Each image is resized to 500px width, to ease processing in the later stages.
- **Grayscale Conversion**: The input image is in RGB format. Main purpose of this conversion is to reduce the number of colors.
- **Noise Removal**: Image noises are distortion in the image that arises due to fault in camera or result of poor visibility due to changing weather conditions. Noises are also the random variation in the intensity levels of the pixels. Noise can be of various types like Gaussian noise, Salt and pepper noise. We used iterative bilateral filter for noise removal. It provides the mechanism for noise reduction while preserving edges more effectively than median filter.
- **Binarization**: Binarization is the process of converting an image into an image with two pixels value only i.e. containing white and black pixels. Performing binarization process before detecting and extracting license plate from the image will make the task of detecting license plate easier as edges will be more clearly in binary image.

After this, the image is ready to find contours.
Initially, all contours are found by using ```cv2.findContours()``` methods. All the contours with area less than 30 are discarded and the remaining contours are send for further processing. Each contour is approximated to form a polygon and if a contour is quadrilateral in shape (has 4 sides), then it is predicted to be the number plate and the contours are drawn using ```cv2.drawContours()``` method.
![1s](https://github.com/snehal224/Number_plate_recognition_system/assets/76654910/1bc05062-efa4-4377-87b3-e1cba9e79e7c)

# 2
Character Segmentation
Character segmentation is an operation that seeks to decompose an image of a sequence of characters into subimages of individual symbols. It is one of the decision processes in a system for optical character recognition (OCR).

This phase contains the use of two functions: ```segment_characters()``` and ```find_contours()```.
![2s](https://github.com/snehal224/Number_plate_recognition_system/assets/76654910/a51ddaf7-ba61-451b-9d88-0e535a9460c4)

# 3
 Character Recognition using CNN
Since the data is all clean and ready, now it’s time do create a Neural Network that will be intelligent enough to recognize the characters after training. In this project, we used CNN model for character recognition.
- For training the model, we’ll be using ImageDataGenerator class available in keras to generate some more data using image augmentation techniques like width shift, height shift.
- Width shift: Accepts a float value denoting by what fraction the image will be shifted left and right.
- Height shift: Accepts a float value denoting by what fraction the image will be shifted up and down.
![3s](https://github.com/snehal224/Number_plate_recognition_system/assets/76654910/484f6a12-2e5e-4ba7-902e-e38e1288e6fb)
![4s](https://github.com/snehal224/Number_plate_recognition_system/assets/76654910/f67e6225-c2ea-4962-8937-5bafd6b61730)
