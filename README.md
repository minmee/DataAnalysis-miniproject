# DataAnalysis-miniproject

새싹 미니 프로젝트 3조 - 명소연, 안병윤, 안재진, 임종근

## 1. 프로젝트 목적

- 도시 팽창으로 인한 교통혼잡이 증가하면서 고객의 요구와 수요에 대응하는 주문형 서비스인 '온디맨드 서비스'가 급부상함.

- 서울시 Smart Card Data를 활용하여 서울시 내 대중교통 취약지점을 파악하고, 온디맨드 서비스의 최적 입지에 대해 분석하고자 함.

## 2. 데이터

- 주어진 Smart Card Data와 시군구명칭이 있는 데이터파일 seoul_id.csv를 병합함.

- on_area_name 탑승위치가 해당되는 구의 명칭을 데이터에 통합함.

## 3. 전처리

- 우회계수(Circuity Factor) : 도로 교통망의 직결성 측면에서의 효율성을 판단하는 기준으로 사용됨.

![image](https://user-images.githubusercontent.com/97076352/168974306-2c7bced1-befa-4039-baac-058352152299.png)

즉, 실제 거리(네트워크 거리) / 직선 거리 = Circuity (1보다 크면 직선 거리를 우회해서 간다는 뜻)

- Circuity(우회계수)가 1보다 작은 것은 직선거리가 더 큰 것이므로 우리가 하고자 하는 프로젝트의 insight와 안 맞다고 판단해 Circuity가 1보다 작고, 3보다 큰 데이터는 제외함.

- Folium 시각화 결과, 서초구, 중랑구, 양천구, 서대문구 총 네 개의 구에서 우회계수의 분포가 높게 나타남.

- 그 중, 서초구의 대중교통 취약지점을 분석해 이용 기록이 많고, 우회계수 평균이 높은 반포3동, 방배1동, 방배본동을 분석함.

- 출, 퇴근 및 이동시간 절약이 가능하고 목적지까지 우회 없이 이동이 가능한 공유 자전거 또는 전동킥보드 등의 단거리 교통수단을 서비스로 선택하였기에 total_distance를 2km로 제한함.

![캡처짱](https://user-images.githubusercontent.com/97076352/168985028-c0ef894d-eecb-4af3-b5cc-b0bce9de7c25.PNG)

## 4. 활용 및 아쉬운 점

- 탑승 경도, 위도 중심으로 Circuity에 따라 색상을 다르게 클러스터링함. 

![image](https://user-images.githubusercontent.com/97076352/168987179-c524f28a-9052-4bd4-8384-55b7b49c6ed8.png)

- 이를 바탕으로 대중교통 취약지점을 파악해 온디맨드 서비스의 최적 입지를 분석함.

- 시간 관계상 이용 승객 수와 Circuity는 유의미한 관계가 있을까?에 대한 가설 검정과 버스 이용 승객 & 지하철 이용 승객 & 둘 다 이용한 승객으로 나눠 데이터 분석 등 온디맨드 서비스를 위한 다양한 데이터 분석을 하지 못한 점이 아쉬움.
