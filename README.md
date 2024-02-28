# Arabic Sign Language Real-Time Detection
* Train model.ipynb -> collect data and training Model
* gp_model.h5 -> model weights
* https://drive.google.com/drive/folders/1J5CWTA_B05RPQFzJnR-EH9VNCaKGAw88 -> Data collected
* Sign language detiction.ipynb -> deploy model
-----------------------------------------------------------------------------------------------
## 1. Data collection and processing :-
* Due to the shortage of Arabic real time prediction datasets, i have collected my own data-set for the training and testing of deep learning model in the following way:
* * 1.	creat a folder for the dataset using: os.path.join ('data_folder_name') method

* * 2.	define an array of 25 gestures that will be used to train our model for recognition.:
  (["اهلا" ,"اراك-احقا", "انا" ,"ابي" ,"امي", "نعم" ,"لا", "مساعدة" ,"من فضلك" ,"شكرا-لك", "اريد" ,"ماذا" ,"كلب" ,"قطة", "تكرارا" ,"طعام" ,"حليب", "المزيد" ,"ذاهب-الي" ,"الحمام" ,"بخير" ,"مثل" ,"يتعلم", "اشارة", "انتهي")]

* * * ![image](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/94193fde-fc7a-4ffc-9075-1297f75c35d6)

* * 3.	define the number of videos (200) to collect and the number of frames (30) for each video to be captured

* * 4.	After done with creation of the gesture folder, the next step is collection of data in folders-A loop is then run to create the 200 video folders for each of the gestures
       
* * * ![image](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/08586afe-6e25-4c12-8fd5-835fdc905f83)

* * 5.	The next step is to collect the video data for each gesture and use the extract_keypoints function to collect the array of key points for each frame. Finally the numpy array of key points collected is saved for each frame inside each video folder as shown in the Figure 4 below, in the figure it shows till 10.npy it actually goes till 29.npy.
  
* * * ![image](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/c1d1b0db-bf28-4426-8231-b2d9c3e7741b)

## 2. Hand Detection using Mediapipe Holistic model :-
* Mediapipe as itself offers a wide range of solutions, within the holistic pipeline of mediapipe, it consists of three components: pose, hand and face. 
* The holistic model extracts a sum of 543 individual landmarks (468- face, 33- pose and 21- hand)
* using Mediapipe holistic model included in mediapipe python module.
* While useing the holistic model and extracted key points for all three: hand, face and pose, we only showed hand landmarks
* ![image](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/429b4bfb-297b-47a7-a008-756b09680af6)

## 3.Data Preparation and Label Creation :-
* After the data collection process is complete, the key points extracted from the data is then structured using data preprocessing, the Data is structured such a way that all the arrays of key points of each gesture is saved as one numpy array (X) which is then mapped to another numpy array of labels(Y).
* then use the to_categorical function to convert Y into a binary class matrix e.g. [1,0,0….] represents"  اهلا," [0,1,0,0….] represents"   "شكرا and [0,0,1,0,0,.....] represents “احبك” and so on. After the preprocessing is complete the data is then split into training and testing data using train_test_split function

## 4.The lstm model implementation:-
* Long short term memory (LSTM) is a variation of RNN which is mainly used for sequence of data or data in time-series. The LSTM unit is more complex than a RNN unit. It has gates that control the flow of information from an individual unit.
* ![image](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/e41c3641-545c-45e7-be6a-ffc496cd8283)

## Some screenshots for data collecting 
* ![Untitled](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/fe3be206-8aeb-4a01-a08b-8f2ddff516fc)

## Model Summary
* ![gp_model](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/26550be5-0ba2-4325-806a-23ecb0c5112f)
* Test accuracy is → 85% 
* Training accuracy is → 96%
  
## Model Test in real live
* ![Untitled](https://github.com/MarwanAhmed20/Arabic-Sign-Language-Real-Time-Detection/assets/47067493/9849dda6-128b-42e7-8318-8fb6cf631488)


# Libraries used
* openCV
* Tensorflow
* Mediapipe
* arabic_reshaper 




