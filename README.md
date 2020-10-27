# Optical Character Recognition (OCR)
In this project, we built and OCR application based on a 

1. Download and unzip the dataset into a folder
2. Preprocess the data: both inputs and outputs

Input:
* Read the images and convert them into gray-scale images: reduce the bias of color
* Reshape each image to size (128,32):
  * 32: not too large not too small to enoughly detect characters
* Expand the dimension of the image from (128,32) to (128,32,1):
  * 1: the number of input channels
* Normalize the image pixel values by dividing it with 255

Output:

*   Read the image file names as the labels of that image
*   Encode word into digits using a map (‘a’:0, ‘b’:1 …….. ‘z’:26 ......) e.g.  "aabb" -> [0,0,1,1]
*   Find the maximum length among all words and pad every label to be the same size(max size) 


In this project, we train the model to recognize the word by predicting each character/digit for words  
So the char_list is the list of all characters (distinguish captical and lower case) and digits  
And we transform each word into char vector  

## Model Architecture
Paper link: (https://arxiv.org/pdf/1507.05717.pdf)

1. Input shape (1, 32, 128)
2. Use CNN to produce feature map
5. Make feature map compatible with LSTM layer.
6. Use two Bidirectional LSTM layers each of which has 128 units. 

loss: Loss function: CTC Details: (https://theailearner.com/2019/05/29/connectionist-temporal-classificationctc/)


## Inference
Steps:


1.   Take a picture
2.   Perform word or line detection
3.   Use OCR model to do predictions on every bounding boxes
4.   Visualize the result
