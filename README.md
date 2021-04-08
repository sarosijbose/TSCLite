# TSCLite: A powerful and lightweight Traffic Sign Classification model Implementation

*Contributors: [Avirup Dey](https://www.linkedin.com/in/avirup-dey-4213a81ab/) (Jadavpur University) and [Sarosij Bose](https://www.linkedin.com/in/sarosijbose/) (University of Calcutta).*


## Short Description:-
This repository contains two lightweight Traffic sign classification implementations which can predict Traffic signs from any real time video feed. Here, a model based on an slightly enhanced LeNet architecture has been used and trained on the [German Traffic Sign Dataset (GTSD)](https://benchmark.ini.rub.de/gtsrb_dataset.html) which has over 70000 images of traffic signs and over 40 various classes. Our model achieves a validation accuracy of over 98% and a training accuracy of over 97%. This saved model is then optimized over the [Intel OpenVINO](https://docs.openvinotoolkit.org/latest/index.html#index) Model Optimizer + Inference Engine and run directly for predicting Traffic signs live from any video source(we have used webcam for our run). We have also provided a non optimized solution for comparison purposes.

To learn more about the features which our model offers, it's advantages and how it can be socially useful in a number of applications, see [Project Details](https://github.com/sarobml2000/TSCLite/blob/main/TSC%20Lite.docx)

## Demo Illustrations:-
 <img src = "https://github.com/sarobml2000/TSCLite/blob/main/sample%20output/ss1.jpg">
 
 <img src = "https://github.com/sarobml2000/TSCLite/blob/main/sample%20output/ss2.jpg">
 
 <img src = "https://github.com/sarobml2000/TSCLite/blob/main/sample%20output/vid.gif">

## Environment requirements:-
Please see the [requirements.py](https://github.com/sarobml2000/TSCLite/blob/main/requirements.py) file to know and install the necessary libraries.

## Project Setup:-
### 1. Getting started.
Download and install the [OpenVINO toolkit](https://software.intel.com/content/www/us/en/develop/tools/openvino-toolkit/download.html) from Intel's website according to your operating system. 

### 2. Clone the repository.
```
git clone https://github.com/sarobml2000/TSCLite.git
```
### 3. Generating the model.
Run the notebook as given below. The created tsc_model.h5 file will be used later for prediction.
```
cd TSCLite\code
jupyter notebook TSC_Tensorflow.ipynb
```
The compiled model(in .h5 format) is avaliable within the dependencies folder.
```
cd TSCLite\dependencies
```
### 4. Running the notebook with OpenVINO support.
Copy the labels.csv file into the working directory from the dependencies folder. 
Run the notebook. 
```
cd TSCLite\code
jupyter notebook TSC_OpenVINO.ipynb
```
After converting the model to ONNX format, run the following commands in windows terminal.  
*Initialize OpenVINO environment variables.*
```
path to openvino\bin\setupvars.bat
```
For linux based systems, use this.
```
cd path to openvino/bin
source ./setupvars.sh
```

*Generate the .xml and .bin files by running the Inference engine.*
```
path to openvino\deployment_tools\model_optimizer\mo.py --input_model <path to model.onnx> --input_shape[1,32,32,1]
```
Once the .xml and .bin files are created, cd them to your working directory and run the rest of the code.
These are also provided inside the external folder.
```
cd TSCLite\external
```
### 5. Running the notebook without OpenVINO support. (Optional)
Copy the labels.csv file into the working directory from the dependencies folder. 
Run the notebook.
```
cd TSCLite\code
jupyter notebook TSC_without_OpenVINO.ipynb
```
## Model Performance:-
Reduced the number of training epochs to achieve standard results. We repeatedly tweaked the model until attaining optimum results.
Here's the loss and accuracy plotted against the number of epochs.<br>

<img src ="https://github.com/sarobml2000/TSCLite/blob/main/sample%20output/loss.jpg" height = "350px" width = "350px">

<img src ="https://github.com/sarobml2000/TSCLite/blob/main/sample%20output/acc.jpg" height = "350px" width = "350px">

## Hardware used:-
The project was carried out with the following system specifications,  
OS: Windows 10 64 bit Home.  
CPU: Intel i5 8th Generation.  
RAM: 8 GB  
GPU: No hardware acceleration required for this project.  
## Contact:-
Mail us at avirupju@outlook.com or sarosijbose2000@gmail.com
