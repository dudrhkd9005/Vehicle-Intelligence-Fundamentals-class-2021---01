# 차량지능기초과제
# 소프트웨어학부 20203042 김영광

1. 자율주행 인지에 관련된 3종 이상의 공개 Data Set 조사, 정리

# 1) COCO Dataset - 코코 데이터셋
 COCO Dataset은 object detection, segmentation, keypoint detection 등을 위한 데이터셋으로, 매년 전 세계의 여러 대학과 기업들이 참가하는 대회 등에서 사용되고 있습니다.

## ※ COCO Dataset의 구성
  ![image](https://user-images.githubusercontent.com/22697171/113810940-40a73f80-97a6-11eb-923b-340cc506929c.png)

dataset을 다운로드 받으면 위와같이 jpg파일로 구성되어있습니다. 그리고 annotations 폴더에는 6개의 json파일이있는데요 각각 captions, instances, person_keypoints가 있습니다.

- captions : 텍스트로 된 그림에 대한 설명
- instances : 그림에 있는 사람/사물에 대한 category와 영역 mask정보
- person_keypoints : 사람의 자세 데이터

COCO Dataset은 여러 일상 이미지들을 집합해 모아놓았습니다. 그 양은 2017년 공개된 데이터 셋 기준으로
● train (19G)
● val2017 (788M)
● test2017 (6.3G)
● annotations (808M)
의 데이터를 제공하고 있습니다. 또한 328,000장의 이미지와 250만개의 label이 포함되어있습니다.






## ※ COCO Dataset의 활용예시와 클래스
![image](https://user-images.githubusercontent.com/22697171/113810959-48ff7a80-97a6-11eb-8c85-b89129707bab.png)

위 사진은 COCO Dataset으로 학습을 적용시킨 person이 인식된 사진입니다. person말고도 car, bench, chair, flower등 다양한 사물도 인식할 수 있습니다. 또한 이러한 생물과 사물의 이름이 클래스의 이름이 되는데요 COCO는 person, bicycle, bus 등 80개에 달하는 클래스를 가지고 있습니다. 만약 클래스 이름을 검출하고 싶다면 coco80.name 명령어를 사용하고 하나의 클래스만 detection 하고싶다면 person.names 과 같이 명령어를 사용하면됩니다.

## ※ API
  COCO Dataset에는 image와 annotation을 쉽게 다루기위한 API인 COCO API와 모든 개체 인스턴스에 대한 세분화 마스크를 제공해주는 MASK API가 있습니다.
COCO Dataset API: https://cocodataset.org/#download

















# 2) PASCAL VOC Dataset
  PASCAL VOC Dataset은 2005년부터 VOC(비주얼 객체 클래스)에 대한 연구를위해 만들어진 데이터셋입니다. PASCAL VOC는 2012년에 공개된 기준으로 총 20개의 분류 클래스와 10개의 동작 클래스를 가지고 있습니다.
  
![image](https://user-images.githubusercontent.com/22697171/113810970-4c930180-97a6-11eb-9e7a-a8823f508d13.png)

20개의 분류 클래스

![image](https://user-images.githubusercontent.com/22697171/113810973-4e5cc500-97a6-11eb-96ae-a6936106b5b9.png)

10개의 동작 클래스

## ※ PASCAL VOC Dataset의 구성
● 객체 클래스 인식을 위한 표준화 된 이미지 데이터 셋
● 데이터 셋 및 주석에 엑세스하기 위한 공토 도구 셋
● 다양한 방법의 평가 및 비교 기능
PASCAL VOC Dataset은 교육/검증 데이터, 주석 데이터를 읽기위한 MATLAB코드, 지원 파일 및 각 대회에 대한 예제 구현 코드로 구성되어있습니다. 2011년 기준으로
● 교육/검증 데이터(2G)
● 개발 키트 코드 및 문서(500KB)
● pdf문서(500KB)
등의 데이터를 제공하고 있습니다.

## ※ PASCAL VOC Dataset의 활용예시
![image](https://user-images.githubusercontent.com/22697171/113810980-5157b580-97a6-11eb-9fa4-5bcb5a0261fc.png)

사람의 신체 부분(손, 머리, 발)의 layou과 label을 예측해내는 기술

![image](https://user-images.githubusercontent.com/22697171/113811047-75b39200-97a6-11eb-9392-2d10a390f651.png)
![image](https://user-images.githubusercontent.com/22697171/113811006-5b79b400-97a6-11eb-952f-dd245aaf4409.png)

동물을 분류해내는 동물 분류기술































# 3) nuscenes Dataset
 nuscenes Dataset은 3D object annotation이 포함 된 대규모 자율주행 데이터 셋입니다.
- nuscenes에 사용되는 데이터베이스 스키마

![image](https://user-images.githubusercontent.com/22697171/113811088-86640800-97a6-11eb-8ff6-86c4185333ec.png)

- nuscenes Dataset의 속성

![image](https://user-images.githubusercontent.com/22697171/113811090-882dcb80-97a6-11eb-935e-9b806b5bfe8e.png)

속성은 범주가 동일하게 유지되는 동안 변경 될 수 있는 인스턴스의 속성을 말합니다. 예시로는 주차 / 정지 / 이동중인 차량 및 자전거 등에 탑승자가 있는지 여부하는 것을 들 수 있습니다.

## ※ nuscenes Dataset의 구성
● 센서 제품(라이다, 레이더 x5, 카메라 x6, IMU센서, GPS센서)
● 20초당 1000개의 scene제공
● 1,400,000 개의  카메라 이미지
● 390,000개의 lidar sweeps
● 23개의 객체 클래스에 대해 수동으로 주석이 추가 된 140만개의 3D 바운딩 박스
● visibility, activity 및 pose와 같은 속성
● 32개 클래스에 대해 수동으로 주석이 추가 된 1.1B의 lidar points

이 외에도 nuscenes Dataset은 nulmages라는 또다른 데이터 셋을 출시 했습니다. nulmages는 이미지 수준의 2D 주석이달린 대규모 자율주행 데이터 셋트로 구성은 다음과 같습니다.
● 6초당 93k 동영상 클립제공(150시간에 달하는 운전시간)
● 110만개의 카메라 이미지
● nusccenes Dataset과 동일한 센서 제품군
● 2D 바운딩 박스 및 Instance mask가 있는 전경 개체
● background class를 위한 10만개의 2D 세분화 마스크

## ※ nuScenes Dataset과 nulmages Dataset의 활용예시

![image](https://user-images.githubusercontent.com/22697171/113811098-8b28bc00-97a6-11eb-890c-bb3b179e7347.png)

nuScenes Dataset

![image](https://user-images.githubusercontent.com/22697171/113811103-8cf27f80-97a6-11eb-96f7-1e0d7a9a27f0.png)

nulmages Dataset
