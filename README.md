# 국내 (상급)종합병원 경영성과 대시보드 제작

<p align = 'center'><img src = 'https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/assets/125945387/9c8b3a72-bbaf-4ef1-8538-22fab640a523' width = 80%></p>

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
  * **기관명 및 주소 정보**
    본 프로젝트에서는 동일 지역 내 병원 간 의료이익을 비교하는 지도 시각화를 수행하고자 함
    수정한 주소 정보와 공간산업진흥원의 Geocoder API를 활용, 위도 및 경도 데이터를 추가 수집함
    * **동일한 주소의 기관명이 연도별로 다른 경우 최근 기준으로 통일**
      ```
      예) 경상남도 진주시 강남로 79에 위치한 상급종합병원의 이름을 아래와 같이 변경
      ```
      <table>
       <tr>
        <th align ='center'>연도</th>
        <th align ='center'>기관명(변경 전)</th>
        <th align ='center'>기관명(변경 후)</th>
       </tr>
       <tr>
        <td align ='center'>2021</td>
        <td align ='center'>경상국립대학교병원</td>
        <td align ='center'>좌동</td>
       </tr>
       <tr>
        <td align ='center'>2020</td>
        <td align ='center'>경상대학교병원</td>
        <td align ='center'>경상국립대학교병원</td>
       </tr>
       <tr>
        <td align ='center'>2019</td>
        <td align ='center'>경상대학교병원</td>
        <td align ='center'>경상국립대학교병원</td>
       </tr>
      </table>
    * **동일한 기관의 주소가 연도별로 다른 경우 최근 기준으로 통일**
      ```
      예) 연세대학교 의과대학 용인세브란스병원의 주소 정보를 최신 기준으로 통일
      ```
      <table>
       <tr>
        <th align ='center'>연도</th>
        <th align ='center'>주소(변경 전)</th>
        <th align ='center'>주소(변경 후)</th>
       </tr>
       <tr>
        <td align ='center'>2021</td>
        <td align ='center'>경기도 용인시 기흥구 동백죽전대로 363</td>
        <td align ='center'>좌동</td>
       </tr>
       <tr>
        <td align ='center'>2020</td>
        <td align ='center'>경기도 용인시 기흥구 동백죽전대로 363</td>
        <td align ='center'>좌동</td>
       </tr>
       <tr>
        <td align ='center'>2019</td>
        <td align ='center'>경기도 용인시 처인구 금학로 225</td>
        <td align ='center'>경기도 용인시 기흥구 동백죽전대로 363</td>
       </tr>
      </table>
      
    * **위도 및 경도가 제대로 수집되지 않는 잘못된 주소 수정**
      <table>
       <tr>
        <th align ='center'>기관명</th>
        <th align ='center'>주소(변경 전)</th>
        <th align ='center'>주소(변경 후)</th>
       </tr>
       <tr>
        <td align ='center'>울산대학교병원</td>
        <td align ='center'>울산광역시 동구 방어진순환도로 877</td>
        <td align ='center'>울산광역시 동구 대학병원로 25</td>
       </tr>
       <tr>
        <td align ='center'>고려대학교 안암병원</td>
        <td align ='center'>서울특별시 성북구 인촌로 73</td>
        <td align ='center'>서울특별시 성북구 고려대로 73</td>
       </tr>
       <tr>
        <td align ='center'>현대유비스병원</td>
        <td align ='center'>인천광역시 남구 독배로 503</td>
        <td align ='center'>인천광역시 미추홀구 독배로 503</td>
       </tr>
      </table>
      
  * **컬럼명 수정**
    ```
    회계 데이터에서 상위 계정과 하위 계정간의 관계를 바로 파악할 수 있도록 컬럼명을 수정함
    ```
    * (예제) 수정 전 : Ⅳ.의료외수익 - **1.의료부대수익**
    * (예제) 수정 후 : Ⅳ.의료외수익 - **Ⅳ-1.의료부대수익**

---
### ③ 1차 대시보드 제작

<p align = 'center'><img src = 'https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/assets/125945387/b37a909f-a5fd-430d-8e15-42d8bdde5d90'></p>

* 대시보드는 [Tableau Public Link](https://public.tableau.com/app/profile/.39367464/viz/_16962095774100/HospitalFinancialAnalysis)를 통해서도 확인하실 수 있습니다.
* 대시보드는 각 항목별로 아래와 같은 정보를 제공함
  1. **지역(시도, 시군구) 내 병원 간 의료이익 비교**
     ```
     상단의 시도, 시군구를 선택했을 때, 선택 지역 병원의 의료이익을 원의 색상, 크기로 비교할 수 있음
     예) 경기도 고양시에는 6곳의 (상급)종합병원이 있고 인제대학교 일산백병원의 의료이익이 가장 큼
     ```
  2. **의료수익경상이익률 비교**
     ```
     기관명을 선택했을 때, 해당 기관의 의료이익경상이익률을 동급 평균과 비교할 수 있음
     최근 대형 병원의 새 먹거리로 떠오른 연구 수익 등 기타 매출 사항을 해당 지표로 가늠할 수 있음
     ```
     관련 기사 : ["연구 수익으로 진료에 투자"··· 고대의료원, '초격차 연구중심 도약'](http://www.doctorstimes.com/news/articleView.html?idxno=222697)
  3. **연도별 의료이익률 추이**
     ```
     기관명을 선택했을 때, 2019 - 21 회계연도 해당 기관의 의료이익률 증감을 확인할 수 있음
     0을 기준으로 선의 색깔이 달라지고, 절대값에 따라 두께가 변하기 때문에 쉽게 이해할 수 있음
     ```
  4. **2021 회계연도 의료수익 대비 비용 비교**
     ```
     기관명을 선택했을 때, 2021 회계연도 의료수익 대비 인건비/재료비/관리운영비를 확인할 수 있음
     의료수익 대비 비용이 동급 평균에 비해 높으면 편차를 적색으로 표시해 개선 필요성을 부각함
     예) 국립암센터의 의료수익 대비 재료비는 40%로 동급 평균 25%에 비해 15%p 가량 높아 개선 필요
     ```

---
### ④ 향후 진행 계획

<p align = 'center'><img src = 'https://github.com/TAEJIN-AHN/Hospital-Profit-Visualization/assets/125945387/ae220ef7-9c43-4a7a-bc83-418863aa10e3' width = 70%></p>
