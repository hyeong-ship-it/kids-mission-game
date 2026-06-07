# 프로젝트 상태 문서

문서 기준일: 2026-06-07  
앱 기능 최신 버전: v1.3-13  
배포 관리 패치: v1.3-14  
설계 문서 패치: v1.4-0

## 프로젝트 목적

`3형제 미션 배틀`은 아이들이 집안 미션, 학습 퀘스트, 위생 미션, 가족 협동 미션을 완료하면서 XP, 코인, 아이템, 성장 기록을 얻는 가족용 미션 RPG다. 부모는 승인, 보상, 마감, 백업, 칭찬 우체통을 관리하고, 아이 화면은 성장, 해금, 칭찬, 협동 중심으로 운영한다.

## 현재 운영 상태

- 최신 기능 적용 기준: v1.3-13
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

- GitHub Pages 최신 파일 반영 여부
- 홈 화면 PWA 실행 여부
- 기존 localStorage 데이터 유지 여부
- 아이별 PIN 입장
- 부모 메뉴 재인증
- 미션 클리어와 되돌리기
- 보물상자 열기와 안내 문구
- 시험 보너스 요청, 취소, 승인
- 가족 보상 요청과 승인
- 형제 협동 보상
- 주간/월간 마감
- 시즌 미션
- 스킨샵, 보관함, 장착 상태
- 알림함과 묶음 알림
- 백업과 불러오기
- 모바일/패드 화면 깨짐 여부

## v1.4 구현 전 주의사항

- v1.4-0 문서는 설계 기준이며 앱 기능은 아직 구현되지 않았다.
- `진우 개발자 모드`는 PC 전용 별도 도구로 설계한다.
- `두뇌 던전`은 메인 코인 경제와 학습 재화를 분리한다.
- AI API 연결은 별도 승인 전까지 구현하지 않는다.
- 승인되지 않은 진우 아이디어나 문제팩은 메인 게임에 자동 반영하지 않는다.
