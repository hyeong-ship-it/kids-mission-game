# 문제팩 형식 설계 문서

문서 기준일: 2026-06-07  
작업명: v1.4-0 PC 전용 진우 개발자 모드 + 두뇌 던전 설계 문서 패치  
대상 기능: 두뇌 던전, 진우 개발자 모드 문제팩 제작실

## 문제 기본 필드

예시 JSON 구조:

```json
{
  "id": "q_math_g6_ratio_001",
  "targetKidId": "jinwoo",
  "grade": 6,
  "subject": "math",
  "topic": "비와 비율",
  "difficulty": 2,
  "type": "multiple_choice",
  "question": "어떤 문제 문장",
  "choices": ["A", "B", "C", "D"],
  "answer": "B",
  "hint": "생각을 도와주는 힌트",
  "explanation": "정답 해설",
  "tags": ["current_progress", "ratio"],
  "retryGroup": "ratio_basic",
  "createdBy": "parent",
  "status": "approved"
}
```

## 필드 설명

- `id`: 문제 고유 ID. 과목, 학년, 주제, 번호를 알 수 있게 작성한다.
- `targetKidId`: 대상 아이 ID. `jinwoo`, `jinyoung`, `jinhwan` 중 하나를 사용한다.
- `grade`: 대상 학년 숫자.
- `subject`: 과목 코드.
- `topic`: 진도 또는 문제 주제.
- `difficulty`: 난이도 숫자. 1부터 4까지 사용한다.
- `type`: 문제 유형. 초기 MVP는 `multiple_choice`를 우선한다.
- `question`: 아이에게 보여줄 문제 문장.
- `choices`: 객관식 선택지 배열.
- `answer`: 정답. 객관식은 선택지 값 또는 선택지 번호 기준을 프로젝트에서 통일한다.
- `hint`: 정답을 바로 알려주지 않고 생각을 도와주는 힌트.
- `explanation`: 짧고 친절한 해설.
- `tags`: 추천, 진도, 복습, 유형 분류에 쓰는 태그 배열.
- `retryGroup`: 비슷한 유형을 다시 도전함에서 묶기 위한 그룹 ID.
- `createdBy`: 작성자. 예: `parent`, `jinwoo`, `ai_draft`.
- `status`: 문제 상태.

## 과목 코드

- `korean`
- `math`
- `society`
- `science`
- `english`
- `reading`
- `common_sense`
- `life`
- `logic`
- `current_issue`

## 난이도

1. 쉬움
2. 현재 수준
3. 도전
4. 보스

## 문제 상태

- `draft`
- `parent_review`
- `approved`
- `rejected`
- `archived`

## 문제 제작 원칙

- 초등학생 눈높이로 쓴다.
- 너무 긴 문장을 피한다.
- 해설은 짧고 친절하게 쓴다.
- 틀렸다는 표현보다 다시 도전 표현을 쓴다.
- 정치, 혐오, 공포, 성인 주제는 금지한다.
- 현재 이슈는 어린이 눈높이의 상식으로 변환한다.

## 진우 제작 문제 승인 흐름

1. 진우가 문제 작성
2. 부모 검토
3. 필요하면 AI 회의
4. 승인
5. 문제팩 반영
6. 동생 풀이 결과 기록

## 저장 분리 원칙

- 진우 개발자 모드의 문제 후보는 `jinwooDirectorMode_v1` 같은 별도 저장 키에 둔다.
- 메인 게임 저장 키 `kidsPointGame_v1`은 문제 후보 작성 단계에서 건드리지 않는다.
- 승인된 문제도 실제 게임 반영 전에는 문서 또는 패치 작업을 거친다.
