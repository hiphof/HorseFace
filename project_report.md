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
- To recognise a horse mainly by the face.

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
- Problem definition.
- Project requirements (e.g., accuracy, deployment constraints).

### 3.3 Data Understanding
- Description of the dataset(s) used (e.g., size, source, diversity).
- Exploratory Data Analysis (EDA): Key insights, distribution of data, biases.

### 3.4 Data Preparation
- For each horse a 2 minute movie is created. And of this movie stills are extracted. This was all done by 
- Data preprocessing steps (e.g., face alignment, resizing, normalization).
- Data augmentation techniques (e.g., flipping, rotation).
- Data splitting strategy (e.g., training, validation, test splits).

### 3.5 Modeling
- ResNet architecture overview.
- Details of the model implementation (e.g., ResNet-50, pre-trained or trained from scratch).
- Training process (e.g., optimizer, learning rate, loss function).
- Hyperparameter tuning.

### 3.6 Evaluation
- Metrics used to evaluate performance (e.g., accuracy, precision, recall, F1-score).
- Results of the evaluation on test data.
- Error analysis and insights.

---

## 4. Results and Discussion

### 4.1 Results
- Tabular and graphical representation of performance metrics.
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
- Suggestions for improving the system (e.g., more diverse datasets, better augmentation techniques).
- Potential areas for future research or development.

---

## 8. References
- List of all references used (e.g., research papers, articles, datasets).

---

## 9. Appendices *(if needed)*
- Additional figures, charts, or tables.
- Details of the codebase or scripts used.
- Extended results (e.g., performance on subgroups).