# Dolphin-or-Seahorse
Getting 100% accuracy on Image Classification(2 Classes - Dolphin &amp; Seahorse) using Convolutional Neural Networks (AlexNet and GoogleLeNet)

###System Used: 
HP Pavilion 15 Notebook (4GB Memory, 1GB 740M Nvidia GPU) which is an average specification.

For an short introduction on Convolutional Neural Networks read this amazing [article](https://adeshpande3.github.io/adeshpande3.github.io/A-Beginner's-Guide-To-Understanding-Convolutional-Neural-Networks/) by [adeshpande3](https://github.com/adeshpande3)

###Steps to Setup:
- [Install Caffe](http://caffe.berkeleyvision.org/installation.html)
- [Install digits](https://github.com/NVIDIA/DIGITS)
- [Download Pretrained Model for AlexNet](http://dl.caffe.berkeleyvision.org/bvlc_alexnet.caffemodel)
- [Download Pretrained Model for GoogleLeNet](http://dl.caffe.berkeleyvision.org/bvlc_googlenet.caffemodel)

After installation, run 
```
./digits-devserver
```

Open localhost:5000 to access digits

###Creating Datasets

- Usually done by label, but we can segrigate the images into do different folders(one for dolphins and one for seahorses)
- Create new Imagedataset for classification 

##Model 1 : Training the Alexnet from scratch

- Create new Classification Model
- Add the dataset
- Choose AlexNet from Standard Networks
- Hit Create to start training.

For training from the dataset my system took the following time


![S-AlexNet JS](/S-AlexNet/T-AlexNetJS.png)

Intially the accuracy started with low and slowly after every epoch it started improving at the same time loss was reduced significantly. 


![S-AlexNet Graph](/S-AlexNet/TrainedAlexNet.png)

**Accuracy:** 87.5
**Loss:** 0.24

Here are few test results:
![S-AlexNet 01](/S-AlexNet/T-AlexNet01.png)
![S-AlexNet 02](/S-AlexNet/T-AlexNet.png)

Predictions now are not very confident, it is because the dataset we have is very small to get higher confident predictions.

To improve it we can use pretrained networks which are trained in ImageNet datasets with Million of images of 1000+ categories which will help get higher confident in prediction.

##Model 2 : FineTuning and Training the AlexNet

- Add AlexNet Pretrained Model which you have downloaded earlier.
- Add Model Definition for the AlexNet, We need to change the last layer of the AlexNet to configure the model for our dataset, like [this](/model_definition/FT-Alexnet.prototxt)
- Hit Create to start training.

For training from the dataset my system took the following time


![FT-AlexNet JS](/FT-AlexNet/FT-AlexNetJS.png)

The accuracy started with 55, but then directly shoots to max at 100, and slowly the loss reduced to near zero.


![FT-AlexNet Graph](/FT-AlexNet/FT-AlexNet.png)

**Accuracy:** 100
**Loss:** 0.000703

Here are few test results:


![FT-AlexNet 01](/FT-AlexNet/FT-AlexNet01.png)
![FT-AlexNet 02](/FT-AlexNet/FT-AlexNet02.png)


##Model 3 : FineTuning and Training the GoogleLeNet

Same as above, add GoogleLeNet Pretrained Moded and Model Definitions and hit Create

We need to change the last 3 layers of the GoogleLeNet to configure the model for our dataset, like [this](/model_definition/FT-GoogleLeNet.prototxt)

For training from the dataset my system took the following time


![FT-GoogleLeNet JS](/FT-GoogleLeNet/FT-GoogleLeNetJs.png)

The accuracy(3)  started somewhere in middle, but then reaches to max at 100, simulantously loss(3) dropped to zero.


![FT-GoogleLeNet Graph](/FT-GoogleLeNet/FT-GoogleLeNet.png)

**Accuracy:** 100,100,100 (3 Loss Layers)
**Loss:** 0.000027,0.000067,0.000013 (3 Loss Layers)

Here are few test results:
![FT-GoogleLeNet 01](/FT-GoogleLeNet/FT-GoogleLeNet01.png)
![FT-GoogleLeNet 02](/FT-GoogleLeNet/FT-GoogleLeNet02.png)
![FT-GoogleLeNet 03](/FT-GoogleLeNet/FT-GoogleLeNet03.png)
![FT-GoogleLeNet 04](/FT-GoogleLeNet/FT-GoogleLeNet04.png)
![FT-GoogleLeNet 05](/FT-GoogleLeNet/FT-GoogleLeNet05.png)
![FT-GoogleLeNet 06](/FT-GoogleLeNet/FT-GoogleLeNet06.png)

##Conclusion:
Convolutional Neural Networks was a hot topic in 2012-2015, a recent technology which gave a breakthrough in Image Classification field. And it's facinating to know that we can actually use it as a blackbox to get state of the art accuracy with almost no dataset in hardly 10 minutes. Caffe and Digits have contributed a lot in faster developement of such networks. In real time training a huge dataset like MsCoCo or Imagenet can take 10-15 days, but having a shared pretrained models lets any one like me with an average specs system, develop and use models to get state of the art accuracy.

Have a great brewing in caffe.

####[Source](https://github.com/humphd/have-fun-with-machine-learning)(Recommended)

Contact me at [ankitkumarojha2@gmail.com](https://mail.google.com/mail/?view=cm&fs=1&to=ankitkumarojha2@gmail.com&su=GitHub Dolphin-or-SeaHorse: &body=&bcc=) if you need my pretrained models or full model files.

