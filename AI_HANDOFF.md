# AI 인계 문서

문서 기준일: 2026-06-06  
프로젝트: 3형제 미션 배틀  
최신 적용 보고 버전: v1.3-13  
문서 정리 패치: v1.3-13

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

문서 파일:

- `PROJECT_STATE.md`
- `PROJECT_RULES.md`
- `ROADMAP.md`
- `CHANGELOG.md`
- `PATCH_QUEUE.md`
- `TEST_CHECKLIST.md`
- `AI_HANDOFF.md`

로컬에 존재하지만 GitHub 업로드 대상이 아닌 파일:

- `index.backup-*.html`
- `.claude/`
- 기타 개인 설정, 임시 파일, 검수 로그

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
2. `PROJECT_STATE.md`, `PROJECT_RULES.md`, `CHANGELOG.md`, `PATCH_QUEUE.md`를 먼저 읽는다.
3. `index.html`, `manifest.webmanifest`, `sw.js`의 현재 수정 시간을 확인한다.
4. 기능 수정 작업이면 수정 전 백업을 만든다.
5. 기존 localStorage 키와 데이터 구조를 바꾸지 않는 계획인지 확인한다.
6. 이미 적용된 부분 수정이 있는지 먼저 진단한다.

## 백업 기준

- 기능 코드 수정 전에는 `index.backup-before-작업명.html` 형태로 백업한다.
- `sw.js`나 `manifest.webmanifest` 수정 전에도 별도 백업 또는 변경 전 내용을 보존한다.
- 문서만 수정하는 작업은 백업 파일을 만들지 않아도 된다.
- 중단 후 다른 도구가 이어받을 때는 새 백업을 만든다.
- 백업 파일은 GitHub Pages에 업로드하지 않는다.

## 완료 보고 형식

완료 보고에는 아래 내용을 포함한다.

1. 작업명과 적용 버전
2. 생성/수정 파일
3. 핵심 변경 요약
4. 기존 코드 수정 여부
5. localStorage 키와 데이터 구조 유지 여부
6. 문법 검사 결과
7. 패드 실사용 검수 필요 여부
8. GitHub 업로드해야 할 파일
9. GitHub에 올리지 말아야 할 파일
10. 남은 주의사항
11. 어떤 도구에서 이어받았는지
12. 부분 적용 상태가 있었다면 어떻게 처리했는지

## GitHub 업로드 기준

업로드 대상:

- `index.html`
- `manifest.webmanifest`
- `sw.js`
- `assets/icon-192.png`
- `assets/icon-512.png`
- `assets/icon-maskable-512.png`
- 운영 문서 7개

업로드 금지:

- `index.backup-*.html`
- `.claude/`
- 개인 설정 파일
- 로컬 로그
- 임시 검수 파일

## 하지 말아야 할 일

- `kidsPointGame_v1` 키를 바꾸지 않는다.
- 저장 데이터를 초기화하지 않는다.
- 내부 kid ID를 바꾸지 않는다.
- 부모 비밀번호를 임의로 바꾸지 않는다.
- 기존 기능을 정리 목적으로 삭제하지 않는다.
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
- 중단 후 이어받을 때는 새 백업을 만든다.
- 완료 보고에는 어떤 도구에서 이어받았는지, 부분 적용 상태를 어떻게 처리했는지 포함한다.
