# Melanoma Detection
Melanoma is the deadliest form of skin cancer among over 200 types. Its diagnosis generally starts with clinical screening, followed by dermoscopy and histopathology. Early detection is crucial for effective treatment. Dermatologists use high-speed cameras for visual inspection, achieving 65-80% accuracy in diagnosis. With additional expert analysis, accuracy increases to 75-84%. The project aims to develop an automated system using image processing to classify skin cancer from lesion images.

## Problem statement

To build a CNN based model which can accurately detect melanoma. Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution that can evaluate images and alert dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.

## Class Distribution

Class with the fewest samples: Seborrheic keratosis
Class dominating the dataset: Pigmented benign keratosis
To balance this, we employ proportional augmentation using zoom, since the images are centered.


## Model Designing Approach

Here's a step-by-step breakdown of the final CNN architecture:
Data Augmentation: The augmentation_data variable encompasses techniques like rotation, scaling, and flipping to expand the diversity of the training set, enhancing the model's ability to generalize.

Normalization: A Rescaling(1./255) layer normalizes image pixel values to a 0-1 range, aiding in quicker and more stable model training.

Convolutional Layers: We use three Conv2D layers, each followed by a ReLU activation for non-linearity. The layers use 16, 32, and 64 filters, respectively, with 'same' padding to maintain output size.

Pooling Layers: Each Conv2D layer is followed by a MaxPooling2D layer to reduce spatial dimensions, decrease computation, and help prevent overfitting.

Dropout Layer: A Dropout layer with a rate of 0.2 is introduced post-pooling to combat overfitting by randomly deactivating neurons during training.

Flatten Layer: The Flatten layer converts the 2D feature maps into a 1D vector for dense layers.

Fully Connected Layers: Two Dense layers follow, with the first having 128 neurons and using ReLU activation, preparing the data for final classification.

Output Layer: The final Dense layer's neuron count matches the number of classes (target_labels). No activation is specified here as it's handled by the loss function.

Model Compilation: The model uses the Adam optimizer, Sparse Categorical Crossentropy loss (suitable for multi-class classification), and tracks accuracy.

Training: The model is trained for 30 epochs using the fit method, allowing it to learn from the data over multiple iterations.
 

## Model Summary

225/225 ━━━━━━━━━━━━━━━━━━━━ 77s 338ms/step - accuracy: 0.9433 - loss: 0.1550 - val_accuracy: 0.4433 - val_loss: 3.3245
Epoch 30/30
225/225 ━━━━━━━━━━━━━━━━━━━━ 78s 340ms/step - accuracy: 0.9534 - loss: 0.1252 - val_accuracy: 0.6850 - val_loss: 1.4141


## Contact
Created by Milind Awade ML-C67 [@milindawade] - feel free to contact me!
