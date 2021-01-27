2016년 1월 1일부터 2021년 1월 26일 까지의 젬벡스 주식 변동 데이터를 가지고 2021년 1월 27일부터 2021년 2월 5일까지의 주식 종가 변동을 예측하였습니다.

달러 변동 csv파일은 [Investing.Com](https://kr.investing.com/equities/gemvax-kael-co-ltd) 에서 다운받았습니다.

Date, Open, High, Low, Volume, Close 중에 Open, High, Low 값을 입력으로 주고 Close 값을 예측할 출력으로 잡았습니다.

RNN과 LSTM을 이용해서 Train 80%와 Test 20%로 나누어 학습을 진행하였습니다.

RNN보다 LSTM에서 조금 더 좋은 성능을 내는 것으로 확인하였습니다.

RNN ) MSE Evaluate : 0.006103877968566969

LSTM ) MSE Evaluate : 0.008207169130269639

기존에 있던 Train과 Test셋을 가지고 오늘부터 10일 간의 주식 종가값도 예측해보았습니다.

기존 전체 시계열 데이터셋에서 맨 뒤의 7일을 window size로 정하고 그 데이터를 가지고 내일의 Close 값을 정해줍니다.

그 후 내일의 Close 값을 내일의 Open, High, Low, Close에 넣어주고 내일 모레의 Close 값은 저장된 내일의 Open, High, Low 값을 가지고 LSTM 모델(model 2)에 넣어 예측해줍니다.

2021년 1월 27일 부터 2021년 2월 5일까지 예측한 값을 그래프로 그린 것은 아래와 같습니다.

![젬벡스](https://github.com/17011813/GemVax-Prediction/blob/main/2.PNG)

위 그래프는 실제(actual)값에 이어서 예측된(future)값을 연결해주었습니다.
