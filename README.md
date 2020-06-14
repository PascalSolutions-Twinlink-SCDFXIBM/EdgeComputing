# Edge Computing to pre-process livestream videos to IBM Cloud Object Storage (COS)

![framedifferencing](/pictures/framedifferencing.jpeg)

## Table of contents
* [General info](#general-info)
* [Included components](#Included-components)
* [Installation](#installation)
* [Dataset](#Dataset)
* [Flow](#flow)
* [Sample output](#Sample-output)

## General Info

### What is Edge Computing

Edge Computing brings computation and data storage closer to the devices where it is being gathered, rather than relying on a central location where it can be situated miles away. As such, even with real time data, it does suffer latency issues that can affect the application's performance. This way organisation can save cost by having processing done locally while reducing the amount of data that needs to be processed in a centralised or cloud based locaiton. 

![edgecomputing](/pictures/edgecomputing.jpg)

In this code pattern, we will take in livestream video as input and pre-process the video using OpenCV, Jupyter Notebook and other utility modules for file management. The code will load video into the Jupyter Notebook where we will process every individual frames and is locally stored. 

With the locally stored image, the images are then parsed and processed for detection of movement between frames using frame differencing technique.  

## Included components

* [IBM Cloud](https://www.ibm.com/sg-en/cloud/object-storage): IBM Cloud Object Storage is designed to support exponential data growth and cloud-native workloads. With built-in high-speed file transfer capabilities, cross-region offerings, and integrated services, IBM Cloud Object Storage can help you securely leverage your data.
* [Jupyter Notebook](https://jupyter.org/): An open source web application that allows you to create and share documents that contain live code, equations, visualizations, and explanatory text.
* [OpenCV](https://opencv.org): Open source computer vision library.

## Featured technologies

* [IBM Cloud](https://www.ibm.com/sg-en/cloud/object-storage): Accessing computer and information technology resources through the Internet.
* [Python](https://www.python.org/): Python is a programming language that lets you work more quickly and integrate your systems more effectively.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install the dependencies.


```bash
pip install ibm-cos-sdk==2.0.1 #IBM SDK for Python
pip install os-win 
pip install opencv-python
pip install pytest-shutil
pip install glob2
pip install numpy
```

### Jupyter Notebooks

The code included in this code pattern runs in a Jupyter Notebook. The notebook itself does not require PowerAI or Power Systems (only access to the deployed API). To run the Jupyter Notebook locally, install it using Anaconda.  The installation instructions are [here](https://jupyter.readthedocs.io/en/latest/install.html).


## Dataset

* The video used to for pre-processing can be downloaded from [here](datasets/training_video.mp4)

## Flow

1. Livestream video from server to local machine using credentials
2. Configuration for IBM Cloud Object Storage (API key etc)
3. Local configuration for output - Create or clean the directories
4. Read livestream video from local directory
5. Parse and explode the video file into JPEGs
6. Using frame differencing to detect motion between frames
7. Create and upload new bucket with images to COS

Additional:

1. Get list of buckets in COS

## Sample output

![graph](/pictures/graph.jpg)

After the video has been processed, the frames from the video was reduced and the total disk size was reduced to 5mb, with a reduction from the original video by approximately 97%.
