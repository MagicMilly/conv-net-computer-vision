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
Due to computing and time constraints, the images were resized to 50x50 pixels and converted to greyscale for use in training a neural network.

## III. Modeling - an Iterative Process
## IV. Model Evaluation
## V. Conclusion & Recommendations

