<img width="2559" height="1391" alt="image" src="https://github.com/user-attachments/assets/f1d96b3b-cae5-4b0c-9b27-9509d78010f2" /># 전성빈

자작차 동아리 데이터로거 개발을 시작으로 차량용 임베디드 SW 개발자를 꿈꾸는 전성빈입니다.

## 자작차 동아리 활동

### [EMU LOGGER](https://github.com/hackisha/EMU-LOGGER)
<img width="1080" height="745" alt="image" src="https://github.com/user-attachments/assets/f171d1c5-e8be-448f-9e02-eb798c778eba" />

EMU Black ECU의 CAN 데이터와 GPS, 가속도 센서 값을 같은 시간축으로 수집하는 Raspberry Pi 기반 차량 데이터 로거입니다. 주행 데이터를 CSV로 저장하고 MQTT와 웹 대시보드로 전달해 차량 안팎에서 기록 상태와 주요 정보를 확인할 수 있도록 구성했습니다.

`Python` `SocketCAN` `UART` `I2C` `GPIO` `MQTT`

### [MF Log Analyzer](https://github.com/hackisha/MF-26)
<img width="2559" height="1391" alt="image" src="https://github.com/user-attachments/assets/52c4a73b-7f14-4efb-b71a-9f155fa1a9a0" />

Formula Student 차량에서 수집한 CSV 로그를 주행 후 검토하기 위한 데스크톱 분석 도구입니다. 서로 다른 차량의 채널과 보정식을 프로필로 관리하며, 로그 진단과 이벤트 탐지, 시계열 및 GPS 시각화 결과를 하나의 HTML 보고서로 정리합니다.

`TypeScript` `Electron` `React` `Zustand` `Plotly` `Vitest`

### Formula Student BSPD 안전회로 · 진행 중
<img width="780" height="777" alt="image" src="https://github.com/user-attachments/assets/d80c0453-25ba-46f6-a9f0-186e13c1ceaf" />

Formula Student 차량에서 브레이크와 스로틀이 동시에 비정상 상태가 되거나 센서 신호가 손실될 때 구동 계통을 차단하는 독립 안전회로입니다. Formula 2026 규정을 바탕으로 TPS와 브레이크 압력 신호를 감시하고, comparator와 RC delay, fault latch, fail-safe relay만으로 고장을 판단하고 유지하도록 설계하고 있습니다.

`Analog Circuit` `Comparator` `RC Timing` `Fail-safe` `EasyEDA`

## HL만도·HL클레무브 IVS 교육

### [V2X 협력주행](https://github.com/ChungRyeung/26HL_IVS_V2X_CAD)

두 대의 Raspberry Pi 기반 주행로봇이 차선과 장애물 정보를 공유해 함께 회피 주행하는 V2X 협력주행 프로젝트입니다. 선행차가 장애물을 인식해 회피 경로를 생성하면 후행차가 전달받은 차선 정보를 이용해 자체 장애물 인식 없이 같은 구간을 주행하도록 구성했습니다.

`Python` `Raspberry Pi` `Pure Pursuit` `UDP/JSON` `System Integration`

### [CarMaker ADAS Motion Planning & Control](https://github.com/hackisha/MotionPlanningControl)

CarMaker와 Simulink를 연동해 추월부터 톨게이트 통과, 주차장 진입, 빈 공간 탐색과 전후진 주차까지 하나의 주행 시나리오로 수행하는 프로젝트입니다. 미션 상태에 따라 경로 생성과 횡종방향 제어, 변속 상태를 전환하도록 구성했으며, 현재 역주차는 완료했지만 전체 경로의 one-lap 조건은 추가 개선이 필요합니다.

`MATLAB` `Simulink` `CarMaker` `Motion Planning` `Vehicle Control`

### UDS OTA 부트로더

AURIX TC234LP 기반 교육용 ECU의 소프트웨어를 UDS 서비스로 갱신하는 부트로더 프로젝트입니다. Boot와 Application 영역을 분리하고, 전송 중에는 기존 Application을 보존하는 이중 메모리 구조와 SHA-256 기반 이미지 검증을 적용해 업데이트와 무결성 확인 흐름을 구성했습니다.

`C` `AURIX` `UDS` `EB tresos` `TRACE32` `SHA-256`

### [CANoe CAPL 블랙박스 테스트](https://github.com/hackisha/IVS/tree/main/BLACK_BOX_TESTING_WITH_CANOE)

ECU의 FailSafe 요구사항이 경계값과 시간 조건에 맞게 동작하는지 검증하는 블랙박스 테스트 프로젝트입니다. 요구사항을 동등 분할과 경계값 분석으로 테스트 케이스화하고, CANoe/CAPL로 입력 신호 주입부터 응답 관찰과 판정까지 자동화했습니다.

`CANoe` `CAPL` `CAN` `Black-box Testing` `EP/BVA`

## 기타

### 관심 분야

- 차량용 임베디드 SW와 ECU Basic Software
- CAN, UDS, AUTOSAR MCAL
- 차량 제어와 시스템 통합
- Fail-safe 설계와 테스트 자동화
- 차량 데이터 수집 및 분석
