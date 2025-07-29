# Cataract Classification - ViT


🔗 [Homepage - AI Vet](https://aivet.hunian.kr/)

## Introduction

This project aims to develop a classification model to determine the presence and severity of cataracts in dogs. Cataracts are a significant cause of vision impairment in dogs, making early detection and accurate diagnosis crucial. The goal is to extend this model into a web or app service for quick detection without needing to visit a veterinarian. This project is part of a team machine learning project at Ajou University.

### Team Member

| Name | Dept | Github | 
| --- | --- | --- |
| 정용훈 | Software & Computer Engineering | https://github.com/hun9008 |
| 남현원 | Software & Computer Engineering | https://github.com/hwnam5 |
| 김혜성 | Software & Computer Engineering | https://github.com/com2t |
| 강수빈 | Software & Computer Engineering | https://github.com/gae-ddong |
| 권세빈 | Software & Computer Engineering | https://github.com/sebeeeen |


### Project Requirements, Assumptions, Risks, and Constraints

	• Requirements: Develop a highly accurate diagnostic model, with a particular focus on high recall for detecting early-stage cataracts (incipient).

	• Assumptions: The image data from AI-Hub is representative and accurately labeled.

	• Risks: The challenge of diagnosing cataracts using only image data, without additional medical equipment and tests.

	• Constraints: The model’s success criteria include achieving over 80% in accuracy, F1 score, and recall.

## Data

### Data Collection

	•	Source: AI-Hub canine eye images.
	•	Classes: No cataract, incipient, mature, overripe.
	•	Preprocessing: Resize images to 224x224 pixels, remove backgrounds, balance classes.

### Data Cleaning

	•	Removed black background images, minimized hair regions using grab cut algorithm, and applied blur to reduce remaining hair impact.

## Methodology

### Initial Models

	•	CNN, VGG16, ResNet50: Tested on initial pre-processed data, but all showed poor accuracy (0.51 - 0.67).

### Model Comparison

	1.	CNN-LSTM: Rejected due to low accuracy (0.46 - 0.41) on multi-class classification.
	2.	Pyramid-Net: Rejected due to poor performance (accuracy 0.58).
	3.	ViT: Accepted with the highest initial accuracy (0.79).
	4.	DeiT: Rejected due to implementation challenges and poor performance (accuracy 0.60).

### Hyperparameter Tuning

	•	Optimized using optuna, achieving best results with lr = 1e-4 and batch size = 16.

## Results

### Model Performance

	•	Accuracy: 0.849 with the final ViT model.
	•	Challenges: Distinguishing incipient from overripe cataracts.
<img src='img/ROC.png'>

### Explainable AI

	•	Techniques Used: LIME for local feature importance and Grad-CAM for visualizing important regions.
<img src='img/gradcam.png'>
<img src='img/lime.png'>

### Conclusion

The final model effectively classifies cataracts in dogs with high accuracy. Future work will focus on further model tuning and expanding applications.

For more details, refer to the project’s documentation.
