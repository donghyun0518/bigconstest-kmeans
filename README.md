<h1 style="text-align: center;">🚲 제 5회 세종특별자치시 빅데이터 분석 아이디어 공모전</h1>
<hr>
<p style="text-align: center;">
    <img src="https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/sejong.png" alt="Project Cover" style="width: 600px; border: 1px solid #c9d1d9; border-radius: 8px;">
    <a href="https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/%EC%84%B8%EC%A2%85%EC%8B%9C%20%EA%B3%B5%EB%AA%A8%EC%A0%84%20%EC%B5%9C%EC%A2%85.pdf" target="_blank">
        <img src="https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/%EC%84%B8%EC%A2%85%EC%8B%9C%ED%91%9C%EC%A7%80.png" alt="Project Cover" style="width: 1000px; border: 1px solid #c9d1d9; border-radius: 8px;">
    </a>
</p>

[프로젝트 발표 자료](https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/%EC%84%B8%EC%A2%85%EC%8B%9C%20%EA%B3%B5%EB%AA%A8%EC%A0%84%20%EC%B5%9C%EC%A2%85.pdf)

## 🔍 프로젝트 개요
- **목적** : 세종시 출퇴근 시간대 교통 체증 완화를 통한 시민의 삶의 질 향상
- **주제** : 세종시 공공 전기자전거 도입을 위한 거치대 최적 입지 선정
- **기간** : 2024.08.09 ~ 2024.09.30 (약 7주간)
- **팀 구성** : 4인
- **성과** : 본선 진출

## ⚙️ 주요 수행 과정
**1. **문제 정의****
   - 출퇴근 시간대 도로 정체로 인한 시민들의 불편함 존재.
   - 도로 정체로 인한 운전자들의 스트레스 증가.
   - 공공자전거(어울링)의 도입으로도 도로 정체가 해결되지 않고 있는 것을 확인함.
   - 기존 공유전기자전거(일레클)의 이용률이 증가하는 것을 확인하였고, 이 공유전기자전거의 이용, 관리 및 주차 문제가 있다는 시민의 불편함을 확인하여 이를 개선하고자 분석을 진행.

**2. **데이터 수집 및 전처리****
   - 데이터 출처 : 공공데이터 포털, 세종시 교통 빅데이터분석 시스템, KOSIS 국가통계포털
   - 데이터 수집
     - 세종 포스트 기사 크롤링
     - 세종시 횡단보도 위치 데이터(구글 어스)
     - 세종시 주차장 정보
     - (국토교통부)행정동 경계 정보
     - 어린이 보호구역 정보
     - 도로 구간별 통행속도
     - 버스 정류장 및 버스 정류장별 노선 수
     - 일레클 이용률 데이터
     - 자전거 이용률 데이터
     - 어울링 및 일레클의 만족도 조사 결과
   - 전처리 작업
     - 문제 시각화를 위한 도로 구간별 통행 속도 전처리
     - 정류장, 주차장, 횡단보도 위치 좌표 가져오기
     - 군집 분석에 사용할 컬럼 생성 및 데이터셋 제작

**3. **군집 분석 모델 선정****
   - 모델 선정 : K-Means, MCLP, OPTICS
   - 모델 적용 분석 과정
     - 총 14개 행정동에 대해 입지 선정 분석 진행.
     - K-Means 군집 분석을 하기 위한 변수 선정( 버스정류장 / 횡단보도 위치 / 버스 정류장별 노선 수 / 주차장 )
     - K-Means 군집 결과를 기반으로 K 값을 선정하여 MCLP 기법 적용. 최대한 많은 수요를 커버할 수 있는 최적의 위치를 선정
     - MCLP 기법을 적용한 후 평가기준에 만족하지 못하는 행정동에 대해서 OPTICS 기법을 적용하여 입지를 선정.
   - **평가 지표**
     - K-Means : Elbow Method(엘보우 기법), Silhouette Score(실루엣 점수)
       - 공공 전기자전거 거치대 수를 각 동의 지역적 특성에 맞는 최적의 수를 반영하기 위해 각 행정동의 어울링 거치대 수를 K값으로 설정.
       - 실루엣 점수가 0.5이상인 지점을 K값으로 설정.
       - 0.5이하라면 지정한 K값에서 0.5이상으로 도달한 가장 가까운 지점을 K값으로 설정.
     - MCLP : Coverage ratio(커버리지 비율)
       - 실루엣 점수가 0.5이상이면서 커버리지 비율이 0.7이상인 행정동 선정
     - OPTICS : Silhouette Score(실루엣 점수)
       - 앞선 모델들의 평가 기준을 만족하지 못하는 행정동에 대해서 OPTICS 모델을 적용.
       - 나머지 행정동의 실루엣 점수가 0.5를 넘기는 것을 확인.

**4. **분석 결과****
   - 총 8개의 행정동에 대해 MCLP 모델을 적용.
   - 총 6개의 행정동에 대해 OPTICS 모델을 적용.
   - 위 두 모델을 적용하여 공공전기자전거 거치대 최적 입지를 선정.

**5. **기대 효과****
   - 세종시 교통 체증 완화
   - 세종시가 차 없는 도시라는 이미지에 더 가까워질 수 있음.
   - 궁극적으로 세종시 시민의 삶의 질 향상을 기대할 수 있음.


## 🧑🏻‍💻환경
- Python
- VScode

