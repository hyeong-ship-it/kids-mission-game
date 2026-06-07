# AI 인계 문서

문서 기준일: 2026-06-07  
프로젝트: 3형제 미션 배틀  
앱 기능 최신 버전: v1.3-13  
배포 관리 패치: v1.3-14  
설계 문서 패치: v1.4-0

## 프로젝트 목적

3형제가 집안 미션, 학습 퀘스트, 위생 미션, 가족 협동 미션을 즐겁게 수행하고 XP, 코인, 아이템, 성장 기록을 얻는 가족용 미션 RPG다. 부모는 승인, 보상, 마감, 백업, 칭찬 우체통을 관리한다. 제품 방향은 성장, 해금, 칭찬, 협동 중심이다.

## 현재 파일 목록

운영 핵심 파일:

- `index.html`
- `manifest.webmanifest`
- `sw.js`
- `assets/icon-192.png`
- `assets/icon-512.png`
- `assets/icon-maskable-512.png`

운영 문서:

- `PROJECT_STATE.md`
- `PROJECT_RULES.md`
- `ROADMAP.md`
- `CHANGELOG.md`
- `PATCH_QUEUE.md`
- `TEST_CHECKLIST.md`
- `AI_HANDOFF.md`

v1.4 설계 문서:

- `JINWOO_DIRECTOR_MODE_SPEC.md`
- `LEARNING_DUNGEON_SPEC.md`
- `AI_COLLABORATION_RULES_FOR_KIDS.md`
- `QUESTION_PACK_FORMAT.md`
- `JINWOO_ACTIVITY_GUIDE.md`

로컬에 존재하지만 GitHub 업로드 대상이 아닌 파일:

- `_do_not_upload/backups/*.html`
- `.claude/`
- `make_release_package.py`, `make_release_package.bat`
- `RELEASE_GUIDE.md`
- 기타 개인 설정, 임시 파일, 검수 로그

## v1.4-0 인계 요약

이번 패치는 코드 기능 구현이 아니라 설계 문서 패치다. 다음 구현자가 바로 기능을 만들기 전에 아래 문서를 기준으로 방향을 확인해야 한다.

- PC 전용 진우 개발자 모드: `JINWOO_DIRECTOR_MODE_SPEC.md`
- 두뇌 던전: `LEARNING_DUNGEON_SPEC.md`
- 아이 AI 협업 원칙: `AI_COLLABORATION_RULES_FOR_KIDS.md`
- 문제팩 데이터 형식: `QUESTION_PACK_FORMAT.md`
- 진우 활동 운영 가이드: `JINWOO_ACTIVITY_GUIDE.md`

## 진우 개발자 모드 철학

진우 개발자 모드는 메인 게임 데이터를 편집하는 관리자 도구가 아니다. 진우가 `주니어 게임 디렉터`로서 동생을 관찰하고, 아이디어를 정리하고, 문제팩 후보를 만들고, 부모 검토를 요청하는 PC 전용 기획 도구다.

중요 기준:

- 실행 환경은 패드가 아니라 PC다.
- 추천 저장 키는 `jinwooDirectorMode_v1`이다.
- 메인 게임 저장 키 `kidsPointGame_v1`을 건드리지 않는다.
- 아이디어와 문제팩은 후보로 저장한다.
- 부모 승인 후 ChatGPT/Codex 작업을 거쳐 실제 게임에 반영한다.
- AI는 최종 결정자가 아니라 회의 상대다.

## 두뇌 던전 방향

두뇌 던전은 공부 앱처럼 보이는 별도 학습장이 아니라 게임 안의 반복 가능한 학습 던전이다.

초기 기준:

- 상어: 초6 진도 + 초5 복습 + 논리/상식
- 축복이: 초5 진도 + 초4 복습 + 사고력
- 복복이: 초2 기초 문해력 + 수감각 + 생활상식
- 1라운드 = 3문제
- 지식 조각을 새 학습 재화로 사용
- 메인 코인 보상은 하루 횟수 제한을 둔다
- 틀린 문제는 `다시 도전함`으로 표현한다

## AI 협업 원칙

AI는 정답을 대신 결정하는 기계가 아니다. 아이가 자기 생각을 먼저 쓰고, AI는 반대 의견, 대안, 작은 실험 방법을 제공한다.

다음 구현자는 AI 기능을 붙이기 전에 이 원칙을 먼저 UI 흐름에 반영해야 한다.

- 내 생각 먼저 쓰기
- AI에게 물어볼 질문 쓰기
- AI에게 반대 의견 요청하기
- AI 의견 중 참고할 점 고르기
- 내가 최종 결정하기
- 왜 그렇게 결정했는지 기록하기
- 부모가 최종 승인하기

초기 구현에서는 AI API 연결보다 프롬프트 생성기 또는 수동 회의 기록이 더 안전하다.

## 배포 패키지 생성

GitHub 업로드 전 아래를 실행한다.

```bash
python make_release_package.py
```

`_github_upload/` 폴더가 생성되고 `UPLOAD_CHECKLIST.md`가 포함된다. `_github_upload/` 폴더 자체가 아니라 그 안의 내용물을 GitHub Pages에 올린다.

## 절대 유지 기준

- localStorage 키 `kidsPointGame_v1` 변경 금지
- 부모 비밀번호 `0903` 유지
- 내부 kid ID 변경 금지: `jinwoo`, `jinyoung`, `jinhwan`
- 표시 이름 유지: 상어, 축복이, 복복이
- 기존 기능 삭제 금지
- 기존 데이터 저장 구조 변경 금지
- localStorage 초기화 금지
- 기존 XP, 코인, PIN, 보관함, 장착 상태, 승인 요청 데이터 유지
- 외부 라이브러리, CDN, 웹폰트, 외부 이미지, 외부 사운드 파일 사용 금지
- 아이 화면에서는 부정적 표현을 피하고 성장, 해금, 칭찬, 협동 중심으로 표현

## 작업 시작 전 해야 할 일

1. 현재 프로젝트 루트 파일 목록을 확인한다.
2. `PROJECT_STATE.md`, `PROJECT_RULES.md`, `CHANGELOG.md`, `PATCH_QUEUE.md`, `AI_HANDOFF.md`를 먼저 읽는다.
3. v1.4 작업이면 신규 설계 문서 5개를 먼저 읽는다.
4. `index.html`, `manifest.webmanifest`, `sw.js`의 현재 수정 시간을 확인한다.
5. 기능 수정 작업이면 수정 전 백업을 만든다.
6. 기존 localStorage 키와 데이터 구조를 바꾸지 않는 계획인지 확인한다.
7. 이미 적용된 부분 수정이 있는지 먼저 진단한다.

## 백업 기준

- 기능 코드 수정 전에는 `index.backup-before-작업명.html` 형태로 백업한다.
- `sw.js`나 `manifest.webmanifest` 수정 전에도 별도 백업 또는 변경 전 내용을 보존한다.
- 문서만 수정하는 작업은 백업 파일을 만들지 않아도 된다.
- 중단 후 다른 도구가 이어받을 때는 새 백업을 만든다.
- 백업 파일은 GitHub Pages에 업로드하지 않는다.

## 다음 추천 작업

1. v1.3-13 패드 실사용 검수
2. v1.4-1 PC 전용 진우 개발자 모드 MVP
3. v1.4-2 두뇌 던전 MVP
4. v1.4-3 문제팩 제작실
5. v1.4-4 제한형 AI 회의실 또는 AI 프롬프트 생성기

## 완료 보고 형식

완료 보고에는 아래 내용을 포함한다.

1. 작업명과 적용 버전
2. 생성/수정 파일
3. 핵심 변경 요약
4. 기존 코드 수정 여부
5. localStorage 키와 데이터 구조 유지 여부
6. 문법 검사 또는 패키지 생성 결과
7. 패드 실사용 검수 필요 여부
8. GitHub 업로드해야 할 파일
9. GitHub에 올리지 말아야 할 파일
10. 남은 주의사항
11. 어떤 도구에서 이어받았는지
12. 부분 적용 상태가 있었다면 어떻게 처리했는지

## 하지 말아야 할 일

- `kidsPointGame_v1` 키를 바꾸지 않는다.
- 저장 데이터를 초기화하지 않는다.
- 내부 kid ID를 바꾸지 않는다.
- 부모 비밀번호를 임의로 바꾸지 않는다.
- 기존 기능을 정리 목적으로 삭제하지 않는다.
- 진우 개발자 모드에서 메인 게임 데이터를 직접 수정하지 않는다.
- AI가 만든 아이디어나 문제를 부모 검토 없이 반영하지 않는다.
- 외부 라이브러리, CDN, 웹폰트, 외부 이미지, 외부 사운드를 추가하지 않는다.
- 백업 파일을 GitHub에 올리지 않는다.
- 패드 실사용 검수 없이 최종 안정판이라고 말하지 않는다.
- 세 도구가 동시에 같은 파일을 수정하게 하지 않는다.

## 도구 운영 원칙

- 기본 1차 코드 작업자는 Codex다.
- Claude Code와 Gemini는 역할 분담보다 토큰/사용량 부족 시 개발 흐름을 끊지 않고 이어가기 위한 대체 작업자로 쓴다.
- Codex 사용량이 부족하거나 중단되면 Claude Code 또는 Gemini로 이어받는다.
- Claude Code 사용량이 끝나면 Codex 또는 Gemini로 이어받는다.
- Gemini는 대형 코드 검토, 문서 정리, 누락 점검, 대체 구현 작업에 사용할 수 있다.
- 세 도구를 동시에 같은 파일에 수정시키지 않는다.
- 한 도구가 중단되면 다음 도구는 반드시 현재 파일 상태를 먼저 진단하고, 기존 변경이 어디까지 적용됐는지 확인한 뒤 이어서 작업한다.
