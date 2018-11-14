RNN을 활용한 배추가격 예측 AI모델
==========================================
Use Tensorflow
--------------
****
# 내용
* 10년의 날씨+가격 데이터 학습 후 예측
* 7일 단위로 학습데이터가 들어간 후 8일째를 예측 
* 예측 범위를 늘리기 위해 실제 8일째 데이터 대신 예측된 8일째 데이터를 주입 후 다음 7일 반복
****
# 결과
처음 7일의 데이터를 학습 후 8일째 즉 하루만을 예측하는 모델을 구현했는데 예측결과가 매우 잘 맞았다. 이유는 배추 가격이 일일간의 변동폭은 매우 적고 월별, 분기별 가격변동이 큰 상품이기 때문으로 생각된다.

그래서 예측 범위를 하루가 아니라 무한대로 늘리기 위해 8일째 **예측된 결과**를 **실제 8일째 데이터**에 주입 하여 8번의 예측 후에는 전부 예측된 데이터들로만 이루어진 데이터셋으로 예측을 진행하는 모델로 구축하였다.

결과는 약 3개월까지 괜찮은 예측률을 보여주다 급락하는 것을 보인다.
아래는 10년간의 데이터를 학습한 후 1년간의 데이터를 예측한 결과이다.
빨간색은 실제 배추 가격 데이터이고 파란색이 예측한 결과 값이다.

![cost1](https://t1.daumcdn.net/cfile/tistory/99500E455BEBB02912 "10년간의 데이터 학습 후 1년 치 예측")

![cost2](https://t1.daumcdn.net/cfile/tistory/991BB6455BEBB02914 "확대모습")
* * *
# 정리
이번 프로젝트는 배추 가격과 무 가격 두가지 데이터를 작성한 RNN모델에 트레이닝 및 예측을 해보았다.
두 작물 모두 약 3개월을 기점으로 예측률이 급격하게 하강하는 것을 알 수 있는데 이러한 예측 범위 한계를 늘리기 위해서는 데이터셋의 정제가 필요하다.
현재는 해당하는 날짜의 기온,습도,강수량,풍향 등 기상정보와 그 날짜에 따른 작물 가격만으로 데이터셋을 구성한다.
하지만 농작물 가격에 영향을 끼치는 요소는 그것보다 더 다양하기 때문에 그에따라 맞는 데이터는 추가하고 영향력이 적은 데이터는 없애는 작업이 반드시 필요하다고 생각된다.
* * *
# 참고문서
* [모두를 위한 딥러닝 강좌 시즌1](https://www.youtube.com/watch?v=BS6O0zOGX4E&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm)
* [TensorFlow KR](https://www.facebook.com/groups/TensorFlowKR/)
* [기상청](http://www.weather.go.kr/weather/main.jsp)
* [농업관측통계정보시스템](http://oasis.krei.re.kr/index.do)
