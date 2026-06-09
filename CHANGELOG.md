# 변경 이력

문서 기준일: 2026-06-10

## v1.4-2c (등교 준비 잠금 모드)

- `index.html`에 평일 아침 등교 준비 잠금 모드 추가
- 기본 설정: 사용함, 월~금, 06:30~08:30
- 앱 시작 흐름을 `스플래시 → 잠금 판단 → 등교 준비 안내 또는 아이 선택/PIN`으로 변경
- 잠금 화면은 안내 중심이며 아이용 큰 버튼, 체크 버튼, 계속하기 버튼 없음
- 잠금 화면 하단에 작은 `부모 메뉴` 제공, 접근 시 매번 비밀번호 `0903` 요구
- 부모 인증 후 오늘만 잠금 해제, 사용/해제, 시작/종료 시간 변경 가능
- 기존 부모 메뉴 설정 탭에도 `등교 준비 잠금` 섹션 추가
- 저장 구조 `state.gameMeta.schoolMorningLock` 추가, localStorage 키 `kidsPointGame_v1` 유지
- 기존 XP, 코인, PIN, 보관함, 승인 대기, 가족 보상, 두뇌 던전 데이터 초기화 없음
- `sw.js` 캐시 버전을 `kids-mission-battle-v1.4.2c`로 갱신
- 백업: `_do_not_upload/backups/index.backup-before-v1-4-2c-school-morning-lock.html`, `_do_not_upload/backups/sw.backup-before-v1-4-2c-school-morning-lock.js`
- Android 패드 업로드 후 일반 시간과 잠금 시간 실사용 검수 필요

## v1.4-2a (두뇌 던전 복구 + PWA 캐시 갱신)

- `index.html` `renderMissions()`에 `dungeonState.active` 분기 추가 — 스플래시 멈춤·던전 시작 후 클릭 미전환 문제 복구
- `missionsEl` null guard 추가로 초기 렌더링 안정성 보강
- `sw.js` 캐시 버전을 `kids-mission-battle-v1.4.2a`로 갱신 (구버전 `index.html` PWA 캐시 무효화)
- `kidsPointGame_v1` localStorage 키·부모 비밀번호·kid ID 변경 없음
- GitHub 업로드 전 로컬 검수 필요. Android 패드는 업로드 후 새로고침 또는 최신 버전 다시 불러오기 필요
- 백업: `_do_not_upload/backups/index.backup-before-v1-4-2a-splash-recovery.html`

## v1.4-2 (두뇌 던전 MVP 구현 및 문서 불일치 수정)

- `index.html`에 두뇌 던전 MVP 로직 및 화면 구현
  - 내장 문제팩(아이별 9문제) `LEARNING_DUNGEON_QUESTIONS` 추가
  - 1일 1회차 10코인, 2회차 5코인, 3회차 이상 0코인 지급 로직 적용
  - 지식 조각 및 두뇌 XP 부여 로직 구현
  - 오답(다시 도전 문제) 재도전 로직 적용
  - 금지어(오답, 실패) 대신 긍정적 메시지 적용
- `kidsPointGame_v1` localStorage 데이터 안전 마이그레이션 (`state.brainDungeon` 추가)
- `sw.js` 캐시 버전을 `kids-mission-battle-v1.4.2`로 갱신
- `v1.3-13 패드 실사용 검수` 관련 상태 문서 불일치(완료 처리) 수정
- `make_release_package.py`에 `GEMINI_HANDOFF_V1_4_1C.md` 업로드 포함

## v1.4-1c (진우 개발자 모드 실사용 전 미니 UX 점검 — 메인 앱 기능 변경 없음)

- `jinwoo_director_mode.html` VERSION 1.4.1c로 갱신
- 저장함 불러오기(importBackup) — 파일 선택 후 confirm() 없이 즉시 덮어쓰는 치명적 버그 수정: 확인 창 추가
- 저장 파일 다시 가져오기 카드에 경고 kid-note 추가 ("지금 기록이 바뀔 수 있어. 먼저 저장 파일 만들기를 해두면 안전해.")
- 불러오기 버튼 색상을 secondary → warn(주황)으로 변경하여 위험도 시각화
- 초기화 카드에 kid-note 추가 ("3형제 미션 배틀의 코인, 레벨, 아이템은 절대 지워지지 않아요")
- AI랑 작전회의 탭에 kid-note 추가 ("① 내 생각 쓰기 → ② AI에게 묻기 → ③ 쓸 것 고르기 → ④ 진우가 최종 결정" 흐름 강조)
- `GEMINI_HANDOFF_V1_4_1C.md` 생성: Gemini 인계 문서 (현재 상태, 다음 작업 제안, 검토 질문 8개)
- 백업: `jinwoo_director_mode.backup-before-v1-4-1c-mini-ux.html`
- 메인 게임 파일(`index.html`, `sw.js`, `manifest.webmanifest`, `assets/`) 수정 없음

## v1.4-1b (운영 책임 원칙 문서 반영 + v1.4-1a 결과 검수 — 앱 기능 변경 없음)

- `PROJECT_RULES.md`에 AI 운영 책임 원칙 섹션 추가: 사용자 역할, AI 역할, 다단계 합의 원칙, 상태 관리 원칙, 도구 전환 원칙, 완료 보고 검수 기준
- `AI_HANDOFF.md`에 AI 운영 책임 원칙·작업 지시서 포함 원칙·Codex/Claude/Gemini 전환 기준·완료 보고 검수 기준 추가, 기존 도구 운영 원칙 섹션과 통합
- `PROJECT_STATE.md`에 AI 운영 철학 확정 기록 추가
- `PATCH_QUEUE.md`에 v1.4-1b 완료 기록 추가, v1.4-1c 진우 개발자 모드 실사용 검수 후보 추가
- `TEST_CHECKLIST.md`에 AI 작업 결과 목적 기준 검수 섹션 추가
- `AGENTS.md` 신규 생성: 작업 시작 전 읽을 문서, 절대 금지 사항, 저장 키, 전환 기준 등 요약
- `make_release_package.py`에 `AGENTS.md` 업로드 대상 추가
- v1.4-1a 결과 검수: 메뉴명·첫 화면·체크 피드백·AI 회의실 원칙·저장 키 분리 모두 확인
- 메인 게임 파일(`index.html`, `sw.js`, `manifest.webmanifest`, `assets/`) 수정 없음
- 진우 개발자 모드 HTML 수정 없음
- `v1.3-13 패드 실사용 검수` 완료 처리 문서 반영 (사용자 확인 완료)

## v1.4-1a (진우 개발자 모드 어린이 UX 리디자인 — 메인 앱 기능 변경 없음)

- `jinwoo_director_mode.html` 첫 화면을 `오늘의 개발자 작전` 중심으로 변경
- 메뉴명을 초6 아이 눈높이로 변경: 오늘의 작전, 동생 반응 보기, 새 기능 만들기, 퀴즈 만들기, AI랑 작전회의, 게임에 넣을 후보, 내 개발자 배지, 저장함
- 오늘의 작전 0/4 진행률, 다음 추천 행동, 4개 완료 메시지 추가
- 체크박스 클릭 시 작전 완료 피드백과 CSS 애니메이션 추가
- 각 탭 상단에 “여기서 하는 일” 설명 추가
- AI 회의실 문구를 “내 생각 먼저”와 “AI는 회의 친구” 중심으로 개선
- 어려운 용어를 아이 눈높이 문구로 순화
- 기존 저장 키 `jinwooDirectorMode_v1` 유지
- 메인 게임 파일과 메인 게임 저장 키는 건드리지 않음

## v1.4-1 (PC 전용 진우 개발자 모드 MVP 구현 패치 — 메인 앱 기능 변경 없음)

- `_do_not_upload/jinwoo_director_mode/` 폴더 추가
- `jinwoo_director_mode.html` 추가: PC 로컬 전용 진우 개발자 모드 단일 HTML 도구
- `start_jinwoo_director.bat` 추가: 로컬 HTML 실행 배치 파일
- `create_desktop_shortcut.bat` 추가: Windows 바탕화면 바로가기 생성 파일
- `README_JINWOO_DIRECTOR_MODE.md` 추가: 실행 방법, 저장 키, 백업/불러오기 안내
- 저장 키 `jinwooDirectorMode_v1` 사용
- 메인 게임 저장 키와 메인 앱 파일은 건드리지 않음
- AI API 직접 연결 없이 ChatGPT에 붙여넣을 수 있는 프롬프트 생성 방식으로 구현
- `PROJECT_STATE.md`, `ROADMAP.md`, `PATCH_QUEUE.md`, `AI_HANDOFF.md`, `TEST_CHECKLIST.md`, `RELEASE_GUIDE.md` 갱신

## v1.4-0 (설계 문서 패치 — 앱 기능 변경 없음)

- `JINWOO_DIRECTOR_MODE_SPEC.md` 추가: PC 전용 진우 개발자 모드 제품 설계
- `LEARNING_DUNGEON_SPEC.md` 추가: 아이별 수준에 맞춘 두뇌 던전 설계
- `AI_COLLABORATION_RULES_FOR_KIDS.md` 추가: 아이가 AI를 회의 친구로 쓰기 위한 원칙
- `QUESTION_PACK_FORMAT.md` 추가: 두뇌 던전 문제팩 JSON 형식과 승인 흐름
- `JINWOO_ACTIVITY_GUIDE.md` 추가: 형님/부모/진우가 함께 진행할 주간 활동 가이드
- `PROJECT_STATE.md`, `ROADMAP.md`, `PATCH_QUEUE.md`, `AI_HANDOFF.md`, `TEST_CHECKLIST.md` 갱신
- `make_release_package.py` 업로드 대상 문서 목록에 신규 설계 문서 5개 추가
- `index.html`, `sw.js`, `manifest.webmanifest`, `assets/` 기능 파일은 수정하지 않음

## v1.3-14 (배포 관리 패치 — 앱 기능 변경 없음)

- 폴더 구조 정비: `_github_upload/`, `_do_not_upload/backups/logs/temp/notes/` 생성
- 루트 백업 파일 20개 → `_do_not_upload/backups/`로 이동
- `make_release_package.py`: GitHub 업로드 패키지 자동 생성 스크립트 추가
- `make_release_package.bat`: 배치 실행 파일 추가
- `RELEASE_GUIDE.md`: 배포 관리 안내 문서 추가
- `_github_upload/UPLOAD_CHECKLIST.md`: 업로드 체크리스트 자동 생성 확인
- 문서 6개 v1.3-14 기준으로 갱신

## v1.3-13

- 앱 이름 "우리집 미션 배틀" → "3형제 미션 배틀" 전체 리브랜딩 (title, meta, 스플래시, 헤더, 입장 게이트)
- manifest.webmanifest name/description 갱신
- 아이 캐릭터 탭 상단에 "오늘의 작전" 카드 추가 (보물상자 진행, 다음 해금 목표, 팀 협동 목표, 내 요청 현황)
- 부모 아이 관리 탭에 "칭찬 우체통" 추가 (아이 선택, 빠른 칭찬 문구, 메시지 입력, 알림함 전송)
- sw.js 캐시 버전 v1.3.13으로 갱신
- CSS: 오늘의 작전 카드, 칭찬 우체통 스타일 추가

## v1.3-12

- 부모 운영센터 탭 구조 도입 (요약/승인 대기/보상 관리/주간월간/아이 관리/데이터백업/앱 설정)
- 오늘의 운영 요약 대시보드 추가
- 승인 대기 타입별 그룹화 (특별 미션/시험 보너스/개인 가족 보상/협동 보상)
- 보상 경제 현황 카드 추가
- 주간/월간 마감 확인창 강화
- 개인 가족 보상·협동 보상 승인 시 확인창 추가
- 전체 초기화 2단계 확인 ("초기화" 입력 + 확인 대화상자)
- 데이터/백업 섹션 정리 및 안내 강화
- 아이별 알림 일괄 읽음 처리 기능 추가
- 앱 설정 섹션 추가 (버전 v1.3.12 표시, 실행 모드, 효과음 상태)
- sw.js 캐시 버전 v1.3.12로 갱신
- CSS: 부모 탭 내비게이션, 대시보드 카드, 경제 현황 카드, 위험 구역 스타일 추가

## v1.3-11

- 프로젝트 운영 체계 문서 정리
- AI 인계 문서 생성
- 코드 기능 변경 없음

## v1.3-10

- 해금 버그 수정
- 캐릭터 매력 강화
- 요청 취소 흐름 추가
- 성장 기록 강화
- 부모 재인증 강화
- 알림함 추가
- 식사 감사 미션 추가
- 보물상자 안내 개선

## v1.3-9

- 가족 보상 경제 추가
- 협동 보상과 팀 메달 추가
- 주간/월간 마감 추가
- 시즌 미션 추가

## v1.3-8

- Android PWA 지원
- 앱 아이콘과 manifest, service worker 구성
- 위생 미션 추가

## v1.3-7

- 개인방 권한 잠금 추가
- 학습 퀘스트 추가
- 시험 보너스 시스템 추가

## v1.3-6

- 보물상자 오픈 연출 강화
- 알림 시스템 추가
- 아이별 PIN 입장 추가

## v1.3-5

- 효과음 추가
- 보물상자 추가
- 부모 승인형 특별 미션 추가
- 백업 알림 추가

## v1.3

- 스킨샵 오픈
- 코인으로 아이템을 구매하고 보관함에서 장착하는 흐름 추가

## v1.2

- 캐릭터 움직임 추가
- 팀 사진관 추가
- 업데이트 예고 영역 추가

## v1.1

- XP와 코인 분리
- 레벨 시스템 추가
- 형제 리그 추가
- 보관함 추가

## v1.0

- 기본 포인트 체크앱 시작
- 아이별 미션 완료와 점수 기록 기능 제공
