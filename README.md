# CVFinalProject
**Task 2 - Automated Breakfast Activity Recognition**

1. **Data Preparation & Preprocessing**
- Number of frames per each video : 16.
- Frames are resized to (224, 224).
- Frames are normalised to the range [0, 1].
- There are several Data Augmentation techniques used such as:
- Horizontal Flipping
- Rotation
- Brightness 
- Contrast Adjustments
- Cropping
- Translation
- Noise addition 
- Shearing

![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.001.jpeg)

**Dataset** 

The dataset is separated into “train” and “valid” folders.

The train folder is separated into 45 folders for 45 people. While the validation folder has 4 folders for 4 people. 

2. **Model Description & Techniques** 
- **InceptionV3-based 3D CNN with LSTM**:
  - The base model is InceptionV3, pretrained on ImageNet, used for feature extraction.
  - A TimeDistributed wrapper is used to apply the InceptionV3 model across the time dimension (16 frames).
  - Global average pooling and batch normalisation layers are added to reduce dimensionality and normalise the features.
  - Two LSTM layers are used to capture temporal dependencies across the frames.
  - Fully connected (dense) layers with dropout regularization are used for classification.
- **Model Architecture**
- ![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.002.jpeg)
- **Regularization Techniques**
- Dropout layers are used to prevent overfitting by randomly setting a fraction of input units to 0 at each update during training.
- L2 regularization is applied to the LSTM and dense layers to penalize large weights and encourage the model to find simpler patterns in the data.
- **Fine-Tuning**
- Fine-tuning involves unfreezing some of the layers in the InceptionV3 base model to allow their weights to be updated during training. This helps the model adapt the pretrained features to the specific task of breakfast action recognition.
3. **Training & Testing Times**
- **Table: Training and Testing Times for InceptionV3-based 3D CNN with LSTM**

  ![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.003.png)

4. **Video Classification Performance Metrics**

   ![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.004.jpeg)

\- More augmentation , add callbacks (early stopping and reduce learning rate)>> **best results**

5. **Confusion Matrix & Validation Accuracy**
- **Validation Accuracy Vs Training Accuracy plotting** 

![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.005.jpeg)

![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.006.png)

![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.007.jpeg)

- **Confusion Matrix**

![](Aspose.Words.5eb5dbaa-819f-4f64-818d-72036115f1b7.008.jpeg)
5
