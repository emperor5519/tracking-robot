# tracking-robot
- 사람의 얼굴을 인식하고, 카메라 화면의 중앙에 얼굴이 위치하도록 지속적으로 추적하는 로봇으로 1인 촬영욜 장비 입니다.  

- 메카넘 휠을 사용한 4륜 로봇으로 원하는 방향으로 원활하게 이동이 가능하고, 짐벌에 핸드폰을 거치하여 촬영할 수 있도록 하였습니다.  

- NVIDIA의 Jetson Nano 보드와 Arduino Uno 보드를 이용하였고, ROS Melodic을 사용하였으며, 인터넷이 연결되지 않은 환경에서 두 보드간 통신이 가능하도록 ROS-Serial통신을 하였습니다.  

- Jetson Nano에서는 python, Arduino Uno에서는 C 언어를 이용해 작성하였고, Jetson Nano가 publisher 노드, Arduino Uno가 subscriber 노드로 동작합니다.  

### 

# 블럭도
<img src="/img/블럭도.png" width="600" height="400">  

- Jetson Nano에 연결된 USB카메라로부터 영상을 수신합니다.
- Ubuntu 18.04(Bionic)의 python스크립트에서 OpenCV 라이브러리와 Haar Cascades알고리즘을 이용해 카메라 영상에서 사람의 얼굴을 인식합니다.
- 인식된 얼굴의 중심 좌표의 위치에 따라 로봇이 움직여야 할 방향을 계산하고, 계산된 값에 따라 앞, 뒤, 좌, 우, 회전 등의 문자열을 설정된 topic으로 publish합니다.
- ROS-Serial통신으로 연결된 Arduino Uno에서 설정된 topic으로 문자열 값을 subscribe하여 4개의 DC모터의 방향이 제어됩니다.

### 

# 기능 설명
## 1. 얼굴 검출기능 ##  
<img src="/img/얼굴검출기능.png" width="400" height="300">  

- Jetson Nano에 연결된 USB카메라로부터 영상을 수신합니다.  
- Ubuntu 18.04 LTS(Bionic)의 python 스크립트에서 OpenCV 라이브러리와 Haar Cascades 알고리즘을 이용해 카메라 영상에서 사람의 얼굴을 검출합니다.  
- 인식된 얼굴의 중심 좌표의 위치에 따라 로봇이 움직여야 할 방향을 계산합니다.  

### 

## 2. ROS 통신기능 ##  
<img src="/img/연결사진.png" width="600" height="300">  

- ROS Melodic을 사용하였으며, 인터넷이 연결되지 않은 환경에서 두 보드간 통신이 가능하도록 ROS-Serial통신을 하였습니다.  
- ROS master 노드

### 

<img src="/img/ROS_pub.png" width="600" height="300">  

- python 스크립트에서 계산된 값에 따라 "left", "right" 등의 문자열을, topic을 설정하고 publish합니다.  

### 

<img src="/img/ROS_sub.png" width="600" height="300">  

- 설정된 topic으로 Arduino Uno에서 문자열 값을 subscribe합니다.  

### 

## 3. 모터 제어기능 ##  
<img src="/img/전체사진1.png" width="600" height="300">  
<img src="/img/전체사진2.png" width="600" height="300">  

- ROS-Serial통신으로 연결된 Arduino Uno에서 subscribe한 문자열 값에 따라 4개의 DC모터의 방향이 제어됩니다.  

### 

<img src="/img/내부사진.png" width="400" height="300">  

- 모터 드라이버(L298N) 2개를 사용하였고, 모터 드라이버 1개당 DC모터 2개와 배터리(1.5V 병렬연결)가 연결되어 모터의 방향이 제어됩니다.  
### 

<img src="/img/메카넘휠원리.png" width="400" height="300">  

- 위의 사진과 같이 모터의 방향이 제어되며 메카넘 휠을 이용해 원하는 방향으로 로봇이 제어됩니다.  

### 

# 동영상 링크(이미지를 클릭하면 유튜브 영상으로 이동합니다) #
[![Video Label](https://github.com/emperor5519/AR-instrument/blob/main/img/%EC%9C%A0%ED%8A%9C%EB%B8%8C%EC%8D%B8%EB%84%A4%EC%9D%BC.png)](https://www.youtube.com/watch?v=4u47xhIxIt0&ab_channel=%EC%B5%9C%EC%8A%B9%ED%98%B8)

사람인 이력서에도 동영상이 첨부되어 있습니다  
