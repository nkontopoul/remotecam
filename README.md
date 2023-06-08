# remotecam
Connect via python 3 to remote cam running on android with IP Webcam App found free in play store
Souce code in python3

import requests
import cv2
import numpy as np
import imutils
url="http://192.168.1.10:8080/shot.jpg"
while True:
    img_resp=requests.get(url)
    img_arr=np.array(bytearray(img_resp.content), dtype=np.uint8)
    img=cv2.imdecode(img_arr,-1)
    img=imutils.resize(img,width=1000,height=1800)
    cv2.imshow("Camera feed", img)
    if cv2.waitKey(1)==27:
        break
cv2.destroyAllWindows()
