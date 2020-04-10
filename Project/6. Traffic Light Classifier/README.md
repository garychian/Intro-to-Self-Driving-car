# Traffic Light Classifier 
In this project, we will build a classifier for images of traffic lights use computer vision techniques(openCV) VS Deep learning and compare the accuracy between two method.

There are two datasets for traffic lights, one is the training set, the other one is test set. Each of the dataset contains: green, red and yellow

## Project pipline 
1. **`Loading and Visualizing the data`** The first step is familar with your data, so we need to load them and visualize them. 

2. **`Pre-Processing`** The input images and output labels need to be standardized. 

3. **`Feature Extraction`** Then, we extract some features from each image that will help distinguish and eventually classify these images
	
	The required feature is a brightness feature using HSV color space:

	1. A brightness feature: 

		Using HSV [](https://en.wikipedia.org/wiki/HSL_and_HSV) color space, create a feature help us identify. 
		
		`Standardized image`

		`HSV color-masked image`

		`Cropped imgae`

		`Brightness feature`

	2. Create more features to help accurately label the traffic light images
		
		It's major weakness is detecting green traffic lights on a very sunny day on which the camera either heavily overexposed the whole image including the traffic light or underexpoded it so it seemed (like in the two right images above) even for a human eye that it might be switched off.

		In general green was the hardest of the three colors to detect, because it doesn't have a single really dominating and in other regions of the image rarely occuring component like the red. In consequence (as seen in the second image above) in an overexposed image the "foggy" red area of the traffic light will dominate the green ones, because in this case it's just an arrow which even less scores for the green region of the traffic light.

		Another large weakness of my algorithm is out of question that it relies a lot on the matter that the images provided already contain the traffic light more or less in it's center. I think in practice when just receiving a video stream from an onboard camera the far harder part of detecting a traffic light's color would be to find the perfect bounding box for a traffic light at all.

4. **`Classification and Visualizing error`** In this section, we will have a function takes image as input and output label, also we write code to determine the accuracy of our classification model.

5. **`Evaluate your model`** To pass this project, the accuracy should > 90%. 

6. **`Improve the model use Deep learning`** The openCV method have a huge drawback, in practice, when receiving a video stream from an onboard camera the far harder part of detecting a traffic light's color would be to find the perfect bounding box for a traffic light at all. 
Also, the openCV method cannot handle sunny day and overexposed image.  

### Deep learning Model definition 
3 Convolution layers and 1 layer fully connected layer. The kernel size is 3x3, each layer's data is batch normalized, the after the final conv layer the data is average pooled before FC layer. 

## Final concludes 
**To pass this project, you must not classify any red lights as green!** Classifying red lights as green would cause a car to drive through a red traffic light, so this red-as-green error is very dangerous in the real world. 

OpenCV test accuracy: 98.6532%

Deep Learning neural network accuracy: 100%