# EMG Dashboard

PyQt6 기반 **실시간 4채널 근전도(EMG) 데이터 시각화** 데스크톱 앱입니다. 시리얼로 수신한 RAW/AMP를 그래프와 막대로 실시간 모니터링합니다.

---

## 주요 기능

- **RAW 그래프**: 4채널 시계열 (Line 모드 / Bar 모드 전환)
- **Diagonal Vector**: 채널별 대각선 방향 벡터 (관측 범위 대비 강도)
- **PWR BARS**: 채널별·AVG 진폭을 **비율(0~100%)**로 표시
- **CSV 로깅**: Raw/AMP/타임스탬프 저장
- **Window Size**: 진폭 계산에 쓰는 샘플 수 조절

---

## 요구 사항

- Python 3.x
- PyQt6
- pyqtgraph
- NumPy
- pyserial

---

## 설치 및 실행

```bash
# 프로젝트 폴더에서
python -m venv .venv
.venv\Scripts\activate   # Windows
# source .venv/bin/activate  # macOS/Linux

pip install PyQt6 pyqtgraph numpy pyserial

python main.py
```

1. 시리얼 포트 선택 후 **START**로 수신 시작  
2. **STOP**으로 종료

---

## 시리얼 프로토콜

**프레임: 23 bytes**

| 구간 | 길이 | 설명 |
|------|------|------|
| 헤더 | 2 bytes | 프레임 식별 |
| 데이터 | 20 bytes | 5×4 (예: 4채널 RAW 등) |
| 체크섬 | 1 byte | XOR |

- 체크섬: 헤더+데이터에 대한 XOR 체크섬.

---

## 문서

- **모듈 역할, 코드 흐름, 동적 스케일링** 등 개발자용 상세 내용 → [MODULES.md](MODULES.md)

---

## 라이선스

프로젝트 정책에 따릅니다.
