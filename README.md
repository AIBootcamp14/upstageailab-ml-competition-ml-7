# House Price Prediction / [Team7] : 3I1E

## Team

| ![안희원](https://avatars.githubusercontent.com/u/156163982?v=4) | ![정민지](https://avatars.githubusercontent.com/u/156163982?v=4) | ![김명철](https://avatars.githubusercontent.com/u/156163982?v=4) | ![민병호](https://avatars.githubusercontent.com/u/156163982?v=4) |
|:--------------------------------------------------------------:|:--------------------------------------------------------------:|:--------------------------------------------------------------:|:--------------------------------------------------------------:|
| [안희원](https://github.com/dukduk12) <br> 팀장, DS | [정민지](https://github.com/UpstageAILab) <br> DS | [김명철](https://github.com/UpstageAILab) <br> DS | [민병호](https://github.com/UpstageAILab) <br> DS |


## 1. Competition Info

### Overview

- 🏠 서울 집값 예측 모델 경진대회
  
### Timeline

- 2025년 07월 07일 - 11일: 데이터 EDA 및 전처리
- 2025년 07월 12일 - 13일: Feature Selection
- 2025년 07월 14일 - 17일: 모델 성능 평가 및 선택

### Evaluation

- RMSE (Root Mean Squared Error) = sqrt( (1/n) * Σ (ŷᵢ - yᵢ)² )
– n: 샘플 개수
– ŷᵢ: i번째 예측값
– yᵢ: i번째 실제값

## 2. Components

### Directory
```
project_root/
│
├── 📁 Data/                  # 데이터 관련 모든 파일 저장
├── 📁 Model/                 # 모델 관련 코드 
├── 📁 EDA/                 # EDA 분석 코드
```


## 3. Data description

###📌 Dataset Overview

- **train.csv** : 학습용 데이터셋, 총 약 ‘1,118,822’개
- **test.csv** : 테스트셋 (target 미포함) , 총 약 ‘9,272’’개
- 주요 feature:
	- ‘시군구’, ’층’, ‘건축년도’, ’계약년월일’, ‘전용면적’, ‘번지’
	- Target : ‘거래금액’

### 📊 EDA 요약

1.  **타겟 분포 확인**
	- 가격 분포가 **우측으로 치우쳐 있음 (right-skewed)**
	- 로그 변환 필요성 확인 (`np.log1p()` 사용)
2. **주요 feature와의 관계** 파악
3. **시각화 예시**
- feature 간 correlation heatmap
- 지역 및 층별 graph
- feature importance
### Feature engineering

1. 데이터분석 결과로 피쳐 필터링
2. 도메인 지식을 활용한 파생변수 생성
3 추가 외부 데이터셋 수집 및 가공
4 데이터 분석을 토대로 검증 및 수정
5 Target log transform
6 Split 된 데이터 분포 확인
7 Data Split 방식 : Hold-out, Time-Series, K-fold

## 4. Modeling

### Model result
ensemble (feature-version3) : 17989.8598(public) 11747.9527(private)
surrogate (feature_version8) : 14489.7672(public) 13091.14772(private)
LGB (feature_version8) : 16194.0080(public) 11534.0853(private)

—
## 5. Result

### 🏆 Leader Board

- **순위**: 🥇 **1위**
- **RMSE**: `13091.1472`

![leaderboard_capture](./Asset/outputs/leaderboard.png)

### Presentation

- **[슬라이드 링크](https://docs.google.com/presentation/d/1y9j3IuEFNUOk9efo_rc3oHwK9a3aLjtS/edit?usp=sharing&ouid=112748544747957738479&rtpof=true&sd=true)** (Google Slides or PDF)

- 주요 내용:
  - 데이터 이해 → EDA → 모델링 전략 → 성능 비교 → 결론
—
## 6. 🧾 Conclusion

### 한계 및 향후 개선 방향
- **지역성(Locality)**을 고려한 **공간 기반 모델**(예: Geo-spatial regression, Graph Neural Networks)의 도입 가능성
- 공공데이터 포털, 국토교통부 API 등을 통해 **추가적인 외부 정보**(예: 학군, 인구 밀도, 인근 개발 계획 등) 확보 시 더 정확한 예측 가능
- Surrogate 방법의 시도는 좋았으나 일반화가 부족. Ensemble의 경우 모델이 서로 상호 보완을 하여 성과가 좋았음을 확인
---
### 결론 요약
- 단순한 회귀 문제처럼 보이지만, 지역성과 비선형적 관계가 복잡하게 얽혀 있어 고성능 예측 모델 구성이 필요한 문제
- EDA → 피처 엔지니어링 → 앙상블 모델 구성이라는 전통적인 ML 파이프라인을 통해 **성능과 해석 가능성**을 모두 확보
- 향후 외부 정보 통합과 공간적 관계 고려가 성능 개선의 핵심 포인트
---


- _Insert your meeting log link like Notion or Google Docs_

### Reference

- _Insert related reference_
