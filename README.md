# WildEye
WildEye is a ML-based wildlife monitoring system aimed at promoting harmony between human habitats and forested areas. Cameras strategically placed at the interface between human settlements and forests are used to detect wildlife like elephants and tigers. Detected animals trigger alerts containing time, location, and images, which are sent to nearby devices and wildlife departments. Recent alerts are logged and accessible via dedicated app or web platform. Users can also privately report animal sightings. This project contributes to improving wildlife management and reduce human-wildlife conflicts.
## Implementation
### Back End
The project asssumes there exist multiple IP cameras which are strategically postioned near forest borders. Feed from the cameras are fed into the server. 
Server is a Object oriented python program in which, each cameras are declared as object of `detect` class. 
YOLOv7 model is used for identifying elephants from the camera feed.
Feed from the camera is fed into the python program using RTSP protocol.
`customized_detect.py` is the backend server.
#### Requirements
To run this file, system must have GPU and CUDA installed.
```markdown
python customized_detect.py
```
When elephant is detected,notification alert is send to the android devices through Firebase Cloud Messaging feature. The detection detailed like place,timestamp,cameraID and detected image is logged into the `log` table, which is in our Firebase database. 
### Front End
Front end consists of two apps:
#### User App
Android app which need minimum SDK version of 21. Receives alert, view recent alerts along with detected image. Map screen with cameras marked in it. There is a report chatroom feature in which Admin can broadcast important notices or share information. Users can also raise concerns in it, which will be visible in admin inbox. `User` folder contains the flutter project of user app. Run the command below in cmd to build apk
```markdown 
flutter build apk
```
#### Admin App
This is a web application is handled by respective Authority. Functionalities include receive concerns from public, broadcast alerts, management of cameras and flagging users. Run the command below in the admin folder to launch the application in web browser
```markdown 
flutter run
```
