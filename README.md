# 전성빈


[차량 데이터 로거](#01-emu-logger) · [ECU 검증](#02-canoe--capl-ecu-검증) · [V2X 협력주행](#03-v2x-협력주행) · [모션 플래닝·제어](#04-motion-planning--control)

## 주요 프로젝트

### 01. EMU LOGGER

**차량의 CAN·GPS·가속도 데이터를 기록하고 웹에서 확인하는 데이터 로거**

<a href="https://github.com/hackisha/EMU-LOGGER"><img src="https://github.com/user-attachments/assets/f171d1c5-e8be-448f-9e02-eb798c778eba" width="680" alt="EMU LOGGER 차량 데이터 대시보드" /></a>

- **수집:** Raspberry Pi에서 EMU Black ECU의 CAN 데이터와 GPS·가속도 센서 값을 수집
- **기록·전송:** CSV 저장과 MQTT 전송으로 주행 데이터를 기록하고 공유
- **시각화:** Flask-SocketIO 기반 웹 대시보드로 차량 상태 확인

`Python` `Raspberry Pi` `SocketCAN` `UART / I²C` `MQTT` `Flask-SocketIO`

**[프로젝트 상세 · 코드 →](https://github.com/hackisha/EMU-LOGGER#readme)**

---

### 02. CANoe / CAPL ECU 검증

**요구사항의 경계값과 시간 조건을 확인하는 블랙박스 테스트**

<a href="https://github.com/hackisha/IVS/tree/main/BLACK_BOX_TESTING_WITH_CANOE"><img src="https://github.com/user-attachments/assets/a0e93772-8427-4750-a2a9-2ee1c265162d" width="680" alt="CANoe 기반 ECU 블랙박스 테스트 화면" /></a>

- **설계:** Fail-safe 요구사항을 동등 분할·경계값 분석으로 테스트 케이스화
- **자동화:** CAPL로 입력 신호 주입, ECU 응답 관찰과 판정 흐름 구성
- **분석:** 경계값과 고장 검출·복귀 시간을 비교해 요구사항과 실제 동작의 차이 확인

`CANoe` `CAPL` `CAN` `Black-box Testing` `EP / BVA`

**[프로젝트 상세 · 테스트 코드 →](https://github.com/hackisha/IVS/tree/main/BLACK_BOX_TESTING_WITH_CANOE#readme)**

---

### 03. V2X 협력주행

**주행 정보를 공유하며 함께 회피하는 두 대의 Raspberry Pi 주행로봇**

<a href="https://github.com/hackisha/26HL_IVS_V2X_CAD"><img src="https://github.com/user-attachments/assets/d3544384-6655-45e6-9b38-fa5684e53a8d" width="680" alt="V2X 협력주행 프로젝트 구성 및 시연" /></a>

- **인지·제어:** 차선 인식, 경로 생성과 추종 제어를 주행 시스템으로 통합
- **통신:** UDP/JSON으로 차량 상태와 목표 차선·신호등 정보 교환
- **협력:** 선행차의 회피 정보를 서버가 중계하고 후행차의 주행에 반영

`Python` `Raspberry Pi` `Pure Pursuit` `UDP / JSON` `System Integration`

**[프로젝트 상세 · 코드 →](https://github.com/hackisha/26HL_IVS_V2X_CAD#readme)**

<details>
<summary>주행로봇 사진 더 보기</summary>

<img src="https://github.com/user-attachments/assets/a8d93f73-e0d7-49d8-8553-baee16383e44" width="420" alt="V2X 협력주행 프로젝트 주행로봇" />

</details>

---

### 04. Motion Planning & Control

**경로 계획과 차량 제어를 학습하고 CarMaker·Simulink에서 연결한 프로젝트**

<a href="https://github.com/hackisha/MotionPlanningControl"><img src="https://github.com/user-attachments/assets/9628b34d-832d-4044-8ae7-01eee8138d9e" width="680" alt="CarMaker 및 Simulink 기반 차량 주행 시뮬레이션" /></a>

- **기초 구현:** 필터, PID, 경로 탐색과 경로 추종 알고리즘 학습·구현
- **통합:** CarMaker와 Simulink를 연동해 주행 시나리오 구성
- **제어:** 미션 상태에 따라 경로 생성, 횡·종방향 제어와 변속 상태 전환

`Python` `MATLAB` `Simulink` `CarMaker` `Motion Planning` `Vehicle Control`

**[프로젝트 상세 · 코드 →](https://github.com/hackisha/MotionPlanningControl#readme)**

## 임베디드 개발 경험

### UDS 기반 펌웨어 업데이트 부트로더

AURIX TC234LP 교육용 ECU에서 Boot와 Application 영역을 분리하고, UDS 서비스를 이용한 펌웨어 업데이트 흐름을 구현했습니다. 전송 중 기존 Application을 보존하는 이중 메모리 구조와 SHA-256 기반 이미지 무결성 검증을 적용했습니다.

`Embedded C` `AURIX TC234LP` `UDS` `EB tresos` `TRACE32` `SHA-256`

## 사용 기술과 관심 분야

| 분야 | 프로젝트에서 사용한 기술 |
| :--- | :--- |
| 임베디드·하드웨어 | Embedded C, AURIX, Raspberry Pi, UART, I²C, GPIO |
| 차량 통신·검증 | CAN, UDS, SocketCAN, CANoe, CAPL |
| 데이터 수집·시각화 | Python, MQTT, Flask-SocketIO, CSV |
| 차량 제어·시뮬레이션 | MATLAB, Simulink, CarMaker, Pure Pursuit |
| 개발·디버깅 | Git, EB tresos, TRACE32 |

차량용 ECU Basic Software, AUTOSAR MCAL, Fail-safe 설계와 테스트 자동화에 관심이 있습니다.
