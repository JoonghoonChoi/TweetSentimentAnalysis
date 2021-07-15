[Go to presentation slide file](https://drive.google.com/file/d/1V1TRaSqLwjVOL0PGyRuDxgao-79WLEOk/view?usp=sharing/)

# 뉴스 헤드라인 감성분석 프로젝트

## 프로젝트 기획 배경

<img width="580" alt="Screen Shot 2021-07-15 at 14 28 33" src="https://user-images.githubusercontent.com/74339882/125733759-32379d07-f2c7-45b6-a203-a4f20464b9b7.png">

### 문제제기
자극적이고 부정적인 헤드라인의 기사는 사회의 차별과 혐오를 조장할 것이다
### 가설설정
사용자 입장에서 긍정 혹은 부정적인 헤드라인의 기사를 분류하여 접할 수 있다면 무분별한 혐오, 차별성 기사를 걸러 볼 수 있지 않을까?
### 해결과제
뉴스 헤드라인 텍스트 감성분석(Positive/Neutral/Negative) 및 분류 모델

<br>

## 프로젝트 결과
> Baseline model
- TF-IDF 스코어를 사용한 Logistic regression model
- Accuracy: 0.56
> LSTM
- Accuracy: 0.76
- 5-fold cv 결과<br>
  5-fold cv mean: 77.83%<br>
  5-fold cv std: +/-0.70%
> **LSTM model tuning**
- Accuracy: **0.79**

<br>

## 문제해결 과정
**1. 데이터셋**
- 약 93,000개의 미국 뉴스 데이터셋 사용 (2002 -2016)
- 기사 헤드라인 및 감성스코어 특성 추출
- 감성 스코어에 따른 Positive/Neutral/Positive 라벨 생성
- 문제해결에 적합한 한국어 데이터셋을 구하지 못함: (영어->한국어) 번역과정을 추가하여 모델을 구축하는 것으로 결정

**2. 영문 텍스트 전처리**

**3. LSA(잠재의미분석)을 통한 각 클래스의 분포 확인**

<img width="343" alt="Screen Shot 2021-07-15 at 14 28 06" src="https://user-images.githubusercontent.com/74339882/125733718-ed33c74c-2a59-4fba-9c93-00706e409c1d.png">

**4. Baseline ML 모델 선정<br>**

: TF-IDF 스코어를 사용한 Logistic Regression 모델을 baseline으로 선정

<img width="464" alt="Screen Shot 2021-07-15 at 14 29 42" src="https://user-images.githubusercontent.com/74339882/125733877-4109b0ee-47e6-4d38-99bb-9a0b8d5cf7e7.png">

**5. DL 모델 학습 및 튜닝**

<img width="403" alt="Screen Shot 2021-07-15 at 14 31 33" src="https://user-images.githubusercontent.com/74339882/125734079-e3cd218d-8a14-4c41-b841-6ad473c54818.png">

**6. 최종모델**

<img width="352" alt="Screen Shot 2021-07-15 at 14 33 58" src="https://user-images.githubusercontent.com/74339882/125734288-4dd6d7fc-78e2-4bd9-b79b-19d41627d16d.png">

**7. 모델 재구현 및 예측 시연**

<img width="840" alt="Screen Shot 2021-07-15 at 14 36 07" src="https://user-images.githubusercontent.com/74339882/125734447-d05b9abb-6511-4cc4-a177-648a9767f399.png">

<br>

## 개선사항
- 하이퍼 파라미터 튜닝 이후에도 학습 epoch가 많이 돌지 못하고 과적합되는 현상이 있는데 아를 해결한다면 성능 향상이 가능할 것이라 생각됨
- BERT 모델을 fine-tuning 후 성능을 추가적으로 비교
- 뉴스와 관련된 한국어 데이터셋을 찾지 못함.
- 어쩔 수 없이 번역API를 사용해서 한국어 감석 분석 진행

<br>


## Data Resources<br>
~~~
News_final.csv: https://archive.ics.uci.edu/ml/datasets/News+Popularity+in+Multiple+Social+Media+Platforms
KCCq28_Q01_txt: http://nlp.kookmin.ac.kr/kcc/
한국어불용어100.txt: https://bab2min.tistory.com/544
data-clean.pkl: Cleaning "News_final.csv" to .pkl(DataFrame)
~~~
