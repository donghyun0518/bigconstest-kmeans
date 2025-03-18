<h1 style="text-align: center;">🏅 2024 AI.데이터 분석활용 빅콘데스트 Ai 데이터 경진대회</h1>
<hr>
<p style="text-align: center;">
    <img src="https://github.com/donghyun0518/bigconstest/blob/main/bigcontest.png" alt="Project Cover" style="width: 600px; border: 1px solid #c9d1d9; border-radius: 8px;">
    <a href="https://github.com/donghyun0518/bigconstest/blob/main/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B6%84%EC%84%9D%EB%B6%84%EC%95%BC_Be%20in.zip%ED%8C%80_%EA%B2%B0%EA%B3%BC%EB%B3%B4%EA%B3%A0%EC%84%9C.pdf" target="_blank">
        <img src="https://github.com/donghyun0518/bigconstest/blob/main/%EB%B9%85%EC%BD%98%EB%B0%9C%ED%91%9C%ED%91%9C%EC%A7%80.png" alt="Project Cover" style="width: 1000px; border: 1px solid #c9d1d9; border-radius: 8px;">
    </a>
</p>

[프로젝트 발표 자료](https://github.com/donghyun0518/bigconstest/blob/main/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B6%84%EC%84%9D%EB%B6%84%EC%95%BC_Be%20in.zip%ED%8C%80_%EA%B2%B0%EA%B3%BC%EB%B3%B4%EA%B3%A0%EC%84%9C.pdf)

## 🔍 프로젝트 개요
- **목적** : 빈집과 전통시장 재활성화를 통한 지역 경제 성장 및 청년층 유입 촉진
- **주제** : 빈집과 전통시장을 활용한 지역 활성화 방안 제시
- **기간** : 2024.09.09 ~ 2024.11.15 (약 9주간)
- **팀 구성** : 4인
- **성과** : 본선 진출

## ⚙️ 주요 수행 과정
**1. **문제 정의****
   - 현재 대한민국에는 도시 쇠퇴 문제가 심각함.
   - 이러한 문제는 빈집 문제로 이어지고 있다. 빈집 문제가 방치될 경우 지역 이미지 악화와 부동산 가치 하락을 초래할 수 있음.
   - 지역 경제에 직,간접적으로 영향을 받는 전통시장을 타겟으로 주요 소비층에 대한 자료 수집.
   - 전통시장의 매출지수가 꾸준히 증가하고 있고 이는 전통시장이 2030세대에게 매력적인 공간으로 발전할 가능성을 보여줌.
   - 쇠퇴 지역의 개선을 위한 빈집 활용 가능성과 전통시장의 성장 가능성을 연결하여 지역 경제 활성화 방안 모색.
 
 **2. **데이터 수집 및 전처리****
 - 데이터 출처 : 문화 빅데이터 플랫폼, 한국정보통신진흥협회(SK 텔레콤), 소규모 & 빈집정보 알림e, 행정안전부
    - 데이터 수집
      - 전통시장 역세권 정보
      - 리뷰 크롤링 정보(시장별)
      - 행정동별(성별, 연령별) 유동 인구 (SK 텔레콤 제공)
      - 성별 연령별 거주인구
      - 시군구 별 빈집 현황
      - 전국 읍면동별 경계 데이터
      - 활성화지역진단지표
    - 전처리 작업
      - 리뷰 평점을 반영하기 위해 크롤링 코드 작성
      - 전통시장 역세권 정보 데이터의 잘못 기입된 컬럼 제거
      - 군집분석을 위한 하나의 데이터셋으로 통합
      - 시장 활성화 수준 파악을 위한 파생변수 생성
     
 
 **3. **군집 분석 모델 선정****
 - **모델 선정** : K-Means, DBSCAN, Spectral
    - **모델 적용 분석 과정**
      - 시장 특성, 거주 특성, 지역 쇠퇴 특성, 유동 인구 특성, 시장 활성화 수준을 포함하는 데이터셋을 가공 및 생성
      - 핵심 특성을 분석 변수로 결정
      - 비선형적 데이터 특성을 유지하면서 고차원 데이터를 저차원 공간으로 투영하여 차원의 저주를 방지하기 위해 UMAP 기법을 사용해 차원 축소.
      - 데이터 간의 유사성을 측정, 상호 유사성 높은 대상을 동일 집단으로 분류하는 모델 선정 (K-Means, DBSCAN, Spectral)
      - 실루엣 점수와 군집 간 일관된 분산을 고려하여 군집화 모델 채택
    - **평가 지표**
      - 모든 모델에 동일한 평가 지표 사용
      - **Elbow method(엘보우 기법)**
        - 데이터의 복잡성을 더 잘 반영할 수 있는 군집 내 오차 감소가 완만해지기 시작하는 K 값 채택
      - **Silhouette Score(실루엣 점수)**
        - 엘보우 기법을 통해 확인한 K 값을 바탕으로 점수가 가장 높은 값을 가지는 K값 채택
        - K-Means : 0.415
        - DBSCAN : 0.213
        - Spectral : 0.4
        - 최적의 실루엣 점수와 군집 간 일관된 분산을 고려하여 K-Means 모델을 군집화 기법으로 선정!
 
 **4. **군집 선정 및 시장 선정****
 - 지역 활성화 가능성이 가장 높은 군집을 선정하여 군집 내 데이터 분포를 세부 분석
    - **활성화 가능성이 높은 군집 조건**
      - 점포당 종사자수 많음
      - 빈 점포 적음
      - 리뷰점수 일정 수준 이상
      - 빈집 비율이 높음
    - 위 조건들을 바탕으로 분석했을 때 가장 적합한 군집인 **'군집2'**를 선정
    - **시장 선정**
      - 시장 선정 기준
        - 군집 내 시장들 중 도시 **쇠퇴지역 지정 기준**을 만족하는 시장
 
 **5. **주요 소비 타겟층 선정****
 - SK 텔레콤이 제공한 행정동별 유동 인구 데이터를 사용하여 각 시장이 있는 지역의 유동 인구를 파악.
 - 주요 소비 타겟층을 20-30대로 선정
 
 **6. 토픽 모델링(LDA)**
 - 주요 소비 타겟층의 선호도 파악을 위한 토픽 모델링 수행
 - **LDA**
   - 텍스트 데이터를 자동 분석해 잠재적 주제를 추출하는 도구
   - 문서 간 연관성과 주제 흐름 파악에 유용
   - 개인의 경험과 감정이 담긴 블로그 게시물을 크롤링하여 2030세대의 트렌드 파악
 
 **7. 결론**
 - **주요 소비 타겟층 트렌드**
      - 전통과 현대적 감각을 동시에 추구
      - 특별한 경험과 콘텐츠 소비를 선호
      - 지속 가능한 소비를 중시
 - **활용 방안**
      - 지역 특성을 활용한 로코노믹 상품 개발
      - 빈공간을 판매처로 활용하여 전통시장과 지속적인 상생 관계 형성
 
 **8. 기대효과**
 - 빈집 문제 해결과 지역 균형 발전을 통해 정부 정책 목표 달성
 - 빈집 리모델링으로 지역 시장 인근 이미지 개선 및 흉흉한 분위기 해소
 - 다양한 협업 기회 제공 및 상권 활성화 촉진으로, 지역 경제 활성화 기여
 - 매출 경로를 새롭게 창출하여 상인들의 수익 증대 기대
 - 지역 인구 일자리 창출 기회
 - 전통과 현대가 유합되어 새로운 경험 제공
 - 체험형 프로그램과 팝업 스토어로 청년 세대의 관심 및 유입 촉진
 - SNS 등을 통한 다양한 소비 경험 제공으로 만족도 상승
 
 
 ## 🧑🏻‍💻환경
 - Python
 - VScode
