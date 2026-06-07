# Gemini 인계 문서 — v1.4-1c 이후

문서 기준일: 2026-06-07  
작성자: Claude Code (v1.4-1c 작업 완료 후 생성)  
다음 작업 권장 도구: **Gemini 고급 추론**

---

## 1. 현재 프로젝트 상태

| 항목 | 값 |
|---|---|
| 앱 기능 최신 버전 | v1.3-13 |
| 진우 개발자 모드 | v1.4.1c (로컬 PC 전용) |
| 최신 문서 패치 | v1.4-1b (AI 운영 책임 원칙) |
| 최신 UX 패치 | v1.4-1c (저장함 안전 보완 + AI 회의실 강화) |
| GitHub Pages | https://hyeong-ship-it.github.io/kids-mission-game/ |
| 메인 저장 키 | `kidsPointGame_v1` (절대 변경 금지) |
| 진우 개발자 모드 저장 키 | `jinwooDirectorMode_v1` (메인과 완전 분리) |

---

## 2. 진우 개발자 모드의 목적

진우(초6)가 `주니어 게임 디렉터`로서:

- 동생들의 반응을 관찰하고 기록한다.
- 새 기능과 퀴즈 아이디어를 정리한다.
- AI와 회의하되 **자기 생각을 먼저** 쓰고 AI에게 결정을 맡기지 않는다.
- 부모 검토를 거쳐야만 실제 게임에 반영된다.

메인 게임 데이터(`kidsPointGame_v1`)에는 절대 접근하지 않는다. PC 전용 로컬 도구이며 GitHub에 올리지 않는다.

---

## 3. v1.4-1 ~ v1.4-1c 패치 흐름 요약

| 버전 | 내용 |
|---|---|
| v1.4-1 | 진우 개발자 모드 MVP 구현 (관찰 노트·아이디어·문제팩·AI 프롬프트·배지·백업) |
| v1.4-1a | 어린이 UX 리디자인 (오늘의 개발자 작전, 쉬운 메뉴명, 체크 피드백, 진행률) |
| v1.4-1b | AI 운영 책임 원칙 문서 확정 (PROJECT_RULES.md, AI_HANDOFF.md, AGENTS.md 등 7개 문서) |
| v1.4-1c | 실사용 전 미니 UX 보완 — 저장함 불러오기 confirm() 추가, 경고 문구 삽입, 초기화 안내 강화, AI 회의실 원칙 kid-note 추가 |

---

## 4. 진우 개발자 모드 파일 위치

```
_do_not_upload/jinwoo_director_mode/
├── jinwoo_director_mode.html          ← 메인 파일 (v1.4.1c)
├── start_jinwoo_director.bat          ← 로컬 실행
├── create_desktop_shortcut.bat        ← 바탕화면 바로가기 생성
├── README_JINWOO_DIRECTOR_MODE.md     ← 사용 안내
├── jinwoo_director_mode.backup-before-v1-4-1a-kid-ux.html
└── jinwoo_director_mode.backup-before-v1-4-1c-mini-ux.html
```

GitHub 업로드 대상 아님. `_do_not_upload/` 폴더 전체 업로드 금지.

---

## 5. 수정하면 안 되는 파일

| 파일 | 이유 |
|---|---|
| `index.html` | 메인 게임 기능. 기능 구현 패치 외 수정 금지. |
| `sw.js` | PWA 서비스 워커. 캐시 갱신 리스크. |
| `manifest.webmanifest` | PWA 앱 정의. |
| `assets/` | 아이콘. |
| `make_release_package.py` | 배포 자동화 스크립트. |

---

## 6. 실제 실행해서 확인해야 할 항목

진우 개발자 모드(`jinwoo_director_mode.html`)를 PC 브라우저에서 열고 아래를 확인한다.

**기본 흐름**
- [ ] 오늘의 개발자 작전 화면이 첫 화면으로 열린다
- [ ] 오늘의 작전 카드 4개가 보인다
- [ ] 체크하면 진행률 바가 바뀐다
- [ ] 4개 모두 체크하면 완료 메시지가 뜬다

**저장함 안전성 (v1.4-1c 핵심)**
- [ ] 저장 파일 가져오기 버튼이 주황색(warn)으로 표시된다
- [ ] 파일 선택 후 버튼을 누르면 confirm 창이 뜬다
- [ ] confirm 창에 "지금 기록이 바뀔 수 있어" 문구가 있다
- [ ] 취소를 누르면 기록이 바뀌지 않는다
- [ ] 초기화 카드에 "코인, 레벨, 아이템은 절대 지워지지 않아요" 문구가 있다

**AI 회의실**
- [ ] section-help에 "먼저 진우 생각을 쓰고, AI는 회의 친구처럼 쓰자" 문구가 있다
- [ ] kid-note에 "① 내 생각 쓰기 → … → ④ 진우가 최종 결정" 흐름이 보인다

**저장 키 분리**
- [ ] 관찰 노트를 저장하면 `jinwooDirectorMode_v1` 키에 저장된다
- [ ] `kidsPointGame_v1` 키는 변경되지 않는다

---

## 7. Gemini에게 맡길 다음 작업 제안

### 추천 작업: `v1.4-1d 진우 개발자 모드 실사용 시나리오 검토 + v1.4-2 두뇌 던전 MVP 사전 설계 점검`

**작업 A — 진우 개발자 모드 실사용 시나리오 검토**

진우가 처음 앱을 열었을 때의 10분 사용 시나리오를 문서로 작성한다.

- 어떤 순서로 탭을 탐색하는가?
- 오늘의 작전 4개 중 처음 막히는 지점은 어디인가?
- 부모가 옆에서 어떤 질문을 던지면 가장 효과적인가?
- 아이가 AI에게 결정을 미루려는 시도를 부모가 어떻게 막는가?

결과물: `JINWOO_FIRST_USE_SCENARIO.md` (선택)

**작업 B — v1.4-2 두뇌 던전 MVP 사전 설계 점검**

`LEARNING_DUNGEON_SPEC.md`를 기준으로 아래를 검토한다.

- 1라운드 3문제 구조가 현재 코인 경제와 충돌하지 않는가?
- "지식 조각" 재화와 기존 XP·코인의 관계 설계
- "다시 도전함" 표현이 아이에게 부정적으로 느껴지지 않는가?
- `index.html`에 두뇌 던전을 추가할 때 기존 탭 구조와의 충돌 여부

결과물: `LEARNING_DUNGEON_DESIGN_REVIEW.md` (선택) 또는 `PATCH_QUEUE.md` 보강

---

## 8. Gemini가 검토해야 할 질문

1. 초6 아이(진우)가 진우 개발자 모드를 처음 열었을 때 10분간 혼자 사용할 수 있는가? 어디서 막히는가?

2. 첫 사용 시나리오가 너무 무겁지 않은가? "동생이 좋아한 장면 1개 적기"만 해도 성공이라는 흐름이 충분히 강조됐는가?

3. 진우가 AI에게 결정을 미루지 않고 자기 생각을 먼저 쓰게 되는가? AI 회의실 흐름에 개선이 필요한가?

4. 부모가 옆에서 어떤 질문을 던져야 하는가? `JINWOO_ACTIVITY_GUIDE.md`에 추가할 내용이 있는가?

5. 두뇌 던전으로 넘어가기 전에 진우 개발자 모드에서 더 보완해야 할 것은 무엇인가?

6. v1.4-2 두뇌 던전 MVP를 바로 구현해도 되는가, 아니면 진우 실사용 테스트를 먼저 하는 것이 맞는가?

7. 코인 인플레이션을 막으면서 학습 반복성을 살리는 구조(지식 조각 재화 분리)가 현재 설계에서 충분한가?

8. v1.3-13 패드 실사용 검수가 아직 미완료 상태다. 두뇌 던전 구현 전에 패드 검수를 먼저 해야 하는가?

---

## 9. Gemini 작업 시작 전 반드시 읽을 파일

1. `AGENTS.md`
2. `AI_HANDOFF.md`
3. `PROJECT_RULES.md`
4. `PROJECT_STATE.md`
5. `PATCH_QUEUE.md`
6. `LEARNING_DUNGEON_SPEC.md`
7. `JINWOO_DIRECTOR_MODE_SPEC.md`
8. `JINWOO_ACTIVITY_GUIDE.md`

---

## 10. 절대 하지 말아야 할 일

- `kidsPointGame_v1` 키를 바꾸거나 읽지 않는다.
- 진우 개발자 모드 파일을 `_github_upload/`에 넣지 않는다.
- 부모 승인 없이 아이디어나 문제팩을 메인 게임에 반영하지 않는다.
- AI API 연결을 구현하지 않는다 (별도 승인 전까지).
- 외부 라이브러리, CDN, 웹폰트를 추가하지 않는다.
- `index.html`, `sw.js`, `manifest.webmanifest`를 임의로 수정하지 않는다.
