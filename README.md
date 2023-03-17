# Driver-Drowsiness-Detection
Implemented a real-time drowsiness detection system using a computer's webcam. The system detects a person's facial landmarks, particularly their eyes, and calculates the eye aspect ratio (EAR) to determine whether the person is drowsy or not. If the person's eyes are closed for a certain period of time, an alarm sound will be played.

Each eye is represented by 6 (x,y) coordinates, starting at the left corner of the eye (if you are looking at the person), and working clockwise around the eye. 
It checks 20 consecutive frames, and if eye aspect ratio of at most 0.25 is detected, an alarm is triggered using playsound library.  


The project uses several Python libraries, including:

scipy: for calculating the Euclidean distance between eye landmarks.
imutils: for working with OpenCV and dlib.
numpy: for numerical operations on arrays.
PIL: for working with images in Python.
io: for working with input/output streams.
cv2: for computer vision and image processing.
dlib: for face detection and landmark recognition.
base64: for encoding and decoding binary data.
threading: for running the alarm sound in a separate thread.
argparse: for parsing command-line arguments.
playsound: for playing the alarm sound.


Here, several functions have been defined:

eye_aspect_ratio: Calculates the EAR using the Euclidean distance between the eye landmarks.
![image](https://user-images.githubusercontent.com/36480901/226058681-0442c355-f199-414f-8d61-cfae0d3f3356.png)

**EAR = ||p2-p6||-||p3-p5||/2*||p1-p4||**

sound_alarm: Plays an alarm sound using the playsound library.

js_to_image: Converts a JavaScript object containing an image from the webcam into an OpenCV BGR image.

bbox_to_bytes: Converts an OpenCV rectangle bounding box image into a base64 byte string that can be overlayed on the video stream.

video_stream: Defines a JavaScript function that creates a video stream using the webcam.

The main implementation of the drowsiness detection system starts by setting a threshold of 0.25 and a frame check of 20. 
The threshold is the minimum EAR value that indicates a person is drowsy, while the frame check is the number of frames to check before determining whether the person is drowsy. 
The detect and predict objects are initialized using the dlib library to detect faces and facial landmarks.

The left and right eye landmarks are then identified using the face_utils library, and a video stream is created using the webcam. 
The stream is then looped over continuously to detect the person's eyes and calculate the EAR. 
If the EAR falls below the threshold of 0.25, the person's eyes are closed for 20 frames, and an alarm sound is played using the sound_alarm function.

The video stream is created using a JavaScript function that creates a video element, captures video from the user's webcam, and returns a Promise object that resolves with the captured image. 
The Promise object is then used to display the video stream and the overlayed bounding box on the video stream.

Overall, the code uses a combination of Python and JavaScript to implement a real-time drowsiness detection system using a computer's webcam.

