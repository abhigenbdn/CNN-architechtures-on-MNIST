# CNN-architechtures-on-MNIST

--->A ConvNet architecture is in the simplest case a list of Layers that transform the image volume into an output volume (e.g. holding       the class scores).
--->There are a few distinct types of Layers (e.g. CONV/FC/RELU/POOL are by far the most popular).
--->Each Layer accepts an input 3D volume and transforms it to an output 3D volume through a differentiable function.
--->Each Layer may or may not have parameters (e.g. CONV/FC do, RELU/POOL don’t).
--->Each Layer may or may not have additional hyperparameters (e.g. CONV/FC/POOL do, RELU doesn’t).

To summarize, the Conv Layer:
Accepts a volume of size ---> W1×H1×D

Requires four hyperparameters: 
1.Number of filters -->(K,K)
2.their spatial extent --->(F,F)
3.the stride --->(S,S)
4,the amount of zero padding --->(P,P)

Produces a volume of size ---> W2×H2×D2
where:W2=(W1−F+2P)/S+1
W2=(W1−F+2P)/S+1
H2=(H1−F+2P)/S+1(i.e. width and height are computed equally by symmetry)
D2=K

Pooling Layer:
It is common to periodically insert a Pooling layer in-between successive Conv layers in a ConvNet architecture. Its function is to progressively reduce the spatial size of the representation to reduce the amount of parameters and computation in the network, and hence to also control overfitting. The Pooling Layer operates independently on every depth slice of the input and resizes it spatially, using the MAX operation. The most common form is a pooling layer with filters of size 2x2 applied with a stride of 2 downsamples every depth slice in the input by 2 along both width and height, discarding 75% of the activations.

Now the objective here is to test the MNIST handwritten character dataset on different convolution architechtures.Some of these architechtures are:-

1.LeNet. The first successful applications of Convolutional Networks were developed by Yann LeCun in 1990’s. Of these, the best known is the LeNet architecture that was used to read zip codes, digits, etc.
2.AlexNet. The first work that popularized Convolutional Networks in Computer Vision was the AlexNet, developed by Alex Krizhevsky, Ilya Sutskever and Geoff Hinton. The AlexNet was submitted to the ImageNet ILSVRC challenge in 2012 and significantly outperformed the second runner-up (top 5 error of 16% compared to runner-up with 26% error). The Network had a very similar architecture to LeNet, but was deeper, bigger, and featured Convolutional Layers stacked on top of each other (previously it was common to only have a single CONV layer always immediately followed by a POOL layer).
4.GoogLeNet. The ILSVRC 2014 winner was a Convolutional Network from Szegedy et al. from Google. Its main contribution was the development of an Inception Module that dramatically reduced the number of parameters in the network (4M, compared to AlexNet with 60M). Additionally, this paper uses Average Pooling instead of Fully Connected layers at the top of the ConvNet, eliminating a large amount of parameters that do not seem to matter much. There are also several followup versions to the GoogLeNet, most recently Inception-v4.
5.VGGNet. The runner-up in ILSVRC 2014 was the network from Karen Simonyan and Andrew Zisserman that became known as the VGGNet. Its main contribution was in showing that the depth of the network is a critical component for good performance. Their final best network contains 16 CONV/FC layers and, appealingly, features an extremely homogeneous architecture that only performs 3x3 convolutions and 2x2 pooling from the beginning to the end. Their pretrained model is available for plug and play use in Caffe. A downside of the VGGNet is that it is more expensive to evaluate and uses a lot more memory and parameters (140M).

