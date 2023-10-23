# 국내 (상급)종합병원 경영성과 시각화

## 요약

### ① 기본정보
* 개인프로젝트 (기여도 100%)
* 데이터 출처 : [한국보건산업진흥원 의료기관 회계정보공시](https://haspa.khidi.or.kr/)
* 2023년 10월 24일 현재 진행 중인 프로젝트입니다.
---

### ② 프로젝트 진행 배경
* 국립암센터 인턴 시절, 기관의 수익 악화 원인을 파악하고자 동일한 주제로 분석을 수행한바 있습니다.
* 그동안 성장한 데이터 전처리 및 시각화 역량을 새롭게 적용해 기존 분석을 한층 발전시키고자 합니다.
---

### ③ 목표
* 본 프로젝트에서는 병원의 경영 성과를 한눈에 파악할 수 있는 태블로 대시보드를 제작하고자 합니다.
* 특히 최근 수익이 악화된 병원의 경우, 대시보드를 통해 그 원인까지 파악할 수 있게 하고 싶습니다.
---

### ④ 주요 액션 및 향후 진행 방향
<p align = 'center'><img src = 'https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/assets/125945387/1c06c124-c7c6-4793-b0b0-a5f6e2c7a9b4' width = 50%></p>

---
## 상세

### ① 1차 데이터 수집
* 자세한 내용과 코드는 [GitHub Link](https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/blob/6d648551ca2cc57fa31cabb69ba15bdf195ea176/data_collection_cleaning.ipynb)를 참고하여 주시기 바랍니다.
* 한국보건산업진흥원 의료기관 회계정보공시의 전국 (상급)종합병원 손익계산서 데이터를 크롤링함
* 2022 회계연도의 데이터는 아직 공개되지 않은 상태로, 2019 - 2021 회계연도의 자료를 이용하고자 함

---
### ② 데이터 전처리
* 자세한 내용과 코드는 [GitHub Link](https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/blob/6d648551ca2cc57fa31cabb69ba15bdf195ea176/data_collection_cleaning.ipynb)를 참고하여 주시기 바랍니다.
* 주요 전처리 내용은 다음과 같음
  * 기관명 및 주소 정보
    ```
    본 프로젝트에서는 동일 지역 내 병원 간 의료이익을 비교하는 지도 시각화를 수행하고자 함
    수정한 주소 정보와 공간산업진흥원의 Geocoder API를 활용, 위도 및 경도 데이터를 추가 수집함
    ```
    * 
