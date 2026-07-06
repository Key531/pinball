# 순서 정하기 핀볼 🎱 (Marble Order Pinball)

숫자(인원수)나 이름을 입력하면, 번호·이름이 적힌 마블들이 **구불구불한 스위치백 트랙**을 질주하며 **순서(등수)** 를 정해주는 웹 게임입니다. 카메라가 선두를 따라가고, 미니맵·실시간 순위·중계 드립이 함께 나옵니다. 매번 결과가 달라지고, 완전 무작위·완전 공정하며, 꼴찌까지 유머러스한 코멘트가 붙어요.

`lazygyu/roulette`(마블 룰렛)의 느낌을 살려, 진짜 2D 물리엔진 **[Matter.js](https://brm.io/matter-js/)** 로 만들었습니다.

## 특징

- 두 가지 입력 모드: 🔢 숫자(인원수) / ✍️ 이름 직접 입력 (2~24명)
- 핀볼식 카오스 코스: **파친코 못밭 4개 + 핀볼 범퍼 + 회전 스피너 4개 + 막판 믹싱볼(교반기)**
- 순위가 끝까지 뒤집힘 — 레이스당 선두 교체 10~28회, 후반부 접전, 사진 판독급 결승
- **선두를 따라가는 카메라** + **미니맵** + **실시간 순위판**
- 유머: 실시간 중계 드립·**대역전 콜아웃**, 도착 순간 멘트, 시상식 밈, 범퍼 효과음, 골인 꽃가루
- 완전 순위 결과 — 1등부터 꼴찌까지 등수 + 재미있는 코멘트
- 클로드 감성 디자인(따뜻한 크림·코랄 톤)
- 의존성 하나(로컬 번들된 `matter.min.js`)뿐인 정적 사이트 — 빌드 불필요
- 물리 검증: 인원수 2~24명 각각 헤드리스 시뮬레이션으로 **100% 완주·잼 없음**·타이밍 9~13초·공정한 우승 분포 확인

## 로컬에서 실행

빌드가 필요 없습니다. 파일을 브라우저로 열기만 하면 됩니다.

```bash
# 방법 1) 그냥 열기
open index.html            # macOS

# 방법 2) 간단한 로컬 서버 (권장)
python3 -m http.server 5173
# → http://localhost:5173 접속
```

## 배포

### GitHub에 올리기

```bash
git init
git add .
git commit -m "순서 정하기 핀볼 마블 레이스"
git branch -M main
git remote add origin https://github.com/<사용자명>/<저장소명>.git
git push -u origin main
```

### Vercel 배포

프레임워크·빌드 설정이 필요 없는 순수 정적 사이트입니다.

1. [vercel.com](https://vercel.com) 로그인 → **Add New… → Project**
2. 위에서 올린 GitHub 저장소를 **Import**
3. Framework Preset은 **Other**(자동 감지됨), Build Command·Output 디렉터리는 비워둔 채로 **Deploy**
4. 발급된 `https://<프로젝트>.vercel.app` 주소로 접속

또는 CLI로:

```bash
npm i -g vercel
vercel          # 미리보기 배포
vercel --prod   # 프로덕션 배포
```

### GitHub Pages로도 가능

저장소 **Settings → Pages → Source: main / (root)** 로 지정하면 `https://<사용자명>.github.io/<저장소명>/` 에서 바로 열립니다.

## 파일 구조

```
index.html      게임 본체 (UI + 물리 + 렌더링)
matter.min.js   물리엔진 (Matter.js 0.20, 로컬 번들)
vercel.json     Vercel 정적 배포 설정
pinball.html    구버전 → index.html 로 리다이렉트
```

## 라이선스

Matter.js는 MIT 라이선스입니다.
