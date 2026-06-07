# GitHub 업로드 체크리스트

생성 시각: 2026-06-07 09:55:45
프로젝트: 3형제 미션 배틀  
앱 기능 최신 버전: v1.3-13  
배포 관리 패치: v1.3-14  
설계 문서 패치: v1.4-0  

---

## 업로드 대상 파일

- [x] `index.html`
- [x] `sw.js`
- [x] `manifest.webmanifest`
- [x] `PROJECT_STATE.md`
- [x] `PROJECT_RULES.md`
- [x] `ROADMAP.md`
- [x] `CHANGELOG.md`
- [x] `PATCH_QUEUE.md`
- [x] `TEST_CHECKLIST.md`
- [x] `AI_HANDOFF.md`
- [x] `JINWOO_DIRECTOR_MODE_SPEC.md`
- [x] `LEARNING_DUNGEON_SPEC.md`
- [x] `AI_COLLABORATION_RULES_FOR_KIDS.md`
- [x] `QUESTION_PACK_FORMAT.md`
- [x] `JINWOO_ACTIVITY_GUIDE.md`
- [x] `assets\icon-192.png`
- [x] `assets\icon-512.png`
- [x] `assets\icon-maskable-512.png`

---

## 업로드 제외 파일

- index.backup-*.html  (백업 파일 — GitHub 업로드 절대 금지)
- _do_not_upload/      (백업·로그·임시 파일 보관 폴더)
- .claude/             (Claude AI 작업 폴더)
- make_release_package.py / .bat
- RELEASE_GUIDE.md     (배포 안내 문서 — 로컬 보관용)
- *.log / *.tmp / *.bak

---

## GitHub Pages 업로드 방법

1. `_github_upload/` 폴더 안의 **내용물 전체**를 선택한다.
   (`_github_upload/` 폴더 자체가 아니라 그 안의 파일과 assets/ 폴더를 올린다)
2. GitHub 저장소 → Add file → Upload files 로 드래그 앤 드롭한다.
3. 커밋 메시지 예: `docs: v1.4-0 진우 개발자 모드와 두뇌 던전 설계`
4. Commit changes 를 누른다.
5. GitHub Pages 배포가 완료될 때까지 1~3분 기다린다.

---

## 업로드 후 확인 주소

```
https://hyeong-ship-it.github.io/kids-mission-game/?v=140-docs
```

캐시 갱신이 안 되면 주소 끝에 `?v=140-docs` 를 추가하거나
패드 브라우저에서 강력 새로고침(캐시 삭제 후 로드)을 한다.

---

## 패드에서 확인할 항목

- [ ] 앱 이름이 '3형제 미션 배틀'로 표시된다
- [ ] 기존 localStorage 데이터(XP, 코인, 아이템)가 유지된다
- [ ] 아이 캐릭터 탭에 '오늘의 작전' 카드가 표시된다
- [ ] 부모 메뉴 아이 관리 탭에 칭찬 우체통이 표시된다
- [ ] 칭찬 메시지 전송 후 아이 알림함에 도착한다
- [ ] PWA 오프라인 실행이 정상 작동한다
- [ ] 신규 설계 문서 5개가 GitHub에 표시된다
- [ ] `_do_not_upload/`와 백업 파일이 업로드되지 않았다

---

## ⚠️ 백업 파일 업로드 절대 금지

`index.backup-*.html` 파일은 GitHub Pages에 올리면 안 됩니다.  
백업 파일은 `_do_not_upload/backups/` 폴더에 보관하세요.  
이 체크리스트의 업로드 대상 목록에 백업 파일이 없는지 반드시 확인하세요.
