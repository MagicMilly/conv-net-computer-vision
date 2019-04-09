# Detecting Retinal Disease with Computer Vision
## Final Project for Deep Learning Module - February 2019
![stylized photo of a human eye](/readme_images/cooleye.png)

## Objective: Train a Convolutional Neural Network to Classify Retinal Scans
The images used as [data](https://www.kaggle.com/paultimothymooney/kermany2018) for this project were obtained from Optical Coherence Tomography (OCT), which is a non-invasive diagnostic test used for examining cross-sections of the retina, though this technology is also applied in other medical and research fields. The images fall into one of four classes:
* **CNV** - Choroidal neovascularization - the abnormal growth of blood vessels beneath the retina. CNV is associated with many conditions, including some forms of myopia and macular degeneration. CNV can cause vision distortions and deterioration.
* **DME** - Diabetic macular edema - a symptom of diabetic retinopathy that causes fluid build-up within the retina. DME is the most common cause of vision loss associated with poorly-controlled and advanced diabetes. Other types of macular edema exist that are not associated with diabetes.
* **Drusen** - fatty deposits under the retina - some types of drusen may affect vision and increase the risk for macular degeneration, while other types may never cause any noticeable problems for the patient.
* **Normal** - no abnormalities present

## Methodology
I. Load & Inspect Original Image Data </br>
II. Preprocess Data </br>
III. Modeling - an Iterative Process </br>
IV. Model Evaluation </br>
V. Conclusion & Recommendations </br>

## I. Load & Inspect Original Image Data
The original dataset consisted of 83,606 500x500 retinal scans belonging to four different classes. The images below represent an example of an original image from each class.
![four retinal scan images representing the different classes of data](/readme_images/fourclasses.png)

## II. Preprocess Data
Due to computing and time constraints, the images were resized to 50x50 pixels and converted to greyscale for use in training a neural network. The loop below iterates through the original data and saves new images to the desired size as a list, which was then saved as a numpy array using `np.save`.
![jupyter lab cell showing code to resize images](/readme_images/resize_images.png) 

## III. Modeling - an Iterative Process
I built a total of seven Convolutional Neural Networks, using validation loss and accuracy to optimize model performance while trying to combat overfitting. Adjustments included: 
* Adding zero padding to convolutional layers
* Using early stopping as a callback 
* Reducing learning rate on plateau as a callback
* Trying different sizes and number of layers
* Trying different filter sizes
* Using dropout in the fully-connected dense layers
## IV. Model Evaluation
Changes made to each successive model, training time, and the resulting training and validation loss and accuracy were stored within a Pandas dataframe for easy comparison. The seventh model balanced performance metrics with goodness of fit. 
![dataframe showing comparison of the seven models](/readme_images/compare_all_models.png)
The plot below shows training and validation loss and accuracy compared to the number of epochs. Training and validation loss start to diverge after about 10 epochs. 
![plot showing loss and accuracy vs. number of epochs](/readme_images/train_val_loss_acc.png)
I used a confusion matrix to visualize how well the final model performed on predicting image labels. 
![confusion matrix for final model's performance](/readme_images/compare_all_models.png)
Due to some class imbalance, the model performed much better on correctly classifying `normal` and `cnv` images than it did predicting `drusen` and `dme` images, though I don't believe that performance was completely due to class imbalance. The sample images show that `drusen` and `normal` retinal scans can appear similar, which is also reflected in the confusion matrix where 258 `normal` images were incorrectly classified as `drusen`. 
![sample images from each class again with arrows pointing to normal and drusen images](/readme_images/
## V. Conclusion & Recommendations

