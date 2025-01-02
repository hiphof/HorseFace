# Horse Face Recognition

## Abstract
- Brief overview of the project.
- Key objectives, methods, and outcomes.
- Summary of results and conclusions.

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

### 3.5 Modeling
- Used both Custom model (~ 8 layers) and ResNet model.
- "ResNet-50 is a deep convolutional neural network with 50 layers that uses residual learning through skip connections to address the vanishing gradient problem, enabling efficient training of very deep networks for image classification and feature extraction tasks."
- Details of the model implementation (e.g., ResNet-50, pre-trained or trained from scratch).
- Training process:
  - Optimizer: using an Adam (Adaptive Moment Estimation) optimizer
  - Learning rate: Default learning rate of 0.001  (e.g., optimizer, learning rate, loss function).
  - Loss-function: Categorical crossentropy (ideal for multi-class classifiction)
- Hyperparameter tuning: tried batch-size 32 up until 128

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
- Tabular and graphical representation of performance metrics.

![Confusion Matrix](/data/confusion_matrix.png)

- Confusion matrix, ROC curves, etc.

### 4.2 Discussion
- Analysis of results.
- Strengths and weaknesses of the model.
- Comparisons to baseline or other existing models.
- Impact of data quality and preprocessing on results.

---

## 5. Deployment

Deployment is not implemented. Only testing on premise, on laptops.

---

## 6. Conclusion
- Summary of the project's accomplishments.
- Key findings and their implications.
- Limitations of the current approach.

---

## 7. Recommendations and Future Work
- Data collection: find a dataset with horses with diverse backgrounds.
- Dataset augmentation:
  - Try removing the background of the horses
  - Crop the object
  - Add feature in which stable the horses are captured
- Use all 47 horses instead of only the first 10.
- Test models like PetFace and ArcFace.
- Use better hardware (GPU)
- Use pre-trained ResNet model
- Use metrics like recall and F1.

---

## 8. References
- Dataset used: (https://ieee-dataport.org/open-access/thdd)

---

## 9. Appendices *(if needed)*
- Additional figures, charts, or tables.
- Details of the codebase or scripts used.
- Extended results (e.g., performance on subgroups).