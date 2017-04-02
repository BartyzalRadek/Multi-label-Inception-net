# Multi-label-Inception-net
Modified `retrain.py` script to allow multi-label image classification using pretrained [Inception net](https://github.com/tensorflow/models/tree/master/inception).

The `label_image.py` has also been slightly modified to write out the resulting class percentages into `results.txt`. 
### Requirements
[TensorFlow 0.12.0-rc1](https://github.com/tensorflow/tensorflow/releases/tag/0.12.0-rc1)

All the training images must be in JPEG format.

### Usage

#### Prepare training images
1. Create a directory for each label inside the `images` folder.
3. Take each of your training images and put them in folders corresponding to their respective categories. For example: image `car.jpg` is in two categories {`car`, `accident`} therefore it is going to be located in `images/car` and `images/accident` folders.

#### Prepare labels for each training image
We need to prepare files with correct labels for each image.
Name the files `<image_file_name.jpg>.txt` = if you have an image `car.jpg` the accompanying file will be `car.jpg.txt`. 

Put each true label on a new line inside the file, nothing else.

Now copy all the created files into the `image_labels_dir` directory located in project root.
You can change the path to this folder by editing global variable IMAGE_LABELS_DIR in `retrain.py`

#### Retraining the model
Simply run the appropriate command from `retrain.sh`.

#### Testing resulting model
Run: `python label_image.py <image_name>` from project root.

### Additional info
If you want to try the original Inception net retraining, here is an excellent CodeLab: https://codelabs.developers.google.com/codelabs/tensorflow-for-poets
