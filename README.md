# final-year-project
Driver Alert System while driver is driving a vehicle when he feel sleepy it alert the system:
Requriments:    The requirement for this Python project is a webcam through which we will capture images. You need to have Python (3.6 version recommended) installed on your system, then using pip, you can install the necessary packages.

    OpenCV – pip install opencv-python (face and eye detection).
    TensorFlow – pip install tensorflow (keras uses TensorFlow as backend).
    Keras – pip install keras (to build our classification model).
    Pygame – pip install pygame (to play alarm sound).
Files Consists:
      The “haar cascade files” folder consists of the xml files that are needed to detect objects from the image. In our case, we are detecting the face and eyes of the person.
      1.The models folder contains our model file “cnnCat2.h5” which was trained on convolutional neural networks.
      2.We have an audio clip “alarm.wav” which is played when the person is feeling drowsy.
      3.“Model.py” file contains the program through which we built our classification model by training on our dataset. You could see the       4.implementation of convolutional neural network in this file.
      5.“DriverAlert.py” is the main file of our project. To start the detection procedure, we have to run this file
To know more about CNN-https://medium.com/technologymadeeasy/the-best-explanation-of-convolutional-neural-networks-on-the-internet-fbb8b1ad5df8
Working Procedure:
               Step 1 – Take image as input from a camera:
                      This can be done by using opencv module by using method cv2.videocaputure()
               
               Step 2 – Detect the face in the image and create a Region of Interest (ROI).
                      To detect the face in the image, we need to first convert the image into grayscale as the OpenCV algorithm for object detection takes gray images in the input. We don’t need color information to detect the objects. We will be using haar cascade classifier to detect faces.
               
               Step 3 – Detect the eyes from ROI and feed it to the classifier.
                      The same procedure to detect faces is used to detect eyes. First, we set the cascade classifier for eyes in leye and reye respectively then detect the eyes
               
               Step 4 – Classifier will categorize whether eyes are open or closed.
                      We are using CNN classifier for predicting the eye status. To feed our image into the model, we need to perform certain operations because the model needs the correct dimensions to start with
               
               Step 5 – Calculate score to check whether the person is drowsy.
                      The score is basically a value we will use to determine how long the person has closed his eyes. So if both eyes are closed, we will keep on increasing score and when eyes are open, we decrease the score. We are drawing the result on the screen using cv2.putText() function which will display real time status of the person.
CONCLUSION:
        A threshold is defined for example if score becomes greater than 15 that means the person’s eyes are closed for a long period of time. This is when we beep the alarm using sound.play()

