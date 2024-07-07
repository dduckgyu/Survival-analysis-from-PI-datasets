# Pressure Injury Experiments

본 연구는 경북대학교 병원 성형외과 의료진분들과 경북대학교 병원 인공지능 센터와 함께 진행되었습니다.

# Dataset

<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/d7fb2e75-2452-4141-a919-d3b6c7c44e86">

- 1142 명의 환자로부터 수집된 33422개의 이미지로 구성

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
1. Cox Proportional Hazard(CoxPH) [ Statistic Based ]
2. Piecewise Exponential (Pw Exp) [ Statistic Based ]
3. DeepSurv [ Deep learning Based ]
4. PC-Hazard [ Deep learning Based ]
---
# Results

- Train, Val, Test : 60% 20% 20% 진행

- 생존 : 78.08%

- 사망 : 21.92%

- Data 가 충분하지 않은 문제를 해결하고자 RandomResizedCrop, RandomHorizontalFlip, ColorJitter, RandomAffine 등 활용

-  Statistic - Based 모델들의 경우, image feature extraction 과정 진행 후, 해당 차원을 바로 모델의 입력으로 넣기에 무리가 있다고 판단되어 PCA를 활용하여 설명 가능한 분산의 비율의 최소 90%를 유지하도록 설정하여, 원본 데이터 정보 손실률을 최소화하도록 설계함.


1. Performance metric : Concordance Index (C-index)
<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/0a0694cc-2817-4956-82bc-1fb3d97283c5" width="1200" height="370">

- 모두 Deep learning - Based 모델들이 전반적으로 우수한 성능을 보임을 확인.
- 이것은 Feature Extraction 과정과 Survival Analysis 과정을 End-To-End로 학습을 진행하는 딥러닝 기반 분석이 개개인의 위험 분석 성능을 개선 시킬 수 있음을 보여줌
  
2. Kaplan Meier Curve Estimation
<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/2c684f00-e184-4cdc-a332-acbe10790869" width="700" height="700">

- 모델이 예측한 위험도를 기준으로 고위험:파란색, 중위험:녹색, 저위험:빨간색으로 나눈 후, 신뢰구간 95% 설정하여 환자들의 생존 예측률에 직관적인 이해를 돕고자 카플란 마이어 커브 활용
- 딥러닝 기반 모델들이 전반적으로 위험 그룹간의 유의미한 차이를 보여주는 것을 확인.

3. Log Rank Test

<img src="https://github.com/gyugyukim/Survival-analysis/assets/135569056/37e8d2fd-2f23-4dea-8720-d565320e345e">

- 위험 그룹 간들 사이에 예측된 생존 예측률이 통계적으로 유의미한 차이가 존재하는 지 확인하기 위해 로그-랭크 검정 추가적으로 진행
