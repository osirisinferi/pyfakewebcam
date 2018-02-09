# pyfakewebcam

An API for writing RGB frames to a fake webcam device on Linux!

## installation

```
git clone https://github.com/jremmons/pyfakewebcam.git
cd pyfakewebcam
sudo python setup.py install
```
 
## usage 

```python
# see red_blue.py in the examples dir
import time
import pyfakewebcam
import numpy as np

blue = np.zeros((480,640,3), dtype=np.uint8)
blue[:,:,2] = 255

red = np.zeros((480,640,3), dtype=np.uint8)
red[:,:,0] = 255

camera = pyfakewebcam.FakeWebcam('/dev/video1', 640, 480)

while True:

    camera.schedule_frame(red)
    time.sleep(1/1)

    camera.schedule_frame(blue)
    time.sleep(1/1)
```

Run the following command to see the output of the fake webcam.
```
ffplay /dev/video1
```
