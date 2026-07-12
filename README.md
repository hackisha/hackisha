<div align="center">

# hackisha

### Automotive Embedded SW Developer

차량의 데이터를 **수집하고, 저장하고, 전달하고, 분석하는** 소프트웨어를 만듭니다.

[Selected Projects](#selected-projects) | [Development Flow](#development-flow) | [Engineering Approach](#engineering-approach)

</div>

---

## About

Raspberry Pi와 Linux SocketCAN으로 차량 CAN 및 센서 데이터를 수집하고, 데스크톱 애플리케이션에서 주행 로그를 분석하고 시각화하는 과정을 경험했습니다.

하드웨어에서 시작하는 데이터 수집부터 CSV 기록, MQTT 전달, 로그 진단과 보고서 생성까지 하나의 흐름으로 연결하는 데 관심이 있습니다.

## What I Build

| Vehicle Data Acquisition | Telemetry Pipeline | Log Analysis |
| --- | --- | --- |
| CAN 프레임 파싱 | CSV 데이터 기록 | 차량 프로필 기반 채널 매핑 |
| GPS 및 가속도 센서 통합 | MQTT 실시간 전송 | 진단 및 이벤트 규칙 |
| Raspberry Pi GPIO 제어 | Flask-SocketIO 중계 | 시계열, 차량 거동, GPS 시각화 |

## Development Flow

```text
Vehicle & Sensors
        ↓
CAN / GPS / Accelerometer
        ↓
Raspberry Pi Data Logger
        ↓
CSV Storage + MQTT Telemetry
        ↓
Web Dashboard + Desktop Log Analyzer
```

수집 장치별 입력을 분리하고, 공통 데이터 구조로 합친 뒤 저장과 전송을 나눕니다. 기록된 데이터는 다시 프로필 매핑, 진단 규칙, 시각화와 보고서 생성으로 이어집니다.

## Selected Projects

### 🚗 [EMU-LOGGER](https://github.com/hackisha/EMU-LOGGER)

> 차량 ECU의 CAN 데이터와 GPS, 가속도 센서를 함께 수집해 CSV와 실시간 텔레메트리로 전달하는 Raspberry Pi 데이터 로거

`Python` `Raspberry Pi` `Linux SocketCAN` `GPS` `ADXL345` `MQTT` `Flask-SocketIO`

- EMU CAN 프레임을 RPM, TPS, 온도, 압력, 기어 등 물리량으로 변환
- CAN, GPS, 3축 가속도 worker를 분리하고 최신 상태를 하나의 CSV 및 JSON 구조로 통합
- GPIO 버튼과 LED로 현장 로깅 상태 제어
- MQTT와 Flask-SocketIO를 연결해 웹 대시보드로 텔레메트리 전달

**[개발 과정과 코드 보기 →](https://github.com/hackisha/EMU-LOGGER)**

---

### 📊 [MF-26](https://github.com/hackisha/MF-26)

> 차량 CSV 로그를 프로필에 맞게 해석하고 진단, 이벤트 탐지, 시각화와 HTML 보고서로 연결하는 데스크톱 분석 도구

`Electron` `TypeScript` `React` `Zustand` `Plotly` `Vitest` `Playwright`

- CSV 채널 별칭과 보정식을 차량 프로필로 관리
- 누락 및 비수치 채널, 타임스탬프, 전압, 센서 스케일을 진단 규칙으로 확인
- 시계열, G-G, GPS 경로와 이벤트 구간을 분석 화면으로 구성
- 선택한 분석 결과를 HTML 보고서로 생성하고 자동화 테스트로 주요 흐름 확인

**[분석 기능과 코드 보기 →](https://github.com/hackisha/MF-26)**

## Engineering Approach

```text
실제 입력 구조를 확인한다
→ 장치와 기능의 경계를 나눈다
→ 데이터 흐름을 코드로 연결한다
→ 테스트와 실행 결과로 동작을 확인한다
→ 남은 한계와 다음 개선점을 기록한다
```

- 하드웨어 의존 코드와 데이터 처리, 사용자 화면을 분리합니다.
- 구현 과정의 선택 이유와 시행착오를 README와 코드에 함께 남깁니다.
- 공개 가능한 코드와 근거가 확인된 내용만 포트폴리오에 소개합니다.

---

<div align="center">

**Vehicle Data Acquisition → Telemetry → Analysis**

</div>
