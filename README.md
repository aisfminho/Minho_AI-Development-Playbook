# AI Development Playbook — 설계편 v0.2

> 상태: **초안 v0.2** (v0.1: 2026-11-15) · 범위: **설계 단계만** · 구현편: 미작성 · ChatGPT 기록: **통합됨**(선별 세션 기준, 한계는 [unverified.md](sources/unverified.md))

**v0.2에서 달라진 것**: ChatGPT의 실제 기여(9월 기획 ~ 11월 지시문 작성·보고서 검토)를 [`05-chatgpt.md`](case-studies/moel-ai/05-chatgpt.md)로 추가했고, 사용자가 AI 사이를 **직접 중계한** 협업 구조, 지시문의 작성 주체와 실행 주체, 11-12 구현 중단·재개 경위, 13,597행/11,380행의 차이를 확인된 근거와 함께 보완했습니다. 중계 검토 양식 [`cross-review-prompt.md`](templates/cross-review-prompt.md)가 새로 생겼습니다. v0.1의 설계 절차 본문은 유지했습니다.

AI 에이전트(Claude Code, Codex 등)와 함께 소프트웨어를 **설계**하는 절차를 정리한 방법론입니다.
MOEL AI 프로젝트(대학원 기말 발표용 민원 처리 시연 시스템)의 실제 설계 과정 기록에서 출발했고, 다른 프로젝트에서도 다시 쓸 수 있도록 일반화했습니다.

## 이 Playbook이 답하려는 질문

- AI가 너무 일찍 코드를 쓰기 시작하지 않게 하려면?
- 데이터 수치·기술 선택·화면 표현을 **추측이 아니라 근거**로 결정하려면?
- 바뀐 결정을 잃지 않고 추적하려면?
- 다른 AI에게 독립 감사를 맡기고, 그 결과를 정직하게 해석하려면?
- 긴 작업을 여러 세션에 나눠도 맥락을 잃지 않으려면?

## 구성

| 폴더 | 내용 | 먼저 읽을 사람 |
|---|---|---|
| [`01-design-playbook/`](01-design-playbook/00-overview.md) | 9단계 설계 절차(요구사항 → Git 기준점) | 처음 적용하는 사람 |
| [`templates/`](templates/README.md) | 바로 복사해 쓰는 양식 8종(v0.2에서 중계 검토 양식 추가) | 실제 작업 중인 사람 |
| [`case-studies/moel-ai/`](case-studies/moel-ai/README.md) | 실제 타임라인, 사용자 반려 사례, 서브에이전트 협업, Codex 감사, **ChatGPT 기여와 3자 협업** | 근거를 확인하려는 사람 |
| [`sources/`](sources/session-index.md) | 세션 ID, 근거 위치, 미확인 목록 | 검증·후속 작업자 |

## 사용 방법 (새 프로젝트에 적용)

1. [`00-overview.md`](01-design-playbook/00-overview.md)의 전체 흐름과 역할 분담을 읽습니다.
2. 프로젝트 헌장 문서(예: `CLAUDE.md`)에 **"지금은 설계 단계, 코드 작성 금지"**와 승인 명령어를 적습니다 → [`06-approval-process.md`](01-design-playbook/06-approval-process.md). 복사용 문장: [`templates/step-approval.md`](templates/step-approval.md)의 "헌장 문서에 넣을 문장".
3. 결정 기록 파일을 만들고 [`templates/decision-record.md`](templates/decision-record.md) 양식을 씁니다.
4. 1~9단계 문서를 순서대로 따르되, 각 문서의 **완료 기준** 체크리스트를 통과해야 다음 단계로 넘어갑니다.
5. 설계 문서가 모이면 [`templates/audit-request.md`](templates/audit-request.md)로 다른 AI에게 독립 감사를 맡깁니다.
6. 구현 시작 전에 Git 기준 태그를 만들고, 구현 시작 승인을 따로 받습니다.
7. 세션을 넘길 때는 [`templates/session-handoff-prompt.md`](templates/session-handoff-prompt.md)로 인계 문서와 새 세션 프롬프트를 준비합니다.

프로젝트가 작다면 1·3·6·7·9단계만 적용해도 효과가 큽니다.

## 표기 규칙

| 표시 | 뜻 |
|---|---|
| **[사실]** | 세션 원본 기록에서 확인된 사실. 근거를 `세션ID앞8자리:줄번호`로 표시 |
| **[권장]** | 사실에서 일반화한 이 Playbook의 제안. 실제 프로젝트에서 그대로 쓰인 규칙과 다를 수 있음 |
| **[MOEL 전용]** | MOEL AI에만 해당하는 설정값(기술 스택, 금액, 줄 수 제한 등). 그대로 복사하지 말 것 |
| **[보고서]** | 1·2차 분석 보고서 기반이며, 이번 작성 때 원본을 다시 대조하지 않음 |
| **[미확인]** | 근거가 부족하거나 원본이 없음 → [`sources/unverified.md`](sources/unverified.md) |
| **[사실: 시각 일치]** / **[사실: 문장 일치]** / **[추정]** | v0.2 ChatGPT 대조에서 확인 수준을 나눈 표기. 정의는 [`05-chatgpt.md`](case-studies/moel-ai/05-chatgpt.md) 0절 |

(v0.1의 **[통합 대기]** 표기는 ChatGPT 기록 통합으로 해소되었고, 남은 불확실성은 **[미확인]**으로 옮겼습니다.)

근거 표기 예: `d39ff7ed:1149` = Claude Code 세션 `d39ff7ed…` JSONL의 1149번째 줄. `codex2:843` = Codex 두 번째 세션 843번째 줄. `gpt:6aed9c1d/7f4ebb09` = ChatGPT 대화 `6aed9c1d…`의 메시지 `7f4ebb…`. 전체 세션 목록은 [`sources/session-index.md`](sources/session-index.md).

## 먼저 알아야 할 정직한 사실 3가지

1. **설계 전에 코드가 일부 있었습니다.** 첫 세션에서 "나머지 개발 진행"이 담긴 지시문(ChatGPT가 권고한 문안, `d39ff7ed:764`, `gpt:6aed5ec8/98e50c1f`)을 받은 Claude가 백엔드 엔진(Mock LLM), API, 합성 데이터, 프론트 설정·일부 모듈, 테스트를 먼저 만들었고, 사용자가 두 번 중단시켰습니다(`d39ff7ed:1149`, `:1160`, `:1386`). 첫 중단 8분 뒤 사용자가 "개발 진행"이 담긴 지시문을 다시 붙여넣어 구현이 재개됐고(`:1164`), Claude는 **충돌을 확인하지 않았습니다**([05-chatgpt.md E-1](case-studies/moel-ai/05-chatgpt.md)). 이후 기록된 `pytest 41 passed / vitest 4 passed`는 **이 초기 코드의 테스트 결과**입니다.
2. **Codex 설계 감사 29건 PASS는 설계 문서에 반영되었다는 뜻입니다.** 코드 수정이나 테스트 통과를 뜻하지 않습니다. 29건 중 26건은 코드 구현이 필요하고(그중 2건은 현재 코드 결함 확인), 2건은 문서 수정, 1건은 관리 규칙으로 해결되며, **코드 실행·테스트로 닫힌 항목은 0건**입니다([04](case-studies/moel-ai/04-codex-audit.md)). Codex도 "구현·테스트 완료 판정은 아닙니다"라고 밝혔습니다(`codex2:843`).
3. **AUD-19·AUD-22 코드 결함이 남아 있습니다.** 수정 답변·메모의 개인정보 가림 누락(AUD-19), 빈 LLM 응답을 성공으로 처리(AUD-22). 둘 다 STEP-03-00에서 고치기로 했고, AUD-19는 공개 배포 전 차단 조건입니다(`09fb2455:630`).

## 범위 밖 (이번 버전에 없는 것)

- 구현편(TDD, 최소 단위 구현, 병렬 구현 운영) — 구현 단계 기록이 생기면 작성
- 구현 코드, 설치 스크립트
- ChatGPT 전체 대화의 요약 — 프로젝트 관련 선별 세션만 다루며, 대화 원문은 저장소에 두지 않음

## 공개 전 주의

이 폴더에는 인증 정보·개인 연락처·로컬 기기 경로를 넣지 않았습니다. 세션 원본을 인용할 때 절대 경로는 `<repo>`, `<archive>`로 바꿨습니다. 외부에 공개하기 전 [`sources/unverified.md`](sources/unverified.md)의 "공개 전 점검" 항목을 확인하세요.
