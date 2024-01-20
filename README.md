# Python script / OpenCV video capture & processing

1. **Import OpenCV Library:**
   ```python
   import cv2
   ```
   This line imports the OpenCV library, which is commonly used for computer vision tasks in Python.

2. **Open Video Capture:**
   ```python
   cap = cv2.VideoCapture(0)
   ```
   This line creates a `VideoCapture` object (`cap`) to access the default camera (camera index 0). If you have multiple cameras, you can specify a different index.

3. **Set Video Writer Properties:**
   ```python
   fourcc = cv2.VideoWriter_fourcc(*'XVID')
   out = cv2.VideoWriter('output.avi', fourcc, 20.0, (640, 480))
   ```
   These lines set up a `VideoWriter` object (`out`) to save the captured frames into a video file named 'output.avi'. The codec used is XVID, the frame rate is set to 20 frames per second, and the frame size is specified as (640, 480) pixels.

4. **Capture and Process Frames in a Loop:**
   ```python
   while cap.isOpened():
       ret, frame = cap.read()
   ```
   This loop continuously captures frames from the camera using `cap.read()`. The function returns two values: `ret` (a boolean indicating if the frame was successfully read) and `frame` (the actual frame).

5. **Check if Frame is Read Successfully:**
   ```python
   if ret:
   ```
   This condition checks if the frame was read successfully. If `ret` is `True`, it means the frame is valid.

6. **Print Frame Width and Height:**
   ```python
   print(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
   print(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
   ```
   These lines print the width and height of the captured frame using the `CAP_PROP_FRAME_WIDTH` and `CAP_PROP_FRAME_HEIGHT` properties.

7. **Write Frame to Video File:**
   ```python
   out.write(frame)
   ```
   This line writes the current frame to the output video file.

8. **Convert Frame to Grayscale:**
   ```python
   gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
   ```
   This line converts the BGR (color) frame to grayscale using the `cv2.cvtColor` function.

9. **Display Grayscale Frame:**
   ```python
   cv2.imshow('frame', gray)
   ```
   This line displays the grayscale frame in a window with the title 'frame'.

10. **Check for 'q' Key Press:**
    ```python
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
    ```
    This condition checks if the 'q' key is pressed. If so, it breaks out of the loop.

11. **Release Capture and Writer Objects:**
    ```python
    cap.release()
    out.release()
    ```
    These lines release the resources associated with the `VideoCapture` and `VideoWriter` objects.

12. **Close OpenCV Windows:**
    ```python
    cv2.destroyAllWindows()
    ```
    This line closes all OpenCV windows, ensuring that the program exits cleanly.

This code captures video from the default camera, prints the width and height of each frame, saves the frames to a video file, converts each frame to grayscale, and displays the grayscale frames in a window. The loop continues until the 'q' key is pressed, and then it releases resources and closes windows.

