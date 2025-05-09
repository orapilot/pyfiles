# opencv with gstreamer

## How to use it?

1. install it via `uv pip install opencv_python_headless-4.10.0.84-cp312-cp312-linux_x86_64.whl`
2. Replace `cv2.VideoCapture(camera_id)` to `cv2.VideoCapture("gst-launch-1.0 v4l2src device=/dev/video" + str(camera_id) + " io-mode=2 ! image/jpeg, width=1920, height=1080, framerate=30/1, format=MJPG ! jpegdec ! videoconvert ! appsink", cv2.CAP_GSTREAMER)`

`jpegdec` can be replaced with hardware acceleration plugins, eg. On rk3588 it's `mppjpegdec`.
