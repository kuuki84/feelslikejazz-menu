# 기분이재즈 QR 메뉴판

손님이 QR을 찍으면 열리는 모바일 메뉴판입니다.

- 주소: https://kuuki84.github.io/feelslikejazz-menu/
- 메뉴 고치기: `index.html` 안의 `const MENU = [...]` 부분만 고치면 됩니다.

## 주차 지도 (`parking/`)

가게 1km 안에서 고른 시각에 문 닫은 가게(초록)·영업 중(빨강)·주차장(P)을 지도에 보여 줍니다. 내 위치도 표시됩니다.

- 주소: https://kuuki84.github.io/feelslikejazz-menu/parking/
- 자료 고치기: `parking/stores.json`만 고치면 됩니다. 가게는 `stores`에 `{"name","category","lat","lng","hours":{"mon":"10:00-21:00",...,"sun":"휴무"},"parkingFront","note"}` 모양으로 넣습니다. 밤을 넘기면 `"18:00-02:00"`, 모르면 `null`.
- 지도: `stores.json`의 `naverClientId`에 네이버 클라우드 Maps Client ID를 넣으면 네이버 지도, 비우면 OpenStreetMap. 열쇠가 틀리면 자동으로 OpenStreetMap으로 돌아감. 길찾기는 카카오맵 링크.

## 페이지 구성 (2026-11 개편)
- 그냥 들어오면: 오늘 밤(TONIGHT) → 공연 일정(7일) → 가게 소개·사진 → 메뉴 → 이용 안내 → 신청곡·와이파이 → 오시는 길·주차 → 자주 묻는 질문
- 테이블 QR(`?at=table`)로 들어오면: 메뉴 → 이용 안내 → 신청곡·와이파이가 먼저, 와이파이 비밀번호도 이때만 보여요.
  - 테이블 QR 주소: `https://kuuki84.github.io/feelslikejazz-menu/?at=table`

## 고치는 곳 (모두 `index.html` 위쪽 ★ 표시)
- `HOURS` 영업·연주 시간 / `CLOSED_WEEKDAYS`, `CLOSED_DATES` 휴무
- `WIFI` 와이파이 이름·비밀번호 (비밀번호는 테이블 QR 화면에만 보이지만, 페이지 소스에는 들어 있어요)
- `INFO` 입장료·결제·대관 한 줄 안내 (비우면 안 보임)
- `FAQ` 자주 묻는 질문
- `LIVE_SHEET_CSV` 또는 `LIVE` 공연 일정
- `MENU` 메뉴

## 공연 일정 고치기
### 구글 시트로 (추천, 휴대폰에서 바로)
1. 구글 시트 첫 줄에 `date | time | title | who | note` 적기 (date 예: `2026-11-28`)
2. 파일 → 공유 → 웹에 게시 → 시트 선택, 형식 **CSV** → 게시 → 나온 주소 복사
3. `index.html`의 `const LIVE_SHEET_CSV = "";` 따옴표 안에 붙여 넣기 (처음 한 번만)
4. 이후로는 시트만 고치면 몇 분 안에 페이지에 반영돼요.

### 코드로
`index.html`에서 `const LIVE = [` 아래에 한 줄씩 넣으면 됩니다.
```
{ date:"2026-11-28", time:"20:00", title:"블루스 나이트", who:"기타 듀오", note:"신청곡 받아요" },
```
지난 날짜는 자동으로 숨고, 오늘부터 7일 안 일정만 보여요. 비워 두면 「매일 1부 20:00 · 2부 21:30」 기본 안내가 나와요.

## 사진
`photos/` 폴더(가로 900px, 손님 얼굴 없는 사진만). `og.jpg`는 링크 공유할 때 미리보기 사진이에요.

## 검색 등록
`sitemap.xml`을 구글 서치 콘솔·네이버 서치어드바이저에 등록하세요(사장님 계정).
