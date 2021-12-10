# Face Detector
This project is the fourth assignment of the course *Principals of Computer Vision*.<br>

In this project, a face detector is implemented using a *HOG descriptor* and an *SVM classifier* to find faces within a picture.
The HOG descriptor is used for extracting feature vectors from images, and 
the SVM classifier is trained on a mix of a face and a non-face dataset to predict whether a given feature vector belongs to a face image or not. <br>

To find the best hyperparameters for both the HOG descriptor and SVM classifier, the mix of two datasets are split into the train, validation, and test datasets. 
Given a set of hyperparameters, the model is trained on the train set and evaluated on the validation set the best performing hyperparameters on the validation set are
then used in the final model and are further evaluated on the test dataset.<br>

To detect faces within an image, the sliding window algorithm on different scales of an input image is used to iterate through all the possible face locations in that image and then 
the previously obtained HOG descriptor and SVM classifier are used to determine whether a face exists in these locations or not.
Then a non-maximum suppression method is used to eliminate the duplicated face locations, and finally, the method returns the input image 
with all the detected face locations are highlighted using bounding boxes.

# Examples

Here are two examples of this face detector:<br>

Example 1:

<img src="https://github.com/sajjad2014/hog-face-detector/blob/master/out/Melli.jpg" alt = "Face detector example 1" width="70%">

Example 2:

<img src="https://github.com/sajjad2014/hog-face-detector/blob/master/out/Persepolis.jpg" alt = "Face detector example 2" width="70%">

From these examples, it can be interpreted that the model is capable of detecting faces in different scales and that it can detect faces that are slightly corrupted.

# Usage
To train the SVM classifier a face and a non-face is required. In this project, the 
[Labelled Faces in the Wild](http://vis-www.cs.umass.edu/lfw/)
is used as the face dataset and 
[Caltech-256](https://authors.library.caltech.edu/7694/)
is used as the non-face dataset.
After downloading these two datasets, put them under the `data/lfw`, and `data/256_ObjectCategories` folders beside the notebook.<br>

Now open the notebook and run all the cells. Load the input image and pass it to the `FaceDetector` function. <br>

Note that running cells aimed at finding hyperparameters are not necessary for running the `FaceDetector` function.
