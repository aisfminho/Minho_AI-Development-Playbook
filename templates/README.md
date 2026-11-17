# 템플릿 모음

각 템플릿은 두 부분으로 나뉩니다.

- **A. 실사용 원문** — MOEL AI에서 실제로 쓴 프롬프트·양식의 발췌. 경로·계정 등은 `<repo>` 등으로 가림. 근거 세션 표시.
- **B. 일반화 템플릿** — 이 Playbook이 새로 만든 양식. `{ }` 안을 채워 씁니다.

| 템플릿 | 쓰는 단계 | A. 실사용 원문 | B. 일반화 |
|---|---|---|---|
| [decision-record.md](decision-record.md) | 3 결정 기록 | 결정 상태 규칙(헌장·결정 문서 발췌) | 결정 표 + 대체 표기 |
| [question-bundle.md](question-bundle.md) | 3·8 질문 | Q1~Q15 질문표(`55b37226:639`), 사용자 응답(`55b37226:88`) | 질문 묶음 + 응답 양식 |
| [step-approval.md](step-approval.md) | 6 승인 | 승인 명령어(memory), 최소 단위 표 항목 | Step 계획서 + 승인 기록 |
| [audit-request.md](audit-request.md) | 7 외부 감사 | Codex 감사 요청서 전문(`codex1:25`), 권한 시험(`codex2:12`) | 감사 요청서 + 권한 시험 |
| [subagent-review-prompt.md](subagent-review-prompt.md) | 4·7·8 내부 검토 | 서브에이전트 감사 프롬프트(`55b37226` 서브 `ae2ab98d:1`) | 영역별 읽기 전용 검토 프롬프트 |
| [audit-status-table.md](audit-status-table.md) | 7 감사 반영 | 상태표 머리말·행(`09fb2455:630`, `b1t5v1u06.txt`) | 상태표 + 용어 정의 |
| [session-handoff-prompt.md](session-handoff-prompt.md) | 9 세션 | 실제 시작 프롬프트(짧음), 상태 문서 항목(`55b37226:241`), 태그 요청(`fc1439ba:846`) | 인계 문서 + 새 세션 프롬프트 + 태그 요청 |
| [cross-review-prompt.md](cross-review-prompt.md) | 6·7 여러 AI 중계 | ChatGPT의 검토 범위 명시·방향 승인 분리·조건부 승인 문장(`gpt:6af696c2/2e1486a5`, `/6ef88671`, `/8bc0bf8e`) | 중계 검토 요청 + 답변 형식 + 지시문 전달 양식 (**v0.2 추가**) |

## 쓰는 법

1. 프로젝트 `docs/` 아래에 복사합니다.
2. B 부분만 남기고 A 부분은 지워도 됩니다(A는 참고용).
3. MOEL 전용 값(금액, 스택, 파일명)은 그대로 쓰지 말고 프로젝트 값으로 바꿉니다.
