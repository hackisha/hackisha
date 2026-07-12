# hackisha | Automotive Embedded SW Developer

차량 CAN 데이터를 수집하고 주행 로그를 분석·시각화하는 소프트웨어를 구현합니다.

## Focus

- Raspberry Pi와 Linux SocketCAN 기반 차량 데이터 수집
- 센서·CAN 로그의 CSV 저장과 MQTT 기반 전달
- 데스크톱 로그 분석, 진단 규칙, 시각화와 보고서 생성
- 실행 가능한 검증 절차와 현재 제약을 함께 기록하는 개발

## Selected Projects

### [EMU-LOGGER](https://github.com/hackisha/EMU-LOGGER)

Raspberry Pi에서 EMU BLACK의 CAN 데이터와 GPS·ADXL345 센서 데이터를 수집해 CSV로 저장하고, MQTT와 웹 대시보드로 전달하는 데이터 로거입니다. 현재 저장소 상태에서는 `gps_worker.py`의 SyntaxError와 누락된 import 때문에 end-to-end 실행이 차단되어 있습니다.

**검증 기술:** Python, Raspberry Pi, Linux SocketCAN, GPS, ADXL345, CSV, MQTT, Flask-SocketIO

- SocketCAN으로 CAN 프레임을 수신하고 센서 데이터를 함께 수집
- 수집 데이터를 CSV로 기록하고 MQTT로 발행
- Flask-SocketIO 기반 실시간 웹 대시보드로 데이터 전달
- 공개 테스트 MQTT broker 설정은 개발 확인용이며 운영 환경용이 아님

[저장소 바로가기](https://github.com/hackisha/EMU-LOGGER)

### [MF-26](https://github.com/hackisha/MF-26)

차량 CSV 로그를 프로필에 매핑해 탐색하고 분석하는 데스크톱 애플리케이션입니다. 제한된 진단·이벤트 규칙, Plotly 시각화와 HTML 보고서 생성을 제공합니다.

**검증 기술:** Electron, Vite, React, Zustand, TypeScript, Plotly, Vitest, Playwright

- CSV 채널을 차량 프로필에 매핑하고 세션 요약 제공
- 누락·비수치 채널 진단과 임계값 기반 이벤트 규칙 적용
- 시계열·차량 거동 데이터를 Plotly로 시각화하고 HTML 보고서 생성
- Vitest, TypeScript 검사, Playwright E2E 검증 구성

[저장소 바로가기](https://github.com/hackisha/MF-26)

## Engineering Approach

- 데이터 수집부터 저장, 전달, 분석까지 경계를 명확히 나눕니다.
- 코드와 검증 구성으로 확인되는 범위만 기술합니다.
- 알려진 실행 제약과 운영 환경의 차이를 숨기지 않습니다.

## Confidentiality

공개 권한과 기여 범위가 확인된 작업만 소개합니다.
