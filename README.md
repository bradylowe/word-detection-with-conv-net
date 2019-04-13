# Word-Detection-Using-YOLOv2-and-Tensorflow

**Collection of code for detecting and interpreting text from images**

This directory houses code, data, and neural network models
for the automation of parsing input text files such as pdfs, 
screenshots, or images of text. The word_detection.ipynb is 
not finished or working, but is available for viewing. All 
other files contain working code and are described below.

The gif seen here demonstrates the
use of the annotation tool image_labeler.py (OpenCV).

![](using_image_labeler.gif)

## Installation

**Dependencies:**
 - jupyter, matplotlib, tensorflow, numpy, scipy
 - sklearn (On Linux:  pip install scikit-learn)
 - cv2 (On Linux: pip install opencv-python)
 - time, datetime, math, os

After cloning the repo and installing the dependencies,
you can perform one of the following tasks:
 - **python image_labeler.py**
   * This is an image annotation tool for labeling object
     detection datasets.
   * To use this, you must have a directory with images of
     objects. 
   * Modify the *config.py* file to point to the image 
     directory or move your images into ./data/documents
     as well as class names
   * This program outputs two files:
      * imagefile_boxes.png:  Image with boxes drawn on it
      * imagefile.xml:        Annotations stored in this file
   * Controls:
      * Drag and drop with the left mouse to define bounding boxes.
      * Use number 0-9 to choose the class of the current bounding box.
      * Use "awsd" for panning the image left, right, up and down.
      * Use +/- keys for zooming in and out.
      * Use ESC key to exit without saving.
      * Use ENTER key to save the current boxes.
      * Use SPACE BAR to save and load the next image.
      * Use BACKSPACE to delete the previous bounding box.

 - **jupyter notebook digit_recognition.ipynb**
   * This is an environment where the [MNIST](http://yann.lecun.com/exdb/mnist/) dataset and/or subset of the
     [Chars74K](http://www.ee.surrey.ac.uk/CVSSP/demos/chars74k/) dataset can be loaded and used to train and test a conv.
     net for 0-9 digit recognition.
   * The model is defined in this environment and can be changed easily.
   * There are pretrained models provided in the *models* directory.
   * In this notebook, we visualize the weights of kernals at different 
     layers in the network to try to see what it is really learning.
   * The confusion matrix is also printed for the network. The confusion
     matrix, when visualized, gives insight into which characters are 
     being confused for one another.

 - **jupyter notebook char_recognition.ipynb**
   * This notebook is nearly identical to *digit_recognition.ipynb*, with
     the exception that here, we train a classification network on all 
     capital and lowercase letters as well as the digits 0-9.
   * The functions are coded such that we only load text of various fonts
     generated by computers. It is easy to modify the code such that we 
     also load characters photographed in the wild.

 - **jupyter notebook word_recognition.ipynb**
   * This code is not finished yet (currently under development)
   * When finished, this environment will allow for defining, training,
     and testing a simple word detection network.
   * The model used here is the [YOLO_v2](https://mlblr.com/includes/mlai/index.html#yolov2) model with some changes to
     the hyperparameters for better results with words and sentences.
   * The number of bounding box predictions here is larger than what 
     YOLO normally expects.

## List of files and directories

**Files**
 - **char_recognition.ipynb**:  ipython notebook environment for
                            training and testing neural networks
                            for classifying ascii characters.
 - **detection_utils.py**:  This file houses functions for reading
                            and writing bounding box and class info to
                            and from csv and xml files.
 - **digit_recognition.ipynb**:  Just a classifier for digits 0-9.
 - **image_labeler.py**:  A command-line program for annotating images
                          for creating dataset for detection systems. 
 - **make_xml_from_csv.py**:  A small script for creating xml files from
                              csv files (bounding box info).
 - **setup.cfg**:  Used for specific automated testing (pytest)
 - **teset_detection_utils.py**:  List of code test case implementation
                                  using pytest.

**Directories**
 - **data**:  Directory storing training and testing data for various models.
   * Chars74K (not included, see link above):  Stores dataset for classification of alpha-numeric chars.
      * This dataset is described in the following publication:  T. E. de Campos, B. R. Babu and M. Varma. Character recognition in natural images. In Proceedings of the International Conference on Computer Vision Theory and Applications (VISAPP), Lisbon, Portugal, February 2009. 
   * MNIST (not included, see link above):  Stores the MNIST 0-9 digit dataset
   * documents:  Stores images of documents and annotation files containing
                 bounding box information for detection system.
 - **models**:  Stores trained models such as character classifiers and 
            text detection models.
