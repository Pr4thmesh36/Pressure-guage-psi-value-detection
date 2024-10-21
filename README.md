# Pressure-guage-psi-value-detection
## Project Overview
We are conducting this project using Google Colab, which is excellent for training deep learning models. Let’s go through the process step by step.

### Step 1: Video Collection and Annotation
First, you will need a video of a pressure gauge where the dial shows varying pressure values. This video will be used for training the model. If you're working on a different object detection task, you can still follow these steps to create your own object detection project.

Once you have the video of the moving pressure gauge, the next step is to annotate it. You can use any annotation software of your choice. I used CVAT (https://www.cvat.ai/) for annotating my frames. There are many YouTube tutorials that can help you learn how to annotate images. In my case, I used the tracking feature in CVAT since the needle of the pressure gauge was in motion. After completing the annotations, save the task and export the annotations in the format required for your model. Since I am using the YOLOv5 model, I exported the annotations in YOLO format.

At this stage, you will have the annotations, but you will also need the images. CVAT does not provide the images automatically, so we will extract them from the video using Python. We’ll generate frames from the video and assign the corresponding annotated labels to them. You can find the code for this in the dataset folder. If you want to download the images and labels directly, here is the Drive link (https://drive.google.com/drive/folders/1GLFnby4-jpCBB69yiaDMQfJlMTDgmS2D?usp=sharing).

Note: Be sure to set the correct folder paths in your environment. Once you have the images and annotations, you'll need to create a .yaml file that specifies the paths for the images and labels. I’ve provided an example of this file, data.yaml, which you can customize for your environment, whether you're training the model on your local system or on Google Colab. You can find a reference to the data.yaml file in the dataset Drive link.

Important: I have not applied any data augmentation (like changing the image size or angle) because the angle plays a crucial role in predicting the pressure values in my model.

### Step 2: Model Training
Now that we have the dataset ready, we can proceed with training the model. First, ensure that all basic requirements are met by downloading the YOLOv5 model. You can either download it directly from GitHub or run the following command to clone the repository:!git clone https://github.com/ultralytics/yolov5.git

The model will be downloaded to your current working directory. After downloading, you can explore the model’s folder, which contains some pre-loaded datasets like COCO, ImageNet, Objects365, and many more. The code works through various Python scripts like detect.py, train.py, and val.py, which handle different aspects of the model.

Also, check out the requirements.txt file in the YOLOv5 directory—it lists all the necessary packages that need to be installed. In the main code, I have added comments to guide you through training the model step by step.

#### Note: Before running the model in Colab, make sure to switch to the T4 GPU by changing the runtime settings. The comments in the code will provide further instructions on how to execute the training In that way it will be easy for executing code.
This is a single image how model in performing for a complete video you can access this link (https://drive.google.com/file/d/1fdpqELugzsN6cCYHKKNTUj0b-SQ9uZnd/view?usp=sharing)
![image](https://github.com/user-attachments/assets/e99c450d-7469-4c1f-b6db-259531c8b169)
These are some of the model training results 
![labels](https://github.com/user-attachments/assets/1d10c634-54e1-431b-8be6-4f6aeb025c1b)
![labels_correlogram](https://github.com/user-attachments/assets/c4e1fcad-a2d6-424c-a69f-9774b671d275)
![train_batch0](https://github.com/user-attachments/assets/bdf5ee60-5902-4c1a-afed-a0544caec0d6)
![image](https://github.com/user-attachments/assets/968cc783-9f49-4909-8f17-9efe4dfbdbbb)
![image](https://github.com/user-attachments/assets/d1b291e1-733b-418b-8091-60bf2f3bf3c6)
![image](https://github.com/user-attachments/assets/97bc8a50-919c-4c8d-a666-963b60135b70)







