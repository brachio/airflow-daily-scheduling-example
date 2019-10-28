# airflow-daily-scheduling-example!

airflow에서 daily schedule이 동작하는 예시를 기록한다.

다음 상황에서 테스트된 것을 기록한다.
> airflow.cfg에 timezone setting이 Asia/Seoul로 세팅되어있다.

> airflow의 구동되는 가상환경에는 arrow 모듈이 설치되어있다. pip install arrow

> airflow의 DAG으로 등록 후, DAG을 ON(구동)시킨 시간은 2019-10-28일 오후 11시 58분(KST) ~ 2019-10-29일 오전 12시 30분(KST)이다.

결과는 아래와 같다.
> 26일과 27일 날짜에 대해서만 동작한다.

- 26일 날짜
    - 26일 날짜에서 airflow에서는 UTC시간만 다루므로, UI에서는 RUN: 2019-10-26T14:00:00+00:00으로 보인다.
    - check111과 check222 사이에 2019-10-26T14:00:00+00:00이 찍힌다.
    - 마지막에 2019-10-26T23:00:00+09:00가 찍힌다. 

- 27일 날짜
    - 27일 날짜에서 airflow에서는 UTC시간만 다루므로, UI에서는 RUN: 2019-10-27T14:00:00+00:00으로 보인다.
    - check111과 check222 사이에 2019-10-27T14:00:00+00:00이 찍힌다.
    - 마지막에 2019-10-27T23:00:00+09:00가 찍힌다. 
    
DAG의 schedule interval을 매일 특정시간으로 만들고 싶을 때,schedule_interval과 start_date를 어떻게 설정하면 되는지 알 수 있다.

그리고 2019-10-28T23:00:00+09:00를 볼수 있는 것은 29일 오후 11시가 될 것이다.
