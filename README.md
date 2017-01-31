# AlexNet training on ImageNet LSVRC 2012

This repo offers the implementation of AlexNet model and its training and testing procedures on the ILSVRC 2012 dataset.

### Training
To train AlexNet just run the command:
```shell
python train.py option
``` 
with options ```-scratch``` to train the model from scratch or ```-resume``` to resume the training from a checkpoint.

The script assumes that ImageNet dataset folder is structured in this way:
```
ILSVRC2012
    ILSVRC2012_img_train
        n01440764
        n01443537
        n01484850
        ...
    ILSVRC2012_img_val
        ILSVRC2012_val_00000001.JPEG
        ILSVRC2012_val_00000002.JPEG
        ...
    data
        meta.mat
        ILSVRC2012_validation_ground_truth.txt
```

### Testing
To evaluate the accuracy of the trained model I used the ILSVRC validation set (no test set is available). Run simply:
```shell
python train.py
```
This evaluates *Top-1* and *Top-k* (you can set *k* inside the script) accuracy and error-rate.
Inside the script you can also play with the ```K_CROPS``` parameter to see how the accuracy change when the predictions are averaged through different random crops of the images.

### Classify an image
To predict the classes of an input image run:
```shell
python classify.py image
```
where ```image``` is the path of the image you want to classify.

e. g. that command on the ```lussari.jpg``` image 
![alt text](lussari.jpg)
gives the output:
```shell
AlexNet saw:
alp - score: 0.575796604156
church, church building - score: 0.0516746938229
valley, vale - score: 0.0432425364852
castle - score: 0.0284509658813
monastery - score: 0.0265731271356
```
Again, you can change the number of random crops produced and the *Top-k* prediction retrieved (here are both `5`).