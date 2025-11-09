# 경량화 기법을 적용한 MLP 기반 IoT 침입 탐지 시스템

## 📋 프로젝트 개요

본 프로젝트는 IoT 환경에서 실시간 네트워크 침입을 탐지하기 위한 경량화된 MLP(Multi-Layer Perceptron) 모델을 개발한 연구입니다. 94%의 모델 크기 감소를 달성하면서도 높은 탐지 정확도를 유지하였습니다.

## 🎯 주요 목표

- IoT 디바이스(Raspberry Pi Zero 등) 환경에서 동작 가능한 경량화 모델 개발
- 실시간 네트워크 침입 탐지 성능 확보
- Progressive Pruning 및 Knowledge Distillation 기법 적용
- TensorFlow Lite INT8 양자화를 통한 모델 최적화

## 📊 모델 성능 비교

| 모델 | ROC-AUC | 추론시간 | 모델 크기 |
|------|---------|---------|-----------|
| 원본 MLP | 0.9717 | 19.43ms | 66.9KB |
| Pruned Teacher | 0.9708 | 19.30ms | 24.7KB |
| Pruned Student | 0.9679 | 19.18ms | 14.5KB |
| INT8 Quantized | 0.9562 | 18.90ms | 3.75KB |

※ 최종 INT8 양자화 모델은 원본 대비 **94% 크기 감소**, ROC-AUC는 **1.6% 감소**에 불과

## 🔧 사용 기술

### 모델 구조
- **1D CNN**: Conv1D + MaxPooling 구조로 시계열 네트워크 패킷 분석
- **XGBoost**: 앙상블 기반 분류 모델
- **MLP**: 50-50-1 구조의 경량 신경망

### 경량화 기법
- Progressive Pruning (30% → 60% sparsity)
- Knowledge Distillation (Temperature=5, Alpha=0.1)
- TensorFlow Lite INT8 Quantization

### 데이터 전처리
- Log Transform 및 Z-score 정규화
- SMOTE를 통한 불균형 데이터 처리
- PCA 차원 축소 (95% 분산 설명)

## 📁 파일 구조

├── 1d_cnn_Model.ipynb # 1D CNN 모델 구현
├── XGB_Model.ipynb # XGBoost 모델 구현
├── traffic_Detection_Model_Lightweighting.ipynb # 경량화 모델 구현
└── 포트폴리오_논문.pdf # 프로젝트 상세 문서

text

## ⚠️ 주의사항

**traffic_Detection_Model_Lightweighting.ipynb 실행 관련:**
- 본 파일은 `TensorFlow Addons`를 사용합니다
- TensorFlow Addons는 2024년 5월 이후 개발이 종료되었으며, 최신 버전의 Google Colab에서는 **실행이 불가능**합니다
- 로컬 환경에서 TensorFlow 2.x 및 호환 가능한 TensorFlow Addons 버전 설치 후 실행을 권장합니다

## 🚀 실행 방법

### 1D CNN 및 XGBoost 모델
데이터 로드 및 전처리
SMOTE 오버샘플링 적용
모델 학습 및 평가
text

### 경량화 모델 (로컬 환경 권장)
필요한 패키지 설치
pip install tensorflow==2.11.0
pip install tensorflow-addons==0.19.0
pip install scikit-learn pandas numpy

Jupyter Notebook 실행
jupyter notebook traffic_Detection_Model_Lightweighting.ipynb

text

## 📈 데이터셋

- **CIC-BCCC-NRC**: 84개 피처를 가진 IoT 침입 탐지 데이터셋
- **ACI-IoT-2023**: IoT 환경 네트워크 트래픽 데이터

## 👨‍💻 개발자

[귀하의 정보]

## 📝 라이선스

[라이선스 정보]

---

**Note**: 본 프로젝트는 IoT 보안 연구 목적으로 개발되었으며, Raspberry Pi Zero 등 리소스 제한 환경에서의 실시간 침입 탐지를 목표로 합니다.