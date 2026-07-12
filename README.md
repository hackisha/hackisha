<div align="center">

# hackisha

### Automotive Embedded Software Developer

차량의 신호를 코드로 읽고, 센서와 제어기를 연결해 실제로 움직이는 시스템을 만듭니다.

`CAN` `SocketCAN` `Raspberry Pi` `Python` `Embedded I/O` `Vehicle Data`

</div>

---

## About Me

차량에서 발생하는 신호를 읽고 필요한 값으로 변환한 뒤, 저장하거나 다른 장치로 전달하는 작업을 해왔습니다.

CAN 프레임 파싱부터 UART와 I2C 센서 연동, GPIO 상태 제어, Raspberry Pi 기반 데이터 로거까지 직접 연결했습니다. 수집한 데이터가 실제 개발에 다시 쓰일 수 있도록 차량 로그 분석 도구도 함께 만들고 있습니다.

현재는 **차량용 임베디드 소프트웨어와 하드웨어 인터페이스를 이해하고, 기능 단위 코드를 전체 시스템으로 연결하는 개발자**를 목표로 합니다.

## What I Have Built

### 1. 차량 신호를 읽는 코드

- SocketCAN으로 ECU의 CAN 프레임 수신
- 바이트 배열의 endian, signed 여부, scale을 반영해 RPM, TPS, 온도, 압력, 기어 등으로 변환
- CAN 수신과 파싱을 worker로 분리해 메인 로직이 프레임 형식에 직접 의존하지 않도록 구성
- 필요한 데이터를 별도 CAN ID로 다시 송신하는 흐름 구현

### 2. 차량과 센서를 연결하는 임베디드 시스템

- Raspberry Pi에서 CAN, GPS, 가속도 센서를 각각 독립된 worker로 구성
- UART 기반 NMEA GPS와 I2C 기반 ADXL345 데이터 처리
- GPIO 버튼으로 로깅 상태를 전환하고 LED로 기록, 오류, 네트워크 상태 표시
- 종료 신호 발생 시 스레드, 파일, CAN, MQTT, GPIO 자원을 순서대로 정리

### 3. 수집한 데이터를 활용하는 도구

- CAN과 센서 데이터를 공통 CSV 및 JSON 구조로 통합
- 로컬 CSV 기록과 MQTT 텔레메트리 전송을 서로 다른 주기로 분리
- Flask-SocketIO 웹 화면에서 차량 상태를 실시간으로 표시
- Electron 데스크톱 도구에서 CSV 채널 매핑, 그래프, 이벤트 구간, HTML 보고서 구성

## System Flow

```text
ECU / GPS / Accelerometer
            ↓
CAN / UART / I2C Interface
            ↓
Raspberry Pi Embedded Software
            ↓
Parsing / State Integration / GPIO Control
            ↓
CSV Logging / MQTT Telemetry
            ↓
Web Dashboard / Desktop Analysis Tool
```

단일 기능을 따로 구현하는 데서 끝내지 않고, 차량 입력이 저장과 화면까지 이어지는 전체 흐름을 코드로 연결했습니다.

## Vehicle Embedded Projects

### 🚗 [EMU-LOGGER](https://github.com/hackisha/EMU-LOGGER)

> EMU BLACK ECU의 CAN 데이터와 GPS, 가속도 센서를 통합한 Raspberry Pi 기반 차량 데이터 로거

**주요 개발 내용**

- `0x600`부터 `0x607`까지의 EMU CAN 프레임 파싱
- GPS와 ADXL345 센서를 CAN 데이터와 같은 기록 구조로 통합
- GPIO 버튼과 상태 LED를 포함한 현장 로깅 흐름 구성
- CSV 저장, MQTT 전송, Flask-SocketIO 대시보드 연결
- 데이터 로거 PCB 자료와 Arduino 랩타이머 코드 정리

**기술:** `Python` `Linux SocketCAN` `UART` `I2C` `GPIO` `MQTT` `Flask-SocketIO`

**[프로젝트 개발 과정 보기 →](https://github.com/hackisha/EMU-LOGGER)**

---

### 📈 [MF-26](https://github.com/hackisha/MF-26)

> 차량에서 수집한 CSV 로그를 엔지니어가 다시 확인하고 활용할 수 있도록 만든 데스크톱 분석 도구

**주요 개발 내용**

- 차량별 CSV 채널 이름과 보정식을 프로필로 관리
- 속도, RPM, 온도, 압력, 가속도, GPS 데이터를 같은 세션에서 확인
- 시계열 그래프, G-G 분포, GPS 경로와 이벤트 구간 표시
- 분석 내용을 HTML 보고서로 저장
- 대용량 로그 처리 과정에서 집계 방식과 화면 렌더링 구조 개선

**기술:** `TypeScript` `Electron` `React` `Zustand` `Plotly`

**[프로젝트 코드 보기 →](https://github.com/hackisha/MF-26)**

## 개발할 때 중요하게 보는 것

- 데이터가 어디에서 들어오고 어떤 단위를 가지는지 먼저 확인합니다.
- 장치별 코드를 분리하고, 메인 흐름에서는 공통 인터페이스로 다룹니다.
- 차량에서 남긴 데이터가 이후 분석과 개선으로 이어지도록 구조를 설계합니다.
- 구현 과정에서 발생한 문제와 선택 이유를 코드와 문서에 함께 남깁니다.

---

<div align="center">

**Vehicle Signal → Embedded Software → Data Utilization**

</div>
