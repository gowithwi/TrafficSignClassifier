

# **Traffic Sign Recognition** 

##  Template


---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report



### Data Set Summary & Exploration

#### 1. Basic summary of the data set.
I used the pickle library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799 samples
* The size of the validation set is 4410 samples
* The size of test set is 12630 samples
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43



#### 2. Data preparation.

As a first step, I normalized the image data from [0 255] to [-1 1]. Theoretically, it would help better the parameter finding. In practise, it is confirmed that before doing so, the accuracy is always lower than 0.92; with the normalized dataset, I can occasionally achieve 0.95+.

As a second step, I followed the LeNet architecture to analyze the data, as shown in the table below, which describes the final model.

#### 3. Model architecture.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x3 RGB image   							| 
| Convolution 3x3     	| 1x1 stride, same padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6				    |
| Convolution 3x3	    | 1x1 stride, same padding, outputs 10x10x16   	|
| Fully connected		| outputs 120                				    |
| RELU					|												|
| Fully connected		| outputs 84                				    |
| RELU					|												|
| Fully connected		| outputs 43                				    |

#### 4. Training.

To train the model, I played with few knobs.

First, I controled the learning rate. I set rate = 0.0015 at the beginning; when validation_accuracy > 0.92, I changed it to 0.0005. The number comes from trial and error. The idea is that at the first few epochs I need a higher learning rate to update fast; but later in the training, I want the learning rate to be slow so that I don't overshoot.

Besides, I also played with the EPOCHS ( = 32) and BATCH_SIZE (= 64). The training pool has 34799 samples, whereas there are 43 types of y choises. Assuming 64 batch size, we could have 800 images per batch, that is large enough to cover the y choises, but not too large to leave less choise for EPOCHS. 

Given above, I can go max epochs number of 64, but since the training accuracy started to fluctuate, I decided to stop at 32, which is already good enough.

#### 5. Results.

My final model results were:
* validation set accuracy of 0.936
* test set accuracy of 0.925



#### 6. Last part of story.

I picked the first 5 images of the test data. The accuracy turns out to be 1.000.

I output the softmax, the first one has softmax > 0.99. All 5 are very eash because the contrast is good, and they are centered.




```python

```
