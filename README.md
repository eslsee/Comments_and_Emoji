# Comments_and_Emoji

2019-12-22 
<네이버 뉴스 크롤링 진행 상황>
-자료 구성 :
요일, 링크, 제목, 댓글내용

-크롤링 과정 :
1 ) 날짜별* 네이버 랭킹 뉴스 수집
2 ) 제목에 ‘타다’ 들어있는 기사 추출
3 ) 각 기사별 댓글 수집

              * 서비스 출범일 (2018.10.08)부터 
                 법령 발의 기준일(2019.12.07) 이
                 후 현재 날짜까지(미정)
TO-DO
-RD 모델 적용 방안 구상 :
법령 발의 기준일 전후 비교 후 예측하기(?)
-그 외 적용 가능 방안 탐구 : 
I ) text analysis를 통한 신문사별 댓글 긍정/부정 비율 분석
II) 특정 신문사의 기사 중 법령 발의 기준일 전후 비교


2019-12-23 
<네이버 뉴스 크롤링 완료>
-csv로 저장
-그 외 적용 가능 방안 탐구 : 
I ) text analysis를 통한 신문사별 댓글 긍정/부정 비율 분석 
	i. 데이터 전처리
	ii. 형태소 분석(꼬꼬마)
	iii. 감정 분석 

II) 특정 신문사의 기사 중 법령 발의 기준일 전후 비교


2019-12-27 
I ) text analysis를 통한 신문사별 댓글 긍정/부정 비율 분석 
한국어 형태소 분류기 konlpy 설치 완료

2019-12-30 이은성
I ) text analysis를 통한 신문사별 댓글 긍정/부정 비율 분석 
한국어 감정 사전 KNU 적용해 긍정/부정 비율 점수화 

TO-DO
II) 날짜별 평균 (12.07 법 발의 일자 기준)으로 시각화 
(x축 날짜, y축 긍정-부정)

2019-01-02 
I ) text analysis를 통한 신문사별 댓글 긍정/부정 비율 분석 
i. 실제 데이터(12.07~12.13) 넣어 댓글별 감성어 개수 파악
ii. 댓글별 감성어 점수 평균 파악 

2019-01-03 
II) 날짜별 평균 (12.07 법 발의 일자 기준)으로 시각화 
(x축 날짜, y축 긍정-부정)

![image](https://user-images.githubusercontent.com/62871418/95105289-e59e7c80-0771-11eb-9ec0-6ffa13e7e457.png)

TO-DO
-날짜 12.07 전 일주일(1~14) 크롤링해 코드에 대입하기
-RD 모델 적용 방안 구상

2019-01-06 
II) 날짜별 평균 (12.07 법 발의 일자 기준, 전후 일주일(12.1~14))으로 시각화 
(x축 날짜, y축 긍정-부정)

![image](https://user-images.githubusercontent.com/62871418/95105666-71b0a400-0772-11eb-882a-01dd243b72cb.png)

2019-01-09
III ) 적용 가능 모델 탐구
i . Regression Discontinuity
긍정/부정 나눠서 
ii. ARIMA


2019-01-09
III ) 적용 가능 모델 탐구
날짜별 box-plot 

![image](https://user-images.githubusercontent.com/62871418/95105720-8856fb00-0772-11eb-86b3-bae967a06b12.png)

2019-01-29
III ) 적용 가능 모델 탐구
iii-1. 기사 내 감정 비율과 댓글 긍정/부정 비율 비교 

![image](https://user-images.githubusercontent.com/62871418/95105901-c3f1c500-0772-11eb-950e-01080658e4f5.png)

iii-2. 기사 내 감정 비율과 댓글 긍정/부정 비율 정확도 측정
기사 : (좋아요 + 훈훈해요) / (좋아요 + 훈훈해요 + 화나요 + 슬퍼요)
댓글 : 긍정 / (긍정 + 부정) 

0.5 이하 확률 74% (0.741379)
부정 정확도 74%


ARIMA
(0,2,1)

![image](https://user-images.githubusercontent.com/62871418/95105971-d9ff8580-0772-11eb-9749-76e772273ff7.png)

![image](https://user-images.githubusercontent.com/62871418/95106022-ebe12880-0772-11eb-8085-ad5dd7867928.png)

![image](https://user-images.githubusercontent.com/62871418/95106058-fa2f4480-0772-11eb-815e-1fd73393a5de.png)

(0,2,0)

![image](https://user-images.githubusercontent.com/62871418/95106120-0f0bd800-0773-11eb-8970-3ca4a23fba50.png)

missing values filled by mean 

![image](https://user-images.githubusercontent.com/62871418/95106156-1c28c700-0773-11eb-9037-effbd63380c9.png)

missing values filled by median

![image](https://user-images.githubusercontent.com/62871418/95106199-2ba81000-0773-11eb-8db5-5da85a7f8b9f.png)

other methods

![image](https://user-images.githubusercontent.com/62871418/95106244-3cf11c80-0773-11eb-98b0-e97e1fc3d19b.png)

![image](https://user-images.githubusercontent.com/62871418/95106298-4bd7cf00-0773-11eb-90c2-4c5a7a27c919.png)

Holt Winter

![image](https://user-images.githubusercontent.com/62871418/95106335-5b571800-0773-11eb-98aa-95a5acade0e3.png)

naive forecast

![image](https://user-images.githubusercontent.com/62871418/95106387-6a3dca80-0773-11eb-9203-3231a0fa64a5.png)

Average Forecast

![image](https://user-images.githubusercontent.com/62871418/95106446-7cb80400-0773-11eb-850f-74da0be133bc.png

Moving Average

![image](https://user-images.githubusercontent.com/62871418/95106485-8c374d00-0773-11eb-96dd-547534d7449b.png)

Holt Linear

![image](https://user-images.githubusercontent.com/62871418/95106534-9b1dff80-0773-11eb-91c9-3d6834df84a4.png)

till February

![image](https://user-images.githubusercontent.com/62871418/95106598-ac670c00-0773-11eb-8f30-25637817e2f1.png)

![image](https://user-images.githubusercontent.com/62871418/95106645-b983fb00-0773-11eb-9eb1-7a2dcccf84df.png)
















