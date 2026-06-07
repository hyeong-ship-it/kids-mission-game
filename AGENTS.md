# AGENTS.md — 3형제 미션 배틀 AI 작업자 핵심 가이드

문서 기준일: 2026-06-07  
대상: Codex, Claude Code, Gemini 등 이 프로젝트에서 작업하는 모든 AI 도구

---

## 1. 작업 시작 전 반드시 읽을 문서 (순서대로)

1. `PROJECT_RULES.md` — 절대 유지 기준, 개발 원칙, AI 운영 책임 원칙
2. `AI_HANDOFF.md` — 인계 요약, AI 운영 원칙, 작업 지시서 원칙, 전환 기준
3. `PROJECT_STATE.md` — 현재 앱 버전, 기능 목록, 최신 패치 상태
4. `PATCH_QUEUE.md` — 다음 작업 후보와 우선순위
5. `CHANGELOG.md` — 패치 이력
6. `TEST_CHECKLIST.md` — 검수 기준 (특히 `0-A` 목적 적합성 섹션)

v1.4 작업이면 추가로:

- `JINWOO_DIRECTOR_MODE_SPEC.md`
- `AI_COLLABORATION_RULES_FOR_KIDS.md`
- `_do_not_upload/jinwoo_director_mode/README_JINWOO_DIRECTOR_MODE.md`

---

## 2. 절대 수정 금지 파일

| 파일 | 이유 |
| --- | --- |
| `index.html` | 메인 게임 기능 파일. 기능 구현 패치가 아니면 건드리지 않는다. |
| `sw.js` | PWA 서비스 워커. 캐시 갱신 리스크 있음. |
| `manifest.webmanifest` | PWA 앱 정의 파일. |
| `assets/` | 아이콘 이미지. |
| `_do_not_upload/jinwoo_director_mode/jinwoo_director_mode.html` | 이미 완료된 패치를 무단 재수정 금지. |

---

## 3. 핵심 저장 키 및 고정 값

| 항목 | 값 |
| --- | --- |
| 메인 게임 localStorage 키 | `kidsPointGame_v1` — 절대 변경 금지 |
| 진우 개발자 모드 localStorage 키 | `jinwooDirectorMode_v1` — 메인 키와 완전 분리 |
| 부모 비밀번호 | `0903` — 변경 금지 |
| 내부 kid ID | `jinwoo`, `jinyoung`, `jinhwan` — 변경 금지 |
| 표시 이름 | 상어(진우·초6), 축복이(진영·초5), 복복이(진환·초2) |

---

## 4. 폴더 업로드 기준

| 폴더/파일 | GitHub 업로드 |
| --- | --- |
| `_github_upload/` 안의 내용물 | ✅ 업로드 대상 (폴더 자체는 올리지 않음) |
| `_do_not_upload/` | ❌ 절대 업로드 금지 |
| `_do_not_upload/jinwoo_director_mode/` | ❌ PC 로컬 전용, GitHub 금지 |
| `_do_not_upload/backups/` | ❌ 백업 파일 GitHub 금지 |
| `make_release_package.py` | ❌ 로컬 도구 |
| `.claude/` | ❌ AI 작업 설정 폴더 |

GitHub 업로드 전 반드시 `python make_release_package.py`를 실행해 `_github_upload/`를 갱신한다.

---

## 5. Codex / Claude Code / Gemini 전환 기준

기본 1차 코드 작업자는 Codex다. 토큰·사용량이 부족하면 아래 순서로 이어받는다.

| 상황 | 전환 |
| --- | --- |
| Codex 사용량 부족 | Claude Code 또는 Gemini |
| Claude Code 사용량 부족 | Codex 또는 Gemini |
| 대형 문서 정리·누락 점검 | Gemini 우선 활용 가능 |

이어받는 도구는 반드시 현재 파일 상태를 먼저 진단하고 기존 변경이 어디까지 적용됐는지 확인한 뒤 작업한다. 세 도구를 동시에 같은 파일에 수정시키지 않는다.

---

## 6. AI 운영 책임 원칙 (핵심 요약)

- 사용자는 목적과 방향을 제시하는 최종 책임자다. 세부 오류를 지적하는 검수자가 아니다.
- AI는 단순 실행자가 아니라 목적 달성을 책임지는 외부 컨설턴트이자 사업부 대표다.
- 작업 전에 단순 구현 가능성이 아니라 "이 목적에 맞는 최선의 설계인가"를 먼저 검토한다.
- UX, 운영성, 리스크, 데이터 안정성, 교육 효과, 장기 확장성의 허점을 선제적으로 제안한다.
- 사용자가 직접 부족한 부분을 지적해야 하는 상황을 만들지 않는다.
- 프로젝트 상태는 장기 메모리가 아니라 프로젝트 문서에 관리한다.

세부 원칙: `PROJECT_RULES.md` AI 운영 책임 원칙 섹션

---

## 7. 작업 완료 후 체크리스트

- [ ] `make_release_package.py` 실행 완료
- [ ] `_github_upload/`에 `_do_not_upload/` 또는 백업 파일 없음
- [ ] `_github_upload/`에 진우 개발자 모드 파일 없음
- [ ] 수정/생성 파일 목록 `CHANGELOG.md`에 기록
- [ ] `PATCH_QUEUE.md` 완료 항목 표시
- [ ] `TEST_CHECKLIST.md` `0-A` 목적 기준 검수 항목 확인
