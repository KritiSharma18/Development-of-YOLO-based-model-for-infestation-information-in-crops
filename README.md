\# Development of YOLO-Based Models for Infestation Information in Crops



\## Overview



This repository contains the work for a BTP project on using deep learning and computer vision for crop disease and infestation detection. The project was carried out in two parts: BTP-I on maize leaf disease detection, and BTP-II on potato leaf disease detection, both under the supervision of Professor Damodhara Rao Mailapalli, Department of Agricultural and Food Engineering, IIT Kharagpur. Both models were built for integration with the IITea Android application.



\## Objectives



\- Develop deep learning models for crop disease and infestation detection.

\- Train and evaluate YOLO-based models for real time field deployment.

\- Compare different model families (detection, segmentation, classification) on the same dataset and conditions.

\- Study the use of computer vision for automated crop health monitoring through the IITea app.



\## Crops



\### Maize (BTP-I)



Four classes: Blight, Common Rust, Gray Leaf Spot, and Healthy. Four architectures were trained and compared: YOLOv11, Detectron2, InceptionV3, and CNN.



\### Potato (BTP-II)



Two classes: Early Blight and Late Blight. Five architectures were trained and compared: YOLOv11, YOLOv8, SSD, Detectron2, and InceptionV3.



\## Models and Results



Results below are from the BTP reports. These are the actual reported metrics, not projected or estimated values.



\### Maize



| Model | Metric | Value |

|---|---|---|

| YOLOv11 | mAP@50 | 86.6% |

| Detectron2 | mAP@50 | 79% |

| InceptionV3 | Validation accuracy | 69.64% |

| CNN | Validation accuracy | 55% |



YOLOv11 was selected as the best performing model for maize, with stable convergence and reliable detection under cluttered backgrounds and uneven lighting. It struggled with very small or low-contrast lesions.



\### Potato



| Model | mAP@50 | Precision | Recall | F1-score |

|---|---|---|---|---|

| YOLOv11 | 0.930 | 0.922 | 0.945 | 0.91 |

| YOLOv8n | 0.807 | 0.900 | 0.851 | 0.875 |

| SSD | 0.784 | - | 1.000 | 0.879 |

| InceptionV3 | - (79.01% accuracy) | - | - | 0.91 |

| Detectron2 | 0.679 | - | - | - |



YOLOv11 was selected as the primary model for potato disease detection, offering the best balance of accuracy and inference speed (\~5.2 ms per image, \~190 FPS, 19.2 MB model size), and was deployed in the IITea Android application for real time early blight and late blight detection.



\## Methodology



The general workflow followed for both crops:



Image Dataset

&#x20;     |

&#x20;     v

Annotation (Roboflow)

&#x20;     |

&#x20;     v

Preprocessing and Augmentation

&#x20;     |

&#x20;     v

Train / Validation / Test Split

&#x20;     |

&#x20;     v

Model Training

&#x20;     |

&#x20;     v

Model Evaluation and Comparison

&#x20;     |

&#x20;     v

Deployment (ONNX / TFLite, IITea app)



\## Repository Structure



Btp/

|

|-- maize/

|   |-- Maize dataset and BTP-I experiments (YOLOv11, Detectron2, InceptionV3, CNN)

|

|-- potato/

|   |-- potato\_dataset/

|   |   |-- Healthy/

|   |   |-- Late\_Blight/

|   |

|   |-- models/

|   |   |-- btp2\_potato\_inception.ipynb

|   |   |-- btp2\_yolov11.ipynb

|   |   |-- potato\_detectron\_v2.ipynb

|   |

|   |-- BTP-II experiments (YOLOv11, YOLOv8, SSD, Detectron2, InceptionV3)

|

|-- README.md

|-- .gitignore



\## Technologies Used



\- Python

\- PyTorch

\- TensorFlow / TensorFlow Lite

\- Ultralytics YOLO (v8, v11)

\- Detectron2

\- OpenCV

\- Roboflow (annotation and augmentation)

\- NumPy, Pandas, Scikit-learn

\- Jupyter Notebook / Google Colab

\- ONNX (mobile deployment)



\## Deployment



The YOLOv11 model was converted to TensorFlow Lite and integrated into the IITea Android application, enabling on-device disease detection from camera images without needing constant cloud access.



\## Limitations



Both studies were limited to RGB imagery from datasets that lacked broad geographic and climatic diversity. Neither study estimated disease severity or lesion area, and real field testing was limited by restricted crop access during data collection. Details are in the respective BTP reports.



\## Author



Kriti Sharma

