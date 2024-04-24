# Raspberry

Alvaroxx1

### Index

---

1. [Instalation Process](#Instalation-Process)
2. [Raspberry Camera](#Raspberry-Camera)
3. [Nano Editor](#Nano-Editor)
4. [Reference](#Reference)


### Instalation Process

---

#### Download & Connection

1. **Download os**
2. **Download Raspberry Pi Imager**

* Set Raspberry Version - OS - Target Device
* Apply OS Customization: 
    * Set user, password and activate ssh

4. **Connection with PuTTy**

* Activate Host Name `raspberrypi.local`
* Insert Username and password
* `sudo raspi-config`
* `Interface Options` -> `VNC` -> `Yes`

5. **Connection with SSH**
* `ssh pi@<raspberry_ip>`

6. **Connection with VNC**
* Set IP Adress
* Set Username & Password
* 
### Raspberry Camera

---

**Check USB Camera**

* `sudo apt update && sudo apt upgrade`
* Video4Linux `sudo apt install v4l-utils`
* List Devices `v4l2-ctl --list-devices1`
* Find Supports of Camera Resolution `v4l2-ctl -d /dev/video0 --list-formats-ext`

**Capture Image**

* `sudo apt install fswebcam`
* Capture Image `fswebcam --no-banner -r {resolution} {image name}`
    * fswebcam --no-banner -r 1280x720 Desktop/image1.jpg

**Video Streaming**
* `pip3 install opencv-contrib-python --break-system-packages`
* Create a python file `nano video_streaming.py`

```python=
import cv2
# camera_index is the video device number of the camera

camera_index = 0
cam = cv2.VideoCapture(camera_index)
while True:
    ret,image = cam.read()
    cv2.imshow('Image_test',image)
    k = cv2.waikey(1)
    if k != -1:
        break
cam.release()
cv2.destroyAllWindows()
```
* `ctrl+xy`
* Set up environment variable `export QT_QPA_PLATFORM=xcb`
* Make an executable file`chmod +x  {file name}”`
    * `chmod +x  video_streaming.py`
* Run `python3 file_name`


### Nano Editor

---

* Write File `ctrl+v`
* Paste `ctrl+shift+v`
* Save `ctrl+s`
* Delete All `ctrl+shift+K`
* Select All Text 
    * Jump at the beginning `ctrl+\`
    * Set a mark `ctrl+6`
    * Jump at the end `alt+/`


### Reference

---
* NTUST - Multimedia Course - Prof.黃琴雅
* HackMD Tutorial [Link](https://hackmd.io/c/tutorials/%2Fs%2Ftutorials)
