# Semantic Segmentation Project
This is a project for Udacity Self-Driving Car Nanodegree program. In this project, I implemented free space searching algorithm on the road image based on the semantic segmentation technique. All codes are written on the iPython notebook. 

## Requirement 
- Python 3.0 >
- Tensorflow 1.0 >
- Numpy
- Scipy
- [Kitty Road Dataset](http://www.cvlibs.net/download.php?file=data_road.zip) 
  
## Run the Project 
Download the Kitti Road dataset. Extract the dataset in the 'data' folder. This will create the folder data_road with all the training a test images. Open the 'semantic_segmentation.ipynb' file and run it sequencially. 

## My Project Implementation
1) Neural Network Architecture  
- I used FCN-8 encoder/decoder architecture. I loaded pretrained VGG16 model into tensorflow followed by 1 by 1 convolution for spartial information. Then, I created the layers for a FCN (Fully Convolutional Network) using deconvolution and skip connection technique. For the detailed undertanding, please refer to below architecture image which I used in this project. 
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/FCN%20for%20Semantic%20Seg.gif)

2) Parameters 
- I used 30 Epochs & 8 batches for the neural network training in this project. 8 batches is the best fitting number for my system environment. When I used 30 epochs, the loss goes down from 5.0 to 0.02 even though there are ups and downs of losses between the epochs. If I use more than 30 epochs, the network was overfitted, and caused more errors to training images. Finally, I found that learning rate was optimal when it was 0.0001.     

3) Image Augmentations  
 - I implemented this in the helper.py. I used mainly 2 techniques. First, I used image rotation and expansion/shrinking technique. Second, I used the brightness control technique for the images. Then, I added those images to the training set, which made 2x image numbers for training. When I compared the result, image augmentation showed better accuracy, especially when there are dark shades on the images. 
 
## Project Result
1) KITTY road segmentation test images
- Mostly, it could separate road from non-road area even though there are a couple of minor errors  
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/runs/1509770087.947018/um_000005.png)
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/runs/1509770087.947018/um_000007.png)
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/runs/1509770087.947018/um_000015.png)
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/runs/1509770087.947018/umm_000008.png)
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/runs/1509770087.947018/umm_000035.png)

2) Recored road video
- I applied the trained model to the real road video. It showed good performance. You can see the full video in my repo. 
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/video1.png)
![Test image](https://github.com/KHKANG36/Semantic-Segmentation/blob/master/video2.png)

## Discussion/Plan
I will apply this model to 'CityScape Dataset' which requires more complex segmentation!!!! 
