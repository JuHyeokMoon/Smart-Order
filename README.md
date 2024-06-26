# 판매량 예측 시스템
매장의 재고 관리와 공장의 생산 효율화를 위한 판매량 예측 시스템 개발

# 프로세스 요약
0. 주단위 배치 프로세스
1. 데이터 마트에서 데이터 수집 후 전처리 수행
2. 머신러닝 모델 학습 및 예측
3. 딥러닝 모델을 위한 전처리 수행
4. 딥러닝 모델 학습 및 예측
5. 전주 예측 값과 실제값 비교 검증

# 파일 설명
* darts_main.py (+ darts_main.sh 실행스크립트)
  > 모델 학습&예측, 데이터 가공
* darts_pre_process.py (+ darts_pre_process.sh 실행스크립트)
  > 데이터 마트에서 학습 데이터 수집 및 전처리
* darts_post_process.py (+ darts_post_process.sh 실행스크립트)
  > 매장 별로 상이한 입고일을 기준으로 예측 결과 가공
* darts_verification.py (+ darts_verification.sh 실행스크립트)
  > 주 단위 검증 프로세스
* file_management.sh
  > 과거 데이터 제거 관련 실행 스크립트
* Batch.sh
  > 각 프로세스들의 전체 실행 스크립트

# 특이 사항
1. 낮은 품질의 데이터
   > TF팀을 구성하여 데이터 정합성 신뢰도 확보
2. 예측 대상의 작은 볼륨과 적은 빈도
   > 학습 데이터를 누적합으로 변환하여 학습하고 결과를 후처리하는 방식으로 정확도 높임
3. 많은 수의 매장과 제품의 예측치 요구
   > 각 매장, 제품 별(매장*제품)로 모델을 학습하고 예측하는 방식으로 정확도 높임  
   > 학습 시간에 큰 비용이 발생하여 모델 구조가 단순한 모델을 위주로 반복 테스트
