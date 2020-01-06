# **Traffic Sign Recognition** 

---

### Code and output can be seen in the Traffic_Sign_Classifier.html
### Data was not included in the repo


**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report

[//]: # (Image References)

[image1]: ./examples/visualization.png "Training Data"
[image2]: ./examples/trafficsigns.png "Traffic Signs"
[image3]: ./examples/predictions.png "Predictions"
[image4]: ./examples/valid.png "Validation Data"
[image5]: ./examples/test.png "Test Data"
[image6]: ./examples/predictions.png "Predictions"
[image7]: ./examples/predictions.png "Predictions"
[image8]: ./examples/predictions.png "Predictions"
[image9]: ./examples/predictions.png "Predictions"
[image10]: ./examples/predictions.png "Predictions"

---

### Data Set Summary & Exploration

#### Basic summary of the data set.

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34,799
* The size of the validation set is 4,410
* The size of test set is 12,630
* The shape of a traffic sign image is 32 x 32 x 3 (rgb)
* The number of unique classes/labels in the data set is 43

#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set.

![alt text][image1]
![alt text][image4]
![alt text][image5]

### Design and Test a Model Architecture

#### 1. Preprocessing 

As a first step, I decided to convert the images to grayscale and to make the 
computation on the neural network less costly. The neural network does not need all three 
channel to make calculations on. Also, normalizing the data kept the data within
the a smaller scale constraint since pixel values can be somewhat wide-spread, 
however not necessary.


#### 2. Model Achitecture

My final model consisted of the following layers:

| 		Layer			|				Description			 			| 
|:---------------------:|:---------------------------------------------:| 
| Input         		|		32x32x1 Gray-scale image				| 
| Convolution        	|		Input = 32x32x3 Output = 28x28x6		|
| RELU					|												|
| Convolution	      	|		Input = 28x28x6 Output = 14x14x10		|
| RELU          	    |			 									|
| Convolution		    |		Input = 14x14x10 Output = 8x8x16		|
| RELU				    |		 										|
| Pooling				|		Input = 8x8x16 Output = 4x4x16			|
| Flatten				|		Input = 4x4x16 Output = 256				|
| Fully Connected		|												|
| Flatten				|		Input = 256 Output = 120				|
| RELU  				|												|
| Dropout 				|												|
| Fully Connected 		|		Input = 120 Output = 100				|
| RELU 					|												|
| Fully Connected 		|		Input = 100 Output = 84					|
| RELU					|												|
| Fully Connected 		|		Input = 84 Output = 43					|
 


#### 3. Training 

To train the model, I used an convolutional neural network as seen above. This network had 7 layers.
I used an Adam Optimizer in order to reduce error. 

Learning rate: 0.0009
Epochs: 100
Batch size: 128

#### 4. Approach 

My final model results were:
* validation set accuracy of 97.2% 
* test set accuracy of 95.2%

The steps for the network were as followed:
1. Preprocess and shuffle data
2. Obtain logits through the LeNet 
3. Calculate the softmax cross entropy with the logits
4. Calulate the loss based on the errors associated with each result
5. Optimize using gradient descent and a learning rate
6. Evaluate accuracy.


### Test a Model on New Images

#### 1. Six random German traffic signs for testing

Here are Six German traffic signs that I found on the web:

![alt text][image2] 

#### 2. Model predictions 

Here are the results of the prediction:

The test predicted with a 100% accuracy for these 6 new images.

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Speed limit (30)      | Speed limit (30)  							| 
| Bumpy Road     		| Bumpy Road 									|
| Ahead Only			| Ahead Only									|
| No vehicles	      	| No vehicles					 				|
| Go straight or left	| Go straight or left      						|
| General caution		| General caution      							|


#### 3. Top 5 softmax probabilities for each image along with each probability

The code for making predictions on my final model is located in the 33th cell of the Ipython notebook.

Here is the final result figure:

![alt text][image3]
![alt text][image6]
![alt text][image7]
![alt text][image8]
![alt text][image9]
![alt text][image10]
