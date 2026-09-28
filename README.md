# 전성빈
### 차량용 임베디드 SW 개발과 검증

실제 차량에서 동작하는 시스템을 만들고, 요구사항을 시험으로 확인하는 경험을 쌓았습니다.  
**UDS 부트로더 개발, CANoe/CAPL 검증, V2X 주행 시스템 통합**을 바탕으로 신뢰할 수 있는 차량용 SW를 개발하고자 합니다.

[프로젝트](#projects) · [기술](#skills) · [교육 및 활동](#experience)

| 개발 | 검증 | 차량 적용 |
| :--- | :--- | :--- |
| AURIX 기반 UDS 부트로더 | CAPL 자동화로 **13건의 동작 이슈** 발견 | CAN 데이터 로거 제작 |
| 다운로드 중단에 대비한 메모리 이중화 | 동등분할과 경계값 분석 | V2X 로그 기반 주행 튜닝 |

<a id="projects"></a>
## 주요 프로젝트

### 01. UDS 기반 OTA 부트로더 개발
**다운로드가 중단돼도 기존 Application을 보존하도록 설계**

`C` `AURIX TC234LP` `AUTOSAR MCAL` `UDS` `EB tresos` `TRACE32`

- Bootloader와 Application의 메모리 영역을 분리하고 부팅 및 Application 진입 흐름 구현
- UDS 세션 제어, SecurityAccess, Flash 삭제와 펌웨어 다운로드 처리
- 신규 이미지를 Secondary 영역에 수신하고 **SHA-256 무결성 검증을 통과한 경우에만 Primary 영역에 반영**
- 전송 중단 시 기존 Application 유지 여부와 바이너리 변경 시 업데이트 차단 여부 시험

<details>
<summary>개발 과정에서 익힌 메모리와 디버깅 지식</summary>

Flash 삭제 및 쓰기 함수의 RAM 실행 조건과 Linker Script의 코드 배치를 학습했습니다. TRACE32로 오류 상태와 메모리 덤프를 확인하는 실습을 통해, 코드의 실행 위치와 하드웨어 제약을 함께 살피는 방법을 익혔습니다.

</details>

---

### 02. CANoe/CAPL 기반 ECU 블랙박스 검증
**요구사항을 반복 가능한 시험으로 바꾸고, 13건의 동작 이슈 발견**

`Vector CANoe` `CAPL` `CAN` `요구사항 기반 테스트`

<a href="https://github.com/hackisha/IVS/tree/main/BLACK_BOX_TESTING_WITH_CANOE"><img src="https://github.com/user-attachments/assets/a0e93772-8427-4750-a2a9-2ee1c265162d" width="680" alt="CANoe 기반 ECU 블랙박스 검증 화면" /></a>

- 고장 검출, 회복, 삭제 요구사항을 분석하고 **동등분할과 경계값 분석**으로 테스트케이스 설계
- CAN 신호 주입부터 응답 수신, Pass/Fail 판정 및 시험 보고서 생성까지 자동화
- `testWaitForMessage()`로 ECU 응답을 기다린 뒤 시험 입력을 변경하도록 구성
- 경계값 오검출, 신호별 고장 상태의 동시 회복, 고장 삭제 시점 오류 등 **13건의 동작 이슈**를 발견하고 재현 조건, 기대값, 실제 결과를 보고

**[테스트 코드와 프로젝트 상세 →](https://github.com/hackisha/IVS/tree/main/BLACK_BOX_TESTING_WITH_CANOE#readme)**

---

### 03. V2X 협력주행 시스템 개발 및 통합
**주행 로그를 근거로 경로 생성과 조향을 개선하고 현장 시연 완료**

`Python` `Raspberry Pi` `Pure Pursuit` `GitHub` `Claude Code`

<a href="https://github.com/hackisha/26HL_IVS_V2X_CAD"><img src="https://github.com/user-attachments/assets/d3544384-6655-45e6-9b38-fa5684e53a8d" width="680" alt="V2X 협력주행 시스템 구성 및 시연" /></a>

- **선행차 하드웨어 구성, 로컬 경로 생성, Pure Pursuit 기반 조향 제어와 모듈 통합** 담당
- 한쪽 차선이 사라지면 학습한 차선 폭으로 가상 중심선을 생성해 코너 이탈 개선
- 차선 검출 상태, 경로 오차, 조향 명령과 모터 duty를 CSV로 기록하고, **Claude Code를 활용한 로그 분석을 바탕으로 조향 게인과 주행 duty 조정**
- 비구동 시험(DRY), 서보 단독 시험, 모형차 반복 주행으로 변경 사항을 확인하고 협력주행 현장 시연 완료

**[프로젝트 상세 →](https://github.com/hackisha/26HL_IVS_V2X_CAD#readme)** · **[로그 기록 코드](https://github.com/hackisha/26HL_IVS_V2X_CAD/blob/main/leader_v2/app/utils/logger.py)** · **[튜닝 설정](https://github.com/hackisha/26HL_IVS_V2X_CAD/blob/main/leader_v2/run_tuned.sh)**

<details>
<summary>주행로봇 사진 보기</summary>

<img src="https://github.com/user-attachments/assets/a8d93f73-e0d7-49d8-8553-baee16383e44" width="420" alt="V2X 프로젝트 주행로봇" />

</details>

---

### 04. 실차 CAN 데이터 로거 및 웹 모니터링
**차량에서 수집한 데이터를 기록하고 팀이 함께 확인할 수 있도록 구현**

`Python` `Raspberry Pi` `SocketCAN` `MQTT` `Flask-SocketIO`

<a href="https://github.com/hackisha/EMU-LOGGER"><img src="https://github.com/user-attachments/assets/f171d1c5-e8be-448f-9e02-eb798c778eba" width="680" alt="EMU LOGGER 차량 데이터 대시보드" /></a>

- EMU Black ECU의 CAN 데이터와 GPS, 가속도 센서 데이터를 수집
- CAN 프레임을 RPM, 차속, 온도 등의 물리량으로 변환하고 CSV 저장 및 MQTT 전송
- Flask-SocketIO 기반 웹 대시보드로 차량 상태와 주행 경로 시각화
- 로거 하드웨어와 센서를 통합하고 실제 차량에 적용해 주행 데이터 수집

**[프로젝트 상세와 코드 →](https://github.com/hackisha/EMU-LOGGER#readme)**

---

### 05. CarMaker 기반 주차 알고리즘 및 통합
**경로 계획과 추종 제어를 연결해 전진 및 후진 주차 구현**

`MATLAB` `Simulink` `CarMaker` `Hybrid A*` `Reeds-Shepp` `Pure Pursuit`

<a href="https://github.com/hackisha/MotionPlanningControl"><img src="https://github.com/user-attachments/assets/9628b34d-832d-4044-8ae7-01eee8138d9e" width="680" alt="CarMaker 및 Simulink 기반 차량 시뮬레이션" /></a>

- 전진 및 후진 주차를 위한 경로 계획과 추종 제어 담당
- Hybrid A*와 Reeds-Shepp 기반 경로 생성, Pure Pursuit 기반 추종 제어 적용
- CarMaker와 Simulink 환경에서 주차 로직을 통합하고 시뮬레이션으로 동작 확인

**[학습 코드와 CarMaker 프로젝트 →](https://github.com/hackisha/MotionPlanningControl#readme)**

<a id="skills"></a>
## 사용 기술

| 분야 | 프로젝트 및 실습에서 사용한 기술 |
| :--- | :--- |
| 임베디드 개발 | C, AURIX TC234LP, AUTOSAR MCAL, STM32 GPIO/HAL |
| 차량 통신 및 검증 | CAN, UDS, CANoe, CAPL, SocketCAN |
| 디버깅 및 개발 도구 | TRACE32, EB tresos, Git, GitHub |
| 데이터 수집 및 분석 | Python, CSV, MQTT, Flask-SocketIO |
| 제어 및 시뮬레이션 | MATLAB, Simulink, CarMaker, Pure Pursuit |
| 회로 및 하드웨어 | EasyEDA, Raspberry Pi, UART, I²C, GPIO |

**학습한 개발 프로세스:** A-SPICE 요구사항 추적성, V모델, ISO 26262 기초

<a id="experience"></a>
## 교육 및 활동

**HL만도·HL클레무브 Intelligent Vehicle School 5기**  
2025.12 – 2026.06 · 812시간 · 우수 수료생 선정

차량용 임베디드 SW, AUTOSAR MCAL, UDS 부트로더, CANoe/CAPL 검증과 차량 제어를 학습하고 프로젝트로 적용했습니다.

**순천향대학교 자작자동차 동아리 무한질주 | 전장팀**  
2024.10 – 2026.08

- 전자식 스로틀 안전회로인 BSPD를 설계하며 해외 팀의 자료와 RC 회로, 비교기 특성을 학습
- 국내 대회 규정을 요구사항으로 정리하고 일곱 번의 재설계를 거쳐 회로 제작
- 규정별 대응 방식과 검사 방법을 보고서로 작성하고, 팀의 전자식 스로틀 검차 통과 및 대회 사용에 기여

**순천향대학교**  
정보보호학과 / 사물인터넷학과 복수전공 · 2026.08 졸업

## 자격 및 수상

- **정보처리기사** · 2026.09
- **ISTQB CTFL** · 2026.02
- **한국융합신호처리학회 우수발표논문상** · 2025.05  
  Wi-Fi CSI 기반 비접촉 제스처 인식 시스템
