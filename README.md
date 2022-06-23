# A Distributed Vision-Based Pipeline
## Prerequsites
One or more Jetson Nano boards with the following packages (code may work with other package versions than those listed):
* socket
* sys
* cv2 - 4.5.5
* os
* PIL - 8.4.0
* numpy - 1.19.5
* json
* torch - 1.8.0
* torchvision - 0.9.0

Make sure all Nanos (nodes) are connected to USB camera modules

A PC with the following packages:
* json
* socket
* numpy - 1.19.5
* struct
* PIL - 8.4.0

## User Implementation Guidelines
1. Copy the Vision-Node folder into your Jetson Nano home directory (you will get an error if it is in any directory besides home) and copy the Vision-Manager folder into your PC home directory. Make sure to keep the folder names the same. Make sure to keep all user-generated test scripts within these respective directories. 
2. Run these commands to create an instance of the Manager class:  
`from manager import Manager`  
`manager = Manager()`  
`#prompt to enter desired port number`  
3. Next, connect a node object to the Manager object created earlier (run these commands from the client side):  
`from node import Node`  
`node = Node()`  
`#prompt to enter desired port number, same number as entered for manager`  
`node.connect() #on the manager side, you should see a printout stating that a connection has been created`  
4. Before running inferencing, first test whether the node's camera pipeline is functioning using the takeImage() function. 
`manager.takeImage()`  
`#prompt asking user if they want to save the image`  
5. When running inferencing, you can either run a [standard pretrained classification model](https://pytorch.org/vision/stable/models.html) or run a custom model. You need to create a config .json file before running inferencing and store it inside of the Vision-Manager folder. Example config files are provided (test.json, test2.json). When running a standard model, this should be what your config file looks like:  
`{"custom":false,"model":{name of model, e.g. (resnet18, alexnet, vgg16}, "height":{integer value specifying height of images taken as input by model, "width":{integer value specifying width of images taken as input by model}}`  
Note: When specifying model name, ensure that the name is equal (characterwise) to the torchvision constructors (e.g. "resnet18" not ResNet18)  
6. 
