# Traffic Sign Recognition

## Writeup
### Build a Traffic Sign Recognition Project

The goals / steps of this project are the following:

* Load the data set (provided by the task itself and dounloaded from the web)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report

# Rubric Points
##### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.

### Writeup / README

##### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here {https://github.com/OSR-raw/SelfDriving2/blob/master/TraficSign/Traffic_Sign_Classifier.ipynb} is a link to my project code

### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the pandas library to calculate summary statistics of the traffic signs data set:

The size of training set is 34799
The size of the validation set is 4410
The size of test set is 12630
The shape of a traffic sign image is 32 *32 *3
The number of unique classes/labels in the data set is 43
#### 2. Include an exploratory visualization of the dataset.

Use the link to it: {https://github.com/OSR-raw/SelfDriving2/blob/master/TraficSign/Traffic_Sign_Classifier.ipynb}

### Design and Test a Model Architecture

##### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)


As a first step, I decided to convert the images to grayscale because it gives much better perseption of data we are interested in: differnces between the pixels that make up the image.

As a last step, I normalized the image data because it makes sense to keep input data within the boundaries like {-1, 1} or {0, 1}

I decided not to generate additional data.

#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

As basis for the project LeNet-Lab-Solution.ipynb was used.
It worked well with images of numbers.
Previously this kind of recognition I've been doing by means of linear algebra - converting image to matrix and calculating its singular values.
With the approach of CNN I had to change my point of view. Knowing the theory of perceptrons and the fact that it is guaranteed to converge to correct result {by Frank Rosenblatt}.
Yet within our system thats not really realistic - our activation functions do not have smooth derivative everywhere.
So another {biological} approach was taken {I have expirience with genetic algo}:

Layer 1 and 2 are convolutional. In biological way they are the eye {"FOW" of the eye was increased comparing to "LeNet-Lab" to get more of "overview"} plus first layers of neural cortex.They are not responsible for remembering but they are responsible for perceiving details. Pooling tho helps NN to focus on important details.
The thing that made my NN to be almost right away to be fulfilling requirements is increase in size of fully connected layers. Again why - because it makes sense that NN now has to "remember" 4.3 times more information than before.
After this change I've got ~92%

#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an supplied dataset for 100 iteration.
I was afraid of overfitting but result was 96.5% on validational set. I consider it as success.

#### 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:

* test set accuracy of 94%
* validation set accuracy of 96.5%
* test set accuracy of 100% {Even tho this is not really reliable. 5 images do not provide sufficient sampling}

### ADDTITIONAL AFTER REVIEW
* What was the first architecture that was tried and why was it chosen?
First arhitecture is the same that is used in the end - copy from "LeNet-Lab-Solution.ipynb" 
* What were some problems with the initial architecture?
Size of convolutianal layer and fully connected was obviously not sufficient.
* How was the architecture adjusted and why was it adjusted?
Increased size of convolutional layer and size of fully connected.
* Which parameters were tuned? How were they adjusted and why?
All the mentioned above plus number of epochs.
* What are some of the important design choices and why were they chosen?
Not much. Assuption was that NN is good but lust too small.

### Test a Model on New Images

#### 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web: {https://github.com/OSR-raw/SelfDriving2/tree/master/TraficSign/GermanImgs}

(I'm really sorry here. I do not know how to include images into .md file. I use online editor.)
### ADDTITIONAL AFTER REVIEW
* Nice job printing out the images here but you also are required to discuss before doing the actual prediction, what qualities your new images have (e.g: brightness, contrast, etc. ) that might cause your model to misclassify them.
What could have caused the problem is brightness inconsistency. Yet normalisation should have removed that. {Up to some extend tho. Overall brightness of background would have made sign itself not visible}

#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

The model was able to correctly guess 5 of the 5 traffic signs, which gives an accuracy of 100%. 
### ADDTITIONAL AFTER REVIEW
*You provide a good analysis of the results on the newly acquired images but forgot to compare the accuracy on the new set of images to that on the old test set and tell if your model is overfitting or underfitting.
Taking into account that I've got 100% accuracy and taking into account 94% on test set the chance to get 100% is 73.3%
Yet even this can not tell me if I am over/underfitting.
What this can tell me that with chance of 73.3% my NN is neither.
*Your explanation can look something like: the accuracy on the captured images is X% while it was Y% on the testing set thus It seems the model is overfitting
From data I have I can suggest the model is overfitting - thats why I got lover recognition rate for test set.
Preciselly this {test set recognition rate} helps to speculate about it.

#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the 8th cell of the Ipython notebook. Probabilities are there aswell.

### ADDTITIONAL AFTER REVIEW
* Just a little thing missing : You should clearly discuss how certain or uncertain your model is of its prediction.
Chances:
[[  1.00000000e+00   3.18314435e-26   8.26585780e-29   5.21670710e-31
    2.37113745e-36]]
[[ 7 40  5  8 42]]
Test Accuracy = 1.000
[[ 1.  0.  0.  0.  0.]]
[[8 0 1 2 3]]
Test Accuracy = 1.000
[[  1.00000000e+00   1.11592281e-27   1.36433888e-28   7.01872909e-29
    1.95939918e-30]]
[[5 3 6 2 1]]
Test Accuracy = 1.000
[[ 1.  0.  0.  0.  0.]]
[[12  0  1  2  3]]
Test Accuracy = 1.000
[[  1.00000000e+00   4.23970125e-29   1.43322424e-33   1.60533625e-34
    1.37967262e-37]]
[[10 37  5 42 40]]
Test Accuracy = 1.000

Taking into account that I've got nearly 100% chance for every image I can tell that model is completelly certain about its prediction.


##  Discuss the visual output of your trained network's feature maps. What characteristics did the neural network use to make classifications?

I was unable to understand how to use that function. I requires variables that are local and not accessible at that point.