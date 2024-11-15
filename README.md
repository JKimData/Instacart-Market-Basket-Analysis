# 🛒 Instacart Market Basket Analysis
> **RFM 분석 기반 세분화 전략 및 머신러닝 기반 재구매 예측**
> Advisor: 민형기 교수님(한양대학교)

### 📌 프로젝트 소개
- 이 프로젝트는 Instacart의 시장 장바구니 데이터를 분석하여 고객의 구매 패턴을 파악하고, 이를 바탕으로 고객 세분화 및 맞춤형 전략을 제시하는 것입니다. Instacart는 미국의 온라인 식료품 쇼핑 플랫폼으로, 고객 데이터를 분석해 더 나은 마케팅 전략과 추천 시스템을 제공합니다. RFM 분석과 머신러닝을 활용해 고객 세분화와 재구매 예측을 통해 사용자 만족도와 비즈니스 성과를 높이는 것을 목표로 합니다.

### 💻 프로젝트 링크  
- PPT 자료 첨부 자료 확인
- Machine Learning 코드 첨부 자료 확인
- kaggle Instacart Market Basket Analysis [LINK](https://www.kaggle.com/c/instacart-market-basket-analysis) 

# 📑 프로젝트 결과 소개

### **1️⃣ 데이터셋 분석 및 전처리** 

**✔ 데이터 전처리**
- Dataset 총 6개 파일로 구성
- orders 고객 주문 데이터 | departments 대분류 상품 데이터 | aisles 중분류 상품 데이터 | products 상품정보, 종류 정보 | order_products_prior 이전 주문 데이터 | order_products_train 모델 훈련 데이터
![image](https://github.com/user-attachments/assets/2b010283-70a9-404d-b7e7-69e1db879391)

**✔ 데이터 전처리**
- Null 값 확인후 컬럼 특성 확인 후 0으로 변경
- Numerical, Categorical 컬럼 확인하여 타입 변경
- 데이터가 부족한 ID 확인 후 1건 삭제

___


### **2️⃣ 데이터 분석**

**✔ 데이터 탐색**(*PPT 일부*)

![image](https://github.com/user-attachments/assets/f7117816-a38a-4eef-81fe-4ace585be542)
![image](https://github.com/user-attachments/assets/3e8b4078-99c0-4fe5-b0d3-a62c475721a8)
___

### **3️⃣ RFM 분석을 통한 고객 세분화**

**✔ 파생 변수 생성**
- 고객별로 얼마나 최근에, 얼마나 자주, 얼마나 많은 금액을 지출했는지에 따라 고객 세분화 시도
- kaggle set 에는 금액, 구매시기가 없어 있는 컬럼을 바탕으로 주문한 순서 컬럼과, 다음 주문까지 걸린 기간을 통해 변수 생성
- 컬럼의 신뢰성을 바탕으로 가중치 부여 후 RFM 점수 계산

**✔ K-means 사용하여 고객 분류**
- 유사한 특성을 가진 고객 그룹 식별을 위해 클러스터 수를 설정하여 고객을 분류
- 클러스터 수는 실루엣 계수를 통해 품질 판단 진행
- 클러스터 범위를 바탕으로 RFM 점수를 바탕으로 고객을 나누고 등급 부여
![image](https://github.com/user-attachments/assets/6220e058-c8ac-4d27-8676-f3ed9d68e166)
 
**✔ 고객 세분화별 EDA 진행**(*PPT 일부*)
- 고객특성별로 고객 분석 진행
![image](https://github.com/user-attachments/assets/881088a4-ba0b-4641-8504-032a8f6217ab)
![image](https://github.com/user-attachments/assets/a5929aed-6475-4f61-a2e9-09a5edb60210)
___

### **4️⃣ 재구매 예측 모델(머신러닝)**

**✔ Feature Engineering**
- 고객 중심 기반으로 Features 를 생성하여 사용
![image](https://github.com/user-attachments/assets/9b836447-3b24-4c51-931d-31ff1c57f783)

**✔ Modeling & Evaluation**
- 심한 데이터 불균형으로 SMOTE 오버샘플링을 Train 세트에 적용하여 'reordered'에 0과 1 데이터 비율을 맞춤
- 이후 StandardScaler 를 사용하여 표준화하고, CatBoost, XGBoost, LightGBM 을 모두 이용하여 머신러닝 진행
- 최종 모델 성능 결과, CatBoost 모델이 약 93.6% 가장 높은 정확도로 재구매 예측이 가능함
  (머신러닝 코드는 맨 위의 링크에서 확인 가능)
![image](https://github.com/user-attachments/assets/078d8fe1-4cae-4fc9-a8d9-ef95a3da8d07)

___

### 5️⃣ 결론 및 제안
 - 세분화된 고객 데이터를 바탕으로 각 그룹에 맞게 분석 결과 전달 및 전략 제안(마케팅을 위한 최적화된 시간, 주기, 상품 등)
 - CatBoost를 활용하여, 약 93.6%의 정확도로 재구매 상품 추천 시스템이 가능한 모델 제안

  
