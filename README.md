# tracking-robot
<img src="/img/실행화면.png" width="600" height="450">

사람의 얼굴을 인식하고, 카메라 화면의 중앙에 얼굴이 위치하도록 지속적으로 추적하는 로봇으로 1인 촬영욜 장비 입니다.  
메카넘 휠을 사용한 4륜 로봇으로 원하는 방향으로 원활하게 이동이 가능합니다.  
NVIDIA의 Jetson Nano 보드와 Arduino Uno 보드를 이용하였고, ROS Melodic을 사용하였으며, 인터넷이 연결되지 않은 환경에서 두 보드간 통신이 가능하도록 ROS-Serial 통신을 하였습니다.  


### 

## 기능 설명
**얼굴 검출 및 
<img src="/img/손가락끝검출.png" width="400" height="300">

- 얼굴 인식

### 

<img src="/img/드럼스틱.png" width="400" height="300">

- 드럼 선택 시 카메라 화면에 검출되는 빨간색, 파란색 물체의 중심좌표를 표시함

### 

<img src="/img/선택화면.png" width="400" height="300">

- 최초 실행시 원하는 악기를 선택할 수 있고, 선택 이후에도 화면의 우측 상단의 메뉴를 통해 악기 변경 가능

### 

<img src="/img/연주.png" width="600" height="300">

- 드럼스틱 또는 손가락 끝 좌표를 이용해 카메라 화면상의 악기 영역 안으로 움직이면 악기의 소리가 재생됨

### 

## 구현 방법

## 손가락 끝 검출 ##

<img src="/img/영상변환.png" width="600" height="300">
<img src="/img/영상이진화.png" width="600" height="300">

- 카메라 화면의 RGB영상을 YCrCb영상으로 변환하여 손 피부색 영역에 해당하는 범위의 값을 추출해 이진화

### 

<img src="/img/손가락끝검출설명.png" width="600" height="300">

- 손 영역의 외곽선을 검출
- Convex 결함(외곽선 다각형 내의 빈 공간) 검출
- Convex 결함의 깊이를 고려하여 결함의 시작점과 끝점을 이용해 손가락 끝 좌표를 검출

### 

## 특정 색 물체 검출 ##

<img src="/img/드럼스틱.png" width="400" height="300">

- 카메라 화면의 RGB영상을 HSV영상으로 변환하여 빨간색, 또는 파란색 물체의 영역을 검출하고 영역안 픽셀들의 x, y좌표의 평균값을 구해 무게중심 좌표를 검출 

### 

## 동영상 링크(이미지를 클릭하면 유튜브 영상으로 이동합니다)
[![Video Label](https://github.com/emperor5519/AR-instrument/blob/main/img/%EC%9C%A0%ED%8A%9C%EB%B8%8C%EC%8D%B8%EB%84%A4%EC%9D%BC.png)](https://www.youtube.com/watch?v=4u47xhIxIt0&ab_channel=%EC%B5%9C%EC%8A%B9%ED%98%B8)

사람인 이력서에도 동영상이 첨부되어 있습니다

### 
