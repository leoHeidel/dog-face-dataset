# dog-face-dataset

The goal of this repository is to create a dataset of dog faces by using Flickr pictures.
we are for example able to extracte about 150000 images for the year 2015 alone.


## Code

- eager_dog_face_training.ipynb : This notebook uses the [TensorFlow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection) that needs to be installed. It trains a detector to detect dog faces by using the [Oxford-IIIT Pet Dataset](https://www.robots.ox.ac.uk/~vgg/data/pets/) that needs to be downloaded. This notebook was inspire by [this notebook from the detection API](https://github.com/tensorflow/models/blob/master/research/object_detection/colab_tutorials/eager_few_shot_od_training_tf2_colab.ipynb). It is quite fast (around 30 minutes).

- woofwoof-dataset-maker.ipynb : This is the main notebook of this repository. it has the folling steps:
    - First it downloads the metadata of the images by searching the Flickr API with the tag "dog". An API key is needed for this step. [A key can easily be obtained for free.](https://www.flickr.com/services/api/misc.api_keys.html)
    - Then the images are downloaded at size 1024. This steps can take a few hours.
    - In the third steps, the previously trained model is used to detect the face of dogs. The results is saved in dictionnary that is pickled every 1000 images in case the algorithm crashes.
    - The last steps will crop the best match for each picture, if it reaches a certain threshold.
    
    The result are however not perfect. Some images don't correspond to dogs, humans for examples. And some are note cropped well enough. 

