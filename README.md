# 객체 인식 모델을 이용한 수신호 인식 모델 학습 및 인포테인먼트 제작

## 프로젝트 개요
이 프로젝트는 AI를 활용하여 수신호 인식 모델을 만들어 차량 고장, 교통 통제 때 사고 발생율을 줄이기 위해 제작된 프로젝트입니다.

## 개발 일정 (Gantt 차트)

```mermaid
gantt
    title 개발 일정      
    dateFormat  YYYY-MM-DD 
    section 계획
    데이터셋 찾기 및 모델 학습 가능 여부 분석 :2024-09-23, 2024-09-29
    딥러닝 모델 조사 및 기자재 리스트업      :2024-09-23, 2024-09-29
    section 모델 개발
    사람 인식 및 포즈 인식                     :2024-09-30, 2024-10-04
    행동 인식                      :2024-09-30, 2024-10-04
    학습된 모델 테스트                      :2024-09-30, 2024-10-04
    section 인포테인먼트 개발
    QT로 모델 사용 가능 확인 및 디스플레이 내장 :2024-10-05, 2024-10-11
    Yocto 제작                             :2024-10-05, 2024-10-11
    인포테인먼트 제작                      :2024-10-12, 2024-10-20
    모델 연동                             :2024-10-12, 2024-10-20
    section 발표 준비
    발표 준비                    :2024-10-21, 2024-10-23

```

## 플로우차트

```mermaid
graph LR

    Sensors["센서 시스템 (환경 데이터 수집)"]
    RGBDepthCamera["RGB-Depth 카메라"]
    LiDAR["LiDAR"]
    EmbeddedLinux["임베디드 리눅스 (데이터 처리 및 ADAS 기능)"]
    Actuators["차량 제어 장치 (예: 조향, 제동)"]
    DriverDisplay["운전자 디스플레이"]
    Infotainment["인포테인먼트 시스템"]

    %% 센서에서 임베디드 시스템으로의 데이터 흐름 %%
    Sensors -->|"RGB & Depth 데이터"| RGBDepthCamera
    Sensors -->|"3D 포인트 클라우드"| LiDAR
    RGBDepthCamera -->|"데이터 처리"| EmbeddedLinux
    LiDAR -->|"데이터 처리"| EmbeddedLinux

    %% 차량 제어 및 운전자 알림 흐름 %%
    EmbeddedLinux -->|"제어 신호"| Actuators
    EmbeddedLinux -->|"경고 및 정보"| DriverDisplay
    EmbeddedLinux -->|"경고 및 알림"| Infotainment
```

## 시스템 아키텍쳐
![시스템 아키텍쳐](https://github.com/user-attachments/assets/bb0c5107-da1c-4e72-b627-c48ee48aabff)


## 개발 환경
- Ubuntu Linux
- Q.T
- VScode


## 프로젝트 팀원
- [서창민]
- [박준수]
- [김도하]

## 사용 기술
- AI/딥러닝
- Python 3.12
- YoloV8
- Yocto

## 09.25
- 사람 인식은 YoloV8 NAS로 진행
- 포즈 인식은 MMpose로 진행
- 행동 인식은 PoseC3D로 진행
- 포즈, 행동 인식은 엣지 디바이스에서 정상적인 성능을 발휘하지 못하면 Movinet으로 변경해야함
- 모델 테스트까지 완료한다면 잿슨 나노에 탑재 후 실행, 추론 테스트 진행
- 잿슨 나노에서 정상적으로 성능을 발휘한다면 디스플레이 탑재 후 띄워보기
- 가능하면 Yocto구현 (이거 가능할지는 잿슨 나노에서의 성공 여부가 가장 중요)
- 인포테인먼트으 기본 기능 구성
- [서창민, 박준수, 김도하]
