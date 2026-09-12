# nunpiro

눈 건강 정보 사이트 (정적 · GitHub Pages)

**상태: 임시 배포 (커스텀 도메인 연결 전)**

- 임시 주소: https://mgyu0904.github.io/nunpiro/
- 목표 도메인: `nunpiro.org` (DNS 미연결)

## 지금 검색 색인이 막혀 있다 — 의도된 것이다

임시 주소가 색인되면 `nunpiro.org` 을 붙인 뒤 같은 글이 두 주소로 잡혀 중복이 된다.
그래서 이 단계에서는 두 겹으로 막아 두었다.

- `robots.txt` = `Disallow: /`
- 전 페이지 `<meta name="robots" content="noindex,nofollow">`

## 도메인 연결 시 해제 절차

1. 가비아에서 `nunpiro.org` DNS 설정 (A 4개 + www CNAME)
2. DNS 전파 확인 후 Settings > Pages > Custom domain 에 `nunpiro.org` 입력
3. 재빌드 — `--staging` 플래그를 **빼고** 돌리면 색인 차단이 자동으로 풀린다

```bash
python3 build.py --site nunpiro          # 색인 허용 + CNAME 생성 + 실도메인 절대경로
python3 tools/deploy_pages.py --apply --prod --site nunpiro
```

`--staging` 없이 빌드하면 robots 전면 허용 · noindex 제거 · `CNAME` 파일 생성이
한 묶음으로 같이 바뀐다. 하나만 빼먹는 사고가 안 나게 묶어 두었다.

## 이 사이트가 지키는 것

- **sitemap 의 lastmod 는 원고 파일의 실제 수정시각.** 빌드할 때마다 오늘로 다시
  찍지 않는다. 그 동작이 기존 사이트의 색인을 끊은 직접 원인이었다.
- 저자는 조직 명의만. 가짜 사람 저자·가짜 댓글을 만들지 않는다.
- 본문은 JS 없이 HTML 안에 그대로 들어 있다.
