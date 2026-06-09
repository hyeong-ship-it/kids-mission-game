# 프로젝트 상태 문서

문서 기준일: 2026-06-10  
앱 기능 최신 버전: v1.4-2c
배포 관리 패치: v1.3-14  
설계 문서 패치: v1.4-0  
로컬 도구 패치: v1.4-1
로컬 UX 개선 패치: v1.4-1a
운영 원칙 문서 반영 패치: v1.4-1b
미니 UX 보완 패치: v1.4-1c
두뇌 던전 MVP 패치: v1.4-2
두뇌 던전 복구·PWA 캐시 갱신 패치: v1.4-2a
등교 준비 잠금 모드 패치: v1.4-2c

## 프로젝트 목적

`3형제 미션 배틀`은 아이들이 집안 미션, 학습 퀘스트, 위생 미션, 가족 협동 미션을 완료하면서 XP, 코인, 아이템, 성장 기록을 얻는 가족용 미션 RPG다. 부모는 승인, 보상, 마감, 백업, 칭찬 우체통을 관리하고, 아이 화면은 성장, 해금, 칭찬, 협동 중심으로 운영한다.

## 현재 운영 상태

- 최신 기능 적용 기준: v1.4-2c
- 실행 방식: GitHub Pages 배포 + 공용 Android 패드 1대 홈앱/PWA 설치
- 저장 방식: 브라우저 localStorage
- 메인 게임 localStorage 키: `kidsPointGame_v1`
- 부모 비밀번호: `0903`
- 현재 운영 기준: 공용 Android 패드 1대에서 가족이 함께 사용
- GitHub Pages 주소: `https://hyeong-ship-it.github.io/kids-mission-game/`

## 아이 정보

| 내부 kid ID | 표시 이름 | 두뇌 던전 기본 학년 |
| --- | --- | -: |
| `jinwoo` | 상어 | 초6 |
| `jinyoung` | 축복이 | 초5 |
| `jinhwan` | 복복이 | 초2 |

## 현재 주요 기능

- 아이별 PIN 입장
- 부모 비밀번호 재인증
- 미션 클리어와 되돌리기
- XP/코인 분리
- 레벨과 해금 아이템
- 스킨샵, 보관함, 장착 상태
- 캐릭터 움직임과 개성 강화
- 팀 사진관
- 업데이트 예고
- 보물상자와 보상 연출
- 부모 승인형 특별 미션
- 시험 보너스 요청, 취소, 승인
- 개인방 권한 잠금
- 학습 퀘스트
- 위생 미션
- 가족 보상 경제
- 형제 협동 보상
- 팀 메달
- 주간/월간 마감
- 시즌 미션
- 성장 기록
- 알림함과 묶음 알림
- 백업 알림과 데이터 불러오기
- Android PWA 설치 지원
- 부모 칭찬 우체통
- 평일 아침 등교 준비 잠금 모드

## v1.4-0 설계 문서 패치

v1.4-0은 기능 구현이 아니라 다음 큰 버전 v1.4를 안전하게 준비하기 위한 설계 문서 패치다. 이번 패치에서는 `index.html`, `sw.js`, `manifest.webmanifest`, `assets/` 아이콘 파일을 수정하지 않는다.

추가된 설계 방향:

- PC 전용 `진우 개발자 모드`
- 진우 역할명: `주니어 게임 디렉터`
- 진우 개발자 모드 추천 저장 키: `jinwooDirectorMode_v1`
- 메인 게임 저장 키 `kidsPointGame_v1`과 완전 분리
- 아이별 수준에 맞춘 `두뇌 던전`
- 문제팩 형식과 부모 승인 흐름
- 아이가 AI를 회의 친구로 쓰기 위한 협업 원칙

## v1.4-0 신규 문서

- `JINWOO_DIRECTOR_MODE_SPEC.md`
- `LEARNING_DUNGEON_SPEC.md`
- `AI_COLLABORATION_RULES_FOR_KIDS.md`
- `QUESTION_PACK_FORMAT.md`
- `JINWOO_ACTIVITY_GUIDE.md`

## v1.4-1 PC 전용 진우 개발자 모드 MVP

v1.4-1은 패드용 메인 게임 기능 추가가 아니라 PC 로컬 전용 도구 구현 패치다. 진우 개발자 모드는 `_do_not_upload/jinwoo_director_mode/` 안에 있으며 GitHub 업로드 대상이 아니다.

생성된 로컬 전용 파일:

- `_do_not_upload/jinwoo_director_mode/jinwoo_director_mode.html`
- `_do_not_upload/jinwoo_director_mode/start_jinwoo_director.bat`
- `_do_not_upload/jinwoo_director_mode/create_desktop_shortcut.bat`
- `_do_not_upload/jinwoo_director_mode/README_JINWOO_DIRECTOR_MODE.md`

저장 기준:

- 진우 개발자 모드 저장 키: `jinwooDirectorMode_v1`
- 메인 게임 저장 키 `kidsPointGame_v1`와 완전 분리
- AI API 직접 연결 없음
- 실제 게임 반영 없음

## AI 운영 철학 (v1.4-1b 확정)

v1.4-1b 패치에서 프로젝트 운영 책임 원칙이 확정됐다.

핵심 요약:

- 사용자는 목적과 방향을 제시하는 최종 책임자다. 세부 오류를 지적하는 검수자가 아니다.
- AI는 목적 달성을 책임지는 외부 컨설턴트이자 사업부 대표 역할을 수행한다.
- AI는 단순 구현 이전에 UX, 운영성, 교육 효과, 데이터 안정성, 장기 확장성의 허점을 선제적으로 제안해야 한다.
- 프로젝트 상태와 이력은 장기 메모리가 아니라 프로젝트 문서에 관리한다.
- 작업 도구는 Codex 우선, 토큰/사용량 부족 시 Claude Code 또는 Gemini로 이어받는다.

세부 원칙은 `PROJECT_RULES.md` AI 운영 책임 원칙 섹션과 `AI_HANDOFF.md`에 기록됐다.

## v1.4-1a 진우 개발자 모드 어린이 UX 개선

v1.4-1a는 기능을 크게 늘리지 않고 초6 아이가 혼자 쓰기 쉽게 만든 UX 개선 패치다. 첫 화면을 `홈 대시보드` 느낌에서 `오늘의 개발자 작전` 흐름으로 바꾸고, 메뉴와 버튼 문구를 아이 눈높이로 순화했다.

핵심 개선:

- 오늘의 작전 0/4 진행률 표시
- 체크 시 축하 피드백과 다음 행동 안내
- 4개 완료 시 작전 완료 메시지
- 탭별 쉬운 설명 추가
- `AI 회의실`을 `AI랑 작전회의` 톤으로 개선
- `저장함` 표현으로 백업/불러오기 부담 완화

유지 기준:

- 저장 키 `jinwooDirectorMode_v1` 유지
- 메인 게임 키와 데이터 접근 없음
- `_do_not_upload/jinwoo_director_mode/` 로컬 전용 유지
- GitHub 업로드 대상 아님

## v1.4-2c 등교 준비 잠금 모드

v1.4-2c는 평일 아침 등교 준비 시간에 앱 조작보다 등교 준비가 먼저라는 가족 규칙을 앱 입장 단계에서 안내하는 패치다.

적용 기준:

- 스플래시 이후 아이 선택/PIN 화면 전에 잠금 여부를 판단한다.
- 기본값은 사용함, 월~금 06:30~08:30이다.
- 잠금 화면에는 아이용 큰 버튼이나 체크 버튼을 두지 않는다.
- 하단의 작은 `부모 메뉴`만 제공하고, 매번 비밀번호 `0903`을 요구한다.
- 부모는 오늘만 잠금 해제, 사용/해제, 시작/종료 시간 변경을 할 수 있다.
- 저장 구조는 `state.gameMeta.schoolMorningLock`이며 기존 localStorage 키 `kidsPointGame_v1`은 유지한다.
- 기존 XP, 코인, PIN, 보관함, 승인 대기, 가족 보상, 두뇌 던전 데이터는 초기화하지 않는다.
- `sw.js` 캐시는 `kids-mission-battle-v1.4.2c`로 갱신했다.
- 패드 업로드 후 실제 월~금 아침 시간대와 임시 시간 설정으로 실사용 검수가 필요하다.

## 업로드해야 할 파일

GitHub Pages 배포 시 아래 파일을 업로드한다.

- `index.html`
- `manifest.webmanifest`
- `sw.js`
- `assets/icon-192.png`
- `assets/icon-512.png`
- `assets/icon-maskable-512.png`
- `PROJECT_STATE.md`
- `PROJECT_RULES.md`
- `ROADMAP.md`
- `CHANGELOG.md`
- `PATCH_QUEUE.md`
- `TEST_CHECKLIST.md`
- `AI_HANDOFF.md`
- `JINWOO_DIRECTOR_MODE_SPEC.md`
- `LEARNING_DUNGEON_SPEC.md`
- `AI_COLLABORATION_RULES_FOR_KIDS.md`
- `QUESTION_PACK_FORMAT.md`
- `JINWOO_ACTIVITY_GUIDE.md`

## 업로드하지 말아야 할 파일

- `index.backup-*.html` 파일
- `_do_not_upload/` 폴더 전체
- `_do_not_upload/jinwoo_director_mode/` 폴더 전체
- `_github_upload/` 폴더 자체
- `.claude/`
- `make_release_package.py`, `make_release_package.bat`
- `RELEASE_GUIDE.md`
- 개인 설정 파일
- 로컬 실행 로그
- 임시 파일, 백업 파일

## 배포 패키지 생성 방법

GitHub Pages 업로드 전 아래 스크립트를 실행한다.

```bash
python make_release_package.py
```

실행 후 `_github_upload/UPLOAD_CHECKLIST.md`를 확인하고 `_github_upload/` 안의 내용물을 GitHub에 올린다. `_github_upload/` 폴더 자체를 올리지 않는다.

## 아직 실제 패드에서 검수해야 할 항목

- [x] GitHub Pages 최신 파일 반영 여부
- [x] 홈 화면 PWA 실행 여부
- [x] 기존 localStorage 데이터 유지 여부
- [x] 아이별 PIN 입장
- [x] 부모 메뉴 재인증
- [x] 미션 클리어와 되돌리기
- [x] 보물상자 열기와 안내 문구
- [x] 시험 보너스 요청, 취소, 승인
- [x] 가족 보상 요청과 승인
- [x] 형제 협동 보상
- [x] 주간/월간 마감
- [x] 시즌 미션
- [x] 스킨샵, 보관함, 장착 상태
- [x] 알림함과 묶음 알림
- [x] 백업과 불러오기
- [x] 모바일/패드 화면 깨짐 여부
- [x] 앱명 변경 확인 (v1.3-13)
- [x] 오늘의 작전 카드 확인 (v1.3-13)
- [x] 칭찬 우체통 확인 (v1.3-13)

## v1.4 구현 전 주의사항

- v1.4-0 문서는 설계 기준이며 앱 기능은 아직 구현되지 않았다.
- `진우 개발자 모드`는 PC 전용 별도 도구로 구현되었으며 GitHub 업로드 대상이 아니다.
- `두뇌 던전`은 메인 코인 경제와 학습 재화를 분리한다.
- AI API 연결은 별도 승인 전까지 구현하지 않는다.
- 승인되지 않은 진우 아이디어나 문제팩은 메인 게임에 자동 반영하지 않는다.
