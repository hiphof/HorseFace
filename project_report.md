# Horse Face Recognition

## Abstract
- In this study horses are classified based on the face, to make RFID scanner obsolete.
- The objective is to identify horses from our client Voskamp. This is done with a pre-trained Resnet CNN. The outcome is an accuracy of 62%. Based on CAM heatmaps it looks like the background is mostly responsible for the prediction.

---

## 1. Introduction

### 1.1 Background
- For humans the market and R&D in face recognition technology is huge.
- For horses there are no models and technology.
- Challenges in face recognition are variations in lighting, pose, expressions.

### 1.2 Objectives
- To recognise, and thus classify, a horse mainly by the face.

### 1.3 Scope
- Recognise horses from our dataset.
- Excluded from the scope: facial emotion detection.

---

## 2. Literature Review
- https://github.com/mapooon/PetFace has no experience with horses. 
- ArcFace: Additive Angular Margin Loss for Deep Face Recognition (https://insightface.ai/arcface)
- Agarwal: Face Recognition with Siamese Networks using ResNet-50 (https://medium.com/@ultimateabhi/face-recognition-with-siamese-networks-using-resnet-50-7831c44e404a)

---

## 3. Methodology

### 3.1 CRISP-DM Framework
- CRISP-DM methodology is a IBM methodology for Data Mining.

### 3.2 Business Understanding
- The current situation is that the horses are identified with RFID tags. The RFID tags are
on the neck of the horses. Some signals of RFID are not healthy for the horse, and it is
not convenient for the horse to have a RFID on their neck.
Also on horse shows, it would be more beautiful to have horses without RFID tags.

- Client: GreenTechlab (Anton Winkelmolen) and John Voskamp (owner of EquiMoves).

- After exploring the unlabeled data from our client, decided is to focus on publicly available labeled dataset.

- An acquired accuracy level is not set as an requirement, but a guideline would be 95%.

### 3.3 Data Understanding
- For the project the Tunisian Horse Detection Database (THDD) is used. The creator/author is Islem Jarraya.  https://ieee-dataport.org/open-access/thdd
- It consist of 47 unique horses. Total zipped size is 150 MB.
- Exploratory Data Analysis (EDA): All image dimensions are the same. Objects have more or less the same background.

### 3.4 Data Preparation
- For each horse a 2 minute movie is created. And of this movie stills are extracted. This was all done by Islem Jarraya.
- Face alignment: left ('Gauche'), right ('Droit') and middle.
- Data preprocessing steps: resized to 128x128 pixels, normalization to 0-1.
- Created a 0-index for horses.
- No Data augmentation techniques, such as flipping or rotation are used.
- Data splitting strategy: 64% training, 16% validation, 20% test. Stratified.
- Focused the get the models working on the first part (10 horses).
- To speed up modelling, only 20% of stills are used.

### 3.5 Modeling
- Used both Custom model (~ 8 layers) and ResNet model.
- "ResNet-50 is a deep convolutional neural network with 50 layers that uses residual learning through skip connections to address the vanishing gradient problem, enabling efficient training of very deep networks for image classification and feature extraction tasks."
- Details of the model implementation (e.g., ResNet-50, pre-trained or trained from scratch).
- Training process:
  - Optimizer: using an Adam (Adaptive Moment Estimation) optimizer
  - Learning rate: Default learning rate of 0.001  (e.g., optimizer, learning rate, loss function).
  - Loss-function: Categorical crossentropy (ideal for multi-class classifiction)
- Hyperparameter tuning:
  - tried batch-size 32 up until 128
  - Used pre-trained model 'ImageNet'

### 3.6 Evaluation
- Metrics used to evaluate performance: accuracy, precision.
- Results of the evaluation on test data: > 0.95 accuracy
- Error analysis and insights.

### 3.7 Technologies and Tools Used
- Frameworks: TensorFlow (::latest). 
- Libraries 
  - General: OpenCV, NumPy, pandas, Matplotlib
  - Keras: tf-keras for Keras 2.
  - CAM (Class Activation Mapping):
    - sicara/tf-explain: for TF, not working with Keras 3, and not working with `custom model`
    - jacobgil/pytorch-grad-cam: for Pytorch, most Github stars
    - frgfm/torch-cam: for Pytorch
- Hardware: laptop (Macbook Air M1, and two Windows laptops). No dedicated NVIDIA GPU.

---

## 4. Results and Discussion

### 4.1 Results
- Training Accuracy: 0.9633
- Validation Accuracy: 0.6114
- Test accuracy: **0.6193**
![Model accuracy](/scripts/results/model_accuracy.png)
![Confusion Matrix](/data/confusion_matrix.png)
![Grad-CAM](/scripts/results/grad_cam_2500.png)

### 4.2 Discussion
- Analysis of results.
  - The setting (background) contains the most changing pixels as seen in heatmaps.
  - Overfitting, because validation accuracy is higher than training accuracy
- Strengths and weaknesses of the model.
  - Only uses 20% of available images
- Did not compare with small custom model, due to problems with CAM (Activation Map).

---

## 5. Conclusion
- Our model could predict 62% of the horses, while using data of 10 horses.
- Limitations: It looks like above results are more based on the background than on the horses itself.

---

## 6. Recommendations and Future Work
- Data collection: find a dataset with horses with diverse backgrounds.
- Dataset augmentation:
  - Try removing the background of the horses
  - Crop the object
  - Add feature in which stable the horses are captured
- Use all 47 horses instead of only the first 10.
- Test models like PetFace and ArcFace.
- Use better hardware (GPU)
- Investigate further based on the correlation matrix. Find out why some horses have better accuracy than others.
- Use pre-trained ResNet model
- Use metrics like recall and F1.
- Check ROC curve with OvR or OvO

---

## 7. References
- Dataset used: (https://ieee-dataport.org/open-access/thdd)

---