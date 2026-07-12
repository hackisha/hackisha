# 전성빈

자작차 동아리 데이터로거 개발을 시작으로 차량용 임베디드 SW 개발자를 꿈꾸는 전성빈입니다.

## 자작차 동아리 활동

### [EMU LOGGER](https://github.com/hackisha/EMU-LOGGER)

EMU Black ECU의 CAN 데이터와 GPS, 가속도 센서 값을 Raspberry Pi에서 함께 수집하는 차량 데이터 로거입니다. SocketCAN, UART, I2C 입력을 각각 분리해 처리하고 CSV 기록, MQTT 전송, 웹 대시보드까지 연결했습니다.

`Python` `SocketCAN` `UART` `I2C` `GPIO` `MQTT`

### [MF Log Analyzer](https://github.com/hackisha/MF-26)

Formula Student 차량에서 수집한 CSV 로그를 주행 후 확인하기 위한 데스크톱 분석 도구입니다. 차량별 채널과 보정식을 프로필로 관리하고, 로그 진단과 이벤트 탐지, 시계열 및 GPS 시각화, HTML 보고서 생성을 구현했습니다.

`TypeScript` `Electron` `React` `Zustand` `Plotly` `Vitest`

### Formula Student BSPD 안전회로 · 진행 중

Formula 2026 규정을 비프로그래밍 하드웨어 요구사항으로 바꾸어 설계하고 있습니다. TPS와 브레이크 압력 신호의 범위 및 시간 조건을 comparator, RC delay, fault latch, fail-safe relay로 구현하고 있으며, 회로 블록별 부품 선정 근거와 검증 항목을 함께 기록합니다.

`Analog Circuit` `Comparator` `RC Timing` `Fail-safe` `EasyEDA`

## HL만도·HL클레무브 IVS 교육

### [V2X 협력주행](https://github.com/ChungRyeung/26HL_IVS_V2X_CAD)

7인 팀에서 선행차 하드웨어와 주행 SW, 시스템 통합을 담당했습니다. Raspberry Pi 기반 차량에 차선 중심 경로 생성과 Pure Pursuit 제어를 적용했고, 한쪽 차선이 사라지는 코너에서는 학습한 차선 폭으로 가상 중심선을 생성하도록 수정했습니다. DRY 실행, 서보 단독 시험, 실차 주행 순서로 검증했으며 프로젝트는 우수 프로젝트로 선정되었습니다.

`Python` `Raspberry Pi` `Pure Pursuit` `UDP/JSON` `System Integration`

### [CarMaker ADAS Motion Planning & Control](https://github.com/hackisha/MotionPlanningControl)

CarMaker와 Simulink를 연동해 추월, 톨게이트 통과, 주차장 진입과 전후진 주차를 구현한 프로젝트입니다. 미션 상태 관리, 경로 생성, 횡종방향 제어를 구성했습니다. 역주차는 목표 자세까지 도달했지만 전체 경로의 one-lap 조건은 만족하지 못해, 부분 성공과 남은 문제를 함께 기록하고 있습니다.

`MATLAB` `Simulink` `CarMaker` `Motion Planning` `Vehicle Control`

### UDS OTA 부트로더

AURIX TC234LP 기반 교육용 ECU에서 Boot와 Application 영역을 분리하고 UDS 재프로그래밍 흐름을 구현했습니다. 업데이트 중 기존 Application을 보존하는 이중 메모리 구조와 SHA-256 이미지 검증을 다뤘으며, Linker Script 주소 충돌을 TRACE32로 분석했습니다.

`C` `AURIX` `UDS` `EB tresos` `TRACE32` `SHA-256`

### [CANoe CAPL 블랙박스 테스트](https://github.com/hackisha/mando/tree/main/BLACK_BOX_TESTING_WITH_CANOE)

ECU FailSafe 요구사항을 동등 분할과 경계값 분석으로 테스트 케이스화하고, CANoe/CAPL로 신호 주입과 판정을 자동화했습니다. 보존된 실행 결과에서는 12개 테스트 중 8개가 통과했고, 경계값과 타이밍, 상태 관리 관련 결함을 확인했습니다.

`CANoe` `CAPL` `CAN` `Black-box Testing` `EP/BVA`

## 기타

### 관심 분야

- 차량용 임베디드 SW와 ECU Basic Software
- CAN, UDS, AUTOSAR MCAL
- 차량 제어와 시스템 통합
- Fail-safe 설계와 테스트 자동화
- 차량 데이터 수집 및 분석

---

프로젝트 저장소에는 결과만 보여주기보다 구현 과정에서 내린 선택, 확인한 문제, 남은 한계를 함께 남기려고 합니다.
