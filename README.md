# Pressure-guage-psi-value-detection
Project Overview
We are conducting this project using Google Colab, which is excellent for training deep learning models. Let’s go through the process step by step.

Step 1: Video Collection and Annotation
First, you will need a video of a pressure gauge where the dial shows varying pressure values. This video will be used for training the model. If you're working on a different object detection task, you can still follow these steps to create your own object detection project.

Once you have the video of the moving pressure gauge, the next step is to annotate it. You can use any annotation software of your choice. I used CVAT for annotating my frames. There are many YouTube tutorials that can help you learn how to annotate images. In my case, I used the tracking feature in CVAT since the needle of the pressure gauge was in motion. After completing the annotations, save the task and export the annotations in the format required for your model. Since I am using the YOLOv5 model, I exported the annotations in YOLO format.

At this stage, you will have the annotations, but you will also need the images. CVAT does not provide the images automatically, so we will extract them from the video using Python. We’ll generate frames from the video and assign the corresponding annotated labels to them. You can find the code for this in the dataset folder. If you want to download the images and labels directly, here is the Drive link.

Note: Be sure to set the correct folder paths in your environment. Once you have the images and annotations, you'll need to create a .yaml file that specifies the paths for the images and labels. I’ve provided an example of this file, data.yaml, which you can customize for your environment, whether you're training the model on your local system or on Google Colab. You can find a reference to the data.yaml file in the dataset Drive link.

Important: I have not applied any data augmentation (like changing the image size or angle) because the angle plays a crucial role in predicting the pressure values in my model.

Step 2: Model Training
Now that we have the dataset ready, we can proceed with training the model. First, ensure that all basic requirements are met by downloading the YOLOv5 model. You can either download it directly from GitHub or run the following command to clone the repository:
