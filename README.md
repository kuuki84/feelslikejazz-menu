# 기분이재즈 QR 메뉴판

손님이 QR을 찍으면 열리는 모바일 메뉴판입니다.

- 주소: https://kuuki84.github.io/feelslikejazz-menu/
- 메뉴 고치기: `index.html` 안의 `const MENU = [...]` 부분만 고치면 됩니다.

## 주차 지도 (`parking/`)

가게 1km 안에서 고른 시각에 문 닫은 가게(초록)·영업 중(빨강)·주차장(P)을 지도에 보여 줍니다. 내 위치도 표시됩니다.

- 주소: https://kuuki84.github.io/feelslikejazz-menu/parking/
- 자료 고치기: `parking/stores.json`만 고치면 됩니다. 가게는 `stores`에 `{"name","category","lat","lng","hours":{"mon":"10:00-21:00",...,"sun":"휴무"},"parkingFront","note"}` 모양으로 넣습니다. 밤을 넘기면 `"18:00-02:00"`, 모르면 `null`.
- 지도: `stores.json`의 `naverClientId`에 네이버 클라우드 Maps Client ID를 넣으면 네이버 지도, 비우면 OpenStreetMap. 열쇠가 틀리면 자동으로 OpenStreetMap으로 돌아감. 길찾기는 카카오맵 링크.
