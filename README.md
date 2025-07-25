# video-tracking-with-opencv
******Key Achievements******

- Developed a multi-approach pipeline for object tracking in tennis videos using OpenCV, TensorFlow, and YOLOv5
- Implemented ball tracking using HSV color filtering and contour-based ellipse fitting
- Integrated TensorFlow’s SSD MobileNet model to detect and track ball movement frame-by-frame
- Applied YOLOv5 object detection with optional CSRT tracking for smoother, more persistent tracking across frames
- Handled video input, live frame display, and real-time annotation using cv2 and Google Colab utilities
- Enabled automatic video saving and export for post-processing or visualization

1. HSV Color Filtering with OpenCV
The first approach relies on the fact that tennis balls are usually bright yellow-green. Each video frame is converted to the HSV color space, and a mask is applied to isolate pixels within a specific color range. After that:
  Contours are detected in the mask.
  Circles or ellipses are drawn around those contours to show the position of the ball.
This method is simple and fast but doesn’t always work well in poor lighting or with distracting backgrounds.

3. Object Detection with TensorFlow (SSD MobileNet)
The second approach uses a pre-trained object detection model from TensorFlow's Model Zoo. It detects general objects, including sports balls. Here’s how it works:
  Each frame is passed through the SSD MobileNet model.
  The model returns bounding boxes for detected objects.
  The box labeled “sports ball” is highlighted.
This approach is more robust than color filtering but occasionally misses the ball if it’s small or blurry.

3. YOLOv5 + Tracking
The final version uses YOLOv5 (a fast and accurate object detector) combined with a CSRT tracker:
  YOLO detects the ball every few frames.
  In between detections, the CSRT tracker keeps following the object’s movement.
  Bounding boxes and labels are drawn throughout the video.
This method balances speed and accuracy, and it's more reliable in dynamic scenes where the ball changes shape or moves quickly.
