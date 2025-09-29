# AXI4-Lite Protocol 기반 IP 설계

## 📝 프로젝트 개요

- 본 프로젝트는 고속 데이터 통신을 위한 **AXI4-Lite 프로토콜**의 구조를 이해하고, 이를 기반으로 **FND Controller IP**를 설계하는 것을 목표 
- SystemVerilog로 설계된 IP를 검증하고, C언어를 통해 FPGA 보드에서 실제 동작을 구현

- **주요 목표**:
  1. AXI 버스 구조 설계 및 프로토콜 동작 이해 
  2. AXI4-Lite 슬레이브로 동작하는 FND 컨트롤러 IP 설계 
  3. C언어를 이용한 펌웨어 작성 및 시스템 기능 구현 

---

## 🛠️ 개발 환경

- **언어**: SystemVerilog, C 
- **개발 툴**: Vivado 2020.2, Vitis 
- **FPGA**: Xilinx Basys3 

---

### 📖 AXI4-Lite의 주요 특징

- **5개의 독립 채널**: 주소와 데이터 경로가 분리되어 읽기와 쓰기 동작이 병렬로 처리될 수 있어 효율이 극대화
  - 쓰기 채널: Write Address (AW), Write Data (W), Write Response (B) 
  - 읽기 채널: Read Address (AR), Read Data (R) 
- **핸드셰이크 메커니즘**: `VALID`와 `READY` 신호를 이용한 핸드셰이킹을 통해 데이터 전송의 안정성을 보장 
---

## ⚙️ 설계 구조: FND 컨트롤러 IP

AXI4-Lite 버스의 슬레이브로 동작하는 FND 컨트롤러를 설계

### 레지스터 맵 (Register Map)

- **Control Register (주소 `0x00`)**: FND의 동작을 제어 
- **Data Register (주소 `0x04`)**: FND에 표시할 숫자 또는 문자 데이터

---

## 🔬 검증 (Verification)

SystemVerilog 테스트벤치를 구축하여 AXI4-Lite 프로토콜의 쓰기/읽기 트랜잭션이 정상적으로 동작하는지, 그리고 레지스터에 기록된 값에 따라 FND가 올바르게 제어되는지를 시뮬레이션 파형을 통해 검증했습니다.

- **주요 검증 항목**:
  - AXI 쓰기 트랜잭션을 통한 레지스터 값 변경 확인
  - AXI 읽기 트랜잭션을 통한 레지스터 값 조회 확인
  - 레지스터 값에 따른 FND 출력 신호 변화 검증

---
