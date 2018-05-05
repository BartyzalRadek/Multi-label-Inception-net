# Multi-label-Inception-net
Modified `retrain.py` script to allow multi-label image classification using pretrained [Inception net](https://github.com/tensorflow/models/tree/master/research/inception).

The `label_image.py` has also been slightly modified to write out the resulting class percentages into `results.txt`. 

Detailed explanation of all the changes and reasons behind them: 
https://medium.com/@bartyrad/multi-label-image-classification-with-inception-net-cbb2ee538e30

### Works on:
[TensorFlow 1.8.0](https://github.com/tensorflow/tensorflow/releases/tag/v1.8.0) - use branch `master`

or

[TensorFlow 1.1.0](https://github.com/tensorflow/tensorflow/releases/tag/v1.1.0) - use branch `tensorflow_1.0` - thanks [moh3th1](https://github.com/moh3th1)

All the training images must be in JPEG format.

### Usage

#### Update
This version has been update to solve possible problems with calculating evaluation accuracies.

Usage change: 
Put all the training images in one folder and create a file `labels.txt` inside project root containing all the possible labels.

#### Prepare training images
1. Put all the training images into **one** folder inside `images` directory.

   The name of the folder does not matter. I use `multi-label`.

#### Prepare labels for each training image
1. We need to prepare files with correct labels for each image.
   Name the files `<image_file_name.jpg>.txt` = if you have an image `car.jpg` the accompanying file will be `car.jpg.txt`. 

   Put each true label on a new line inside the file, nothing else.

   Now copy all the created files into the `image_labels_dir` directory located in project root.
   You can change the path to this folder by editing global variable IMAGE_LABELS_DIR in `retrain.py`

2. Create file `labels.txt` in project root and fill it with all the possible labels. 
   Each label on a new line, nothing else.
   Just like an `image_label` file for an image that is in all the possible classes.

#### Retraining the model
Simply run the appropriate command from `retrain.sh`.
Feel free to play with the parameters.

**Disclaimer**: If you try to retrain the model with just the single example image `car.jpg`, it is going to crash.
Include at least 20 images in folder inside `images` directory.

#### Testing resulting model
Run: `python label_image.py <image_name>` from project root.

#### Visualize training progress
After the retraining is done you can view the logs by running:

`tensorboard --logdir retrain_logs`

and navigating to http://127.0.0.1:6006/ in your browser.


### Additional info
If you want to try the original Inception net retraining, here is an excellent CodeLab: https://codelabs.developers.google.com/codelabs/tensorflow-for-poets

#### License
Apache License, Version 2.0
