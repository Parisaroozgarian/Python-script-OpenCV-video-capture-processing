# Python script / OpenCV video capture & processing

import cv2
This line imports the OpenCV library, which is a popular computer vision library in Python.
Open Video Capture:
python
Copy code
cap = cv2.VideoCapture(0)
This line creates a VideoCapture object (cap) that is used to capture video frames. The argument 0 represents the default camera (usually the built-in webcam). If you have multiple cameras, you can specify the camera index accordingly (e.g., 1 for an external camera).
Set Video Writer Properties:
python
Copy code
fourcc = cv2.VideoWriter_fourcc(*'XVID')
out = cv2.VideoWriter('output.avi', fourcc, 20.0, (640, 480))
These lines set up a VideoWriter object (out) to save the captured frames into a video file. The codec used is XVID, and the output file is named 'output.avi'. The frame rate is set to 20 frames per second, and the frame size is specified as (640, 480) pixels.
Capture and Process Frames in a Loop:
python
Copy code
while cap.isOpened():
    ret, frame = cap.read()
This loop continuously captures frames from the camera using cap.read(). The function returns two values: ret (a boolean indicating if the frame was successfully read) and frame (the actual frame).
Check if Frame is Read Successfully:
python
Copy code
if ret:
This condition checks if the frame was read successfully. If ret is True, it means the frame is valid.
Print Frame Width and Height:
python
Copy code
print(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
print(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
These lines print the width and height of the captured frame using the CAP_PROP_FRAME_WIDTH and CAP_PROP_FRAME_HEIGHT properties.
Write Frame to Video File:
python
Copy code
out.write(frame)
This line writes the current frame to the output video file.
Convert Frame to Grayscale:
python
Copy code
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
This line converts the BGR (color) frame to grayscale using the cv2.cvtColor function.
Display Grayscale Frame:
python
Copy code
cv2.imshow('frame', gray)
This line displays the grayscale frame in a window with the title 'frame'.
Check for 'q' Key Press:
python
Copy code
if cv2.waitKey(1) & 0xFF == ord('q'):
    break
This condition checks if the 'q' key is pressed. If so, it breaks out of the loop.
Release Capture and Writer Objects:
python
Copy code
cap.release()
out.release()
These lines release the resources associated with the VideoCapture and VideoWriter objects.
Close OpenCV Windows:
python
Copy code
cv2.destroyAllWindows()
This line closes all OpenCV windows, ensuring that the program exits cleanly.
