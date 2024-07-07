# Pressure Injury Experiments

본 연구는 경북대학교 병원 성형외과 의료진분들과 경북대학교 병원 인공지능 센터와 함께 진행되었습니다.

# Dataset

<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/d7fb2e75-2452-4141-a919-d3b6c7c44e86">

- 1142 명의 호나자로부터 수집된 33422개의 이미지로 구성

1. 엉덩이 근처 부위에 발생한 욕창 이미지만 별도의 선별 과정 진행
2. 환자의 내원 첫 날 촬영된 첫 번째 이미지 영상 사용
3. 괴사 조직 제거술과 같은 처치가 필요했던 욕창의 경우, 처치 전의 이미지들이 데이터 셋에 포함

- 결과적으로 948명의 환자로부터 948명의 이미지 영상 구성
----
# PipeLine
<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/5497f632-ed57-4944-9f82-07a229689173" width="700" height="370">

CNN Models:
1. ResNet18
2. ResNet50
3. GoogLeNet
4. MobileNetv2
5. DenseNet

Survival Models:
1. Cox Proportional Hazard(CoxPH)
2. Piecewise Exponential (Pw Exp)
3. DeepSurv
4. PC-Hazard
---
# Results

1. Performance metric : Concordance Index (C-index)
<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/0a0694cc-2817-4956-82bc-1fb3d97283c5" width="1200" height="370">

2. Kaplan Meier Curve Estimation
<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/2c684f00-e184-4cdc-a332-acbe10790869" width="700" height="700">
