# Computer Pointer Controller

## Overview
Computer Pointer Controller is an application that uses a gaze detection model to control the mouse pointer using an input video or a live stream from your webcam

## Demo video
[![Demo video]()]()


## Project Set Up and Installation

### Setup 

#### Install Intel® Distribution of OpenVINO™ toolkit
See this [guide](https://docs.openvinotoolkit.org/latest/) for installing openvino.

#### Intsalling pre-trained models

##### First, you have to initialize openVINO Environment 

* For windows:
'''
cd C:\Program Files (x86)\IntelSWTools\openvino\bin\
'''
'''
setupvars.bat
'''

## Documention for downloaded models

	- [Face Detection Model](https://docs.openvinotoolkit.org/latest/_models_intel_face_detection_adas_binary_0001_description_face_detection_adas_binary_0001.html)
	- [Facial Landmarks Detection Model](https://docs.openvinotoolkit.org/latest/_models_intel_landmarks_regression_retail_0009_description_landmarks_regression_retail_0009.html)
	- [Head Pose Estimation Model](https://docs.openvinotoolkit.org/latest/_models_intel_head_pose_estimation_adas_0001_description_head_pose_estimation_adas_0001.html)
	- [Gaze Estimation Model](https://docs.openvinotoolkit.org/latest/_models_intel_gaze_estimation_adas_0002_description_gaze_estimation_adas_0002.html)


* Downloading Models 
for Face Detection Model

'''
python <openvino directory>/deployment_tools/tools/model_downloader/downloader.py --name "face-detection-adas-binary-0001"
'''

for landmarks-regression-retail-0009

'''
python /opt/intel/openvino/deployment_tools/tools/model_downloader/downloader.py --name "landmarks-regression-retail-0009"
'''

for head-pose-estimation-adas-0001

'''
python /opt/intel/openvino/deployment_tools/tools/model_downloader/downloader.py --name "head-pose-estimation-adas-0001"
'''

for gaze-estimation-adas-0002

'''
python /opt/intel/openvino/deployment_tools/tools/model_downloader/downloader.py --name "gaze-estimation-adas-0002"
''''

* Running the app

	- Run on CPU 

'''
python <project_file.py directory> -fd <Face detection model name directory> -fl <Facial landmark detection model name directory> -hp <head pose estimation model name directory> -ge <Gaze estimation model name directory> -i <input video directory> -d CPU
'''

	- Run on GPU 

'''
python <project_file.py directory> -fd <Face detection model name directory> -fl <Facial landmark detection model name directory> -hp <head pose estimation model name directory> -ge <Gaze estimation model name directory> -i <input video directory> -d GPU
'''

	- Run on FPGA 

'''
python <project_file.py directory> -fd <Face detection model name directory> -fl <Facial landmark detection model name directory> -hp <head pose estimation model name directory> -ge <Gaze estimation model name directory> -i <input video directory> -d HETERO:FPGA,CPU
'''


## Benchmarks
* I have Submited three jobs using this script to the DevCloud, using same demo video, but different hardware: 
  * IEI Tank 870-Q170 edge node with an Intel® Core™ i5-6500TE (CPU)
  * IEI Tank 870-Q170 edge node with an Intel® Core™ i5-6500TE (CPU + Integrated Intel® HD Graphics 530 card GPU)
  * IEI Tank 870-Q170 edge node with an Intel® Core™ i5-6500TE, with IEI Mustang-F100-A10 card (Arria 10 FPGA).

* for FP32
  | Type of Hardware | Total inference time in seconds              | Time for loading the model | fps |
  |------------------|----------------------------------------------|----------------------------|------
  | CPU              |  68                                          |  1.5                       |  9  |
  | GPU              |  69                                          |  55                        |  9  |
  | FPGA             |  118                                         |  6                         |  5  |

* for FP16
  | Type of Hardware | Total inference time in seconds              | Time for loading the model | fps |
  |------------------|----------------------------------------------|----------------------------|------
  | CPU              |  77                                          |  1.3                       |  8  |
  | GPU              |  75                                          |  52.4                      |  9  |
  | FPGA             |  125                                         |  4.5                       |  5  |


* for INT8
  | Type of Hardware | Total inference time in seconds              | Time for loading the model | fps |
  |------------------|----------------------------------------------|----------------------------|------
  | CPU              |  79                                          |  1.3                       |  8  |
  | GPU              |  74                                          |  52 .4                     |  9  |
  | FPGA             |  130                                         |  3                         |  5  |

## Results




