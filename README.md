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
V. Conclusion </br>
VI. Recommendations to Improve Model
VII. Recommendations to Improve Diagnosis & Patient Care with Model 

## I. Load & Inspect Original Image Data
The original dataset consisted of 83,606 500x500 retinal scans belonging to four different classes. The images below represent an example of an original image from each class.
![four retinal scan images representing the different classes of data](/readme_images/fourclasses.png)

## II. Preprocess Data
Due to computing and time constraints, the images were resized to 50x50 pixels and converted to greyscale for use in training a neural network. The loop below iterates through the original data and saves new images to the desired size as a list, which was then saved as a numpy array using `np.save`.
![jupyter lab cell showing code to resize images](/readme_images/resize_images.png) 

## III. Modeling - an Iterative Process
I built a total of seven Convolutional Neural Networks, using validation loss and accuracy to optimize model performance while trying to combat overfitting. Adjustments included: 
* Adding zero padding to convolutional layers
* Reducing size of holdout set / Increasing size of training and validation sets
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
![confusion matrix for final model's performance](/readme_images/final_model_confusion_matrix.png)
Due to some class imbalance, the model performed much better on correctly classifying `normal` and `cnv` images than it did predicting `drusen` and `dme` images, though I don't believe that performance was completely due to class imbalance. The sample images show that `drusen` and `normal` retinal scans can appear similar, which is also reflected in the confusion matrix where 258 `normal` images were incorrectly classified as `drusen`. 
![sample images from each class again with arrows pointing to normal and drusen images](/readme_images/fourclasses_edit.png)
## V. Conclusion
All of the models had good accuracy scores between 87-97% for training data and 84-90% for validation data. The later models (Model 5 and beyond) had similar test accuracy scores around 90% which was an improvement over earlier models. Model 5 was also the first model to train on larger training and validation sets due to decreasing the holdout test size to 10% of the overall data. As usual, more data leads to better model performance. This is especially apparent in the Confusion Matrices, which clearly show that the model can more accurately identify CNV images - which was the class with the largest amount of samples. The models performed poorly on identifying Drusen images mostly likely because this was the smallest class and also because normal and Drusen images appear similar. 

## VI. Recommendations to Improve Model¶
* More data for each class, or at the very least - more data for the smaller classes of Drusen and DME
* Balanced classes with the addition of more images or data augmentation
* More information on disease progression and when the images were taken
  * Were the images of the non-normal classes taken in the early or late stages of disease?
  * If the non-normal class images were all taken in the later stages when changes are more prominent, the model will not perform well when introduced to early-stage non-normal images
  * The model would need images from a wide range of disease progression if it is to catch problems early
* The addition of patient information
* With enough computational resources, larger images could be used successfully with available pre-trained models

## VII. Recommendations to Improve Diagnosis & Patient Care with Model 
More information on the people whose images these belong to could greatly improve not only model performance, but also patient care, which is the ultimate goal when using computer vision to identify disease. Information that would be useful includes:
* Additional data for each patient
  * Family history of retinal disease
  * Family history of medical problems that can lead to retinal disease (i.e. Diabetes, Metabolic Syndrome)
  * Patient's age, ethnicity, gender, and other medical history and demographics
    * Risk of Macular Degeneration and Glaucoma increases with age
    * Caucasians have a higher risk of Macular Degeneration
    * African Americans, American Indians, and Mexican Americans have a higher risk of Diabetes
* Overall Risk Factor Score that takes additional patient information into account
  * An image that the model classifies as DME - or could possibly be DME - would appear to the clinician as having different risk levels when combined with other factors

