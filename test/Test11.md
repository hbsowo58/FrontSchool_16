# 프론트엔드 16기 - JAVASCRIPT QUIZ 11

Q) 아래 코드를 보고, 결과값을 작성한 후 결과값이 나오는 이유를 그림을 아시는만큼 설명하세요. 뒷면을 활용하세요 (결과값 25점, 이유25점, 실행컨텍스트 그림 50점)(평가는 생략하고 코드가 실행된 이후시점을 그려주시면 됩니다.)
키워드 : 전역실행컨텍스트, outer함수실행컨텍스트, inner함수실행컨텍스트
렉시컬 환경,전역렉시컬환경,전역환경레코드, 외부 렉시컬 환경에 대한참조,객체환경레코드 BindingObject, 선언적환경레코드,전역객체,[[GlobalThisValue]], [[ThisValue]],함수환경레코드,outer,inner환경레코드, argumnent, 

function object



![img](https://lh6.googleusercontent.com/EQEhE0_X_Z4phjC5h885sRz95agVEpK0yvL9iBsDZc_ykXI_61n72mifhrsUD3a1vu03vuheVe1d85lR-AHwzWSfX9jhClduYk2vY-jeSokC0ae36ZqAr_khN7sJWqhDf_mTJ6ZZ)

<br>

답:27

다평가 및 실행된후 console.log실행될때(a:1 b:4, c:2 , d: 9, e5, f:6) e,f는 inner 환경레코드 존재 abcd는 outer 환경레코드존재
 foo-> outer bar -> inner (수정못함)

![img](https://lh5.googleusercontent.com/cFFj-mArUBXfamsSOM2NG_2D3IRy4qrW9qxrR0uudLpyeev_6jG4VfCX4sKWQw9aE3U-9LHBqo4oDhiD6bj26E-olNGkzhlq_MsrgX8HnwYgMIsSh1AeDBqzZQXMIeOx5Idf7Lhr)