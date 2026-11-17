# 사례: MOEL AI Desk 설계 과정

> 이 폴더는 **실제 기록**입니다. 일반화된 절차는 [`01-design-playbook/`](../../01-design-playbook/00-overview.md)에 있습니다.

## 프로젝트 개요 [사실]

- 무엇: 고용노동 민원을 분류하고, 담당 부서를 추천하고, 근거 기반 답변 초안을 만드는 AI 시연 시스템
- 왜: 대학원 기말 발표용(장기 운영 상용 서비스 아님)(`d39ff7ed:496`)
- 필수 시연: 단일 민원 자동 처리, Excel·CSV 최대 100건 일괄 처리와 실시간 진행률
- 기간: 기획 2026-09-02 ~ (ChatGPT), 설계 2026-11-11 ~ 2026-11-14(Claude Code 메인 세션 11개, Codex 세션 2개)
- 끝난 상태: 구현 전 기준 태그 `pre-implementation-2026-11-14` 생성(`fc1439ba:870`). **구현 본격 착수 전**
- 승인 상태: 태그 시점에 **STEP-01 완료 승인은 아직 대기 중**. 다음 순서: STEP-01 완료 승인 → 묶음 1 시작 승인 → STEP-03-00 시작 승인. 인계 문서의 커밋·push·태그 상태 갱신도 대기(`fc1439ba:870`)

## 문서

| 문서 | 내용 |
|---|---|
| [01-timeline.md](01-timeline.md) | 날짜별 작업과 주요 결정 |
| [02-user-corrections.md](02-user-corrections.md) | 사용자 반려·정정으로 설계가 바뀐 사례 |
| [03-subagent-collaboration.md](03-subagent-collaboration.md) | 서브에이전트 16개 위임과 문제점 |
| [04-codex-audit.md](04-codex-audit.md) | Codex 감사 AUD-01~29와 남은 결함 |
| [05-chatgpt.md](05-chatgpt.md) | **(v0.2)** ChatGPT의 기획·기술 제안·지시문 작성, 사용자 중계 협업 구조, 검증된 충돌 2건 |

## MOEL 전용 설정 (다른 프로젝트에 그대로 복사하지 말 것)

| 영역 | 설정 |
|---|---|
| 스택 | Vue 3 + TypeScript + Tailwind + shadcn-vue / FastAPI / LangChain / ChromaDB / SSE / SQLite + asyncio |
| AI | OpenAI API(LLM·임베딩). 로컬 LLM 안은 대체됨 |
| 배포 | Vercel + Railway(체험 플랜으로 시작), 조기 배포 STEP-03-02 |
| 비용 | 소액 선불·자동 충전 꺼짐, 앱 내부 한도 < 선불액(추천안), 시연 예비비 고정(구체 금액은 공개본에서 생략) |
| 데이터 | AI-Hub 민원 1,309건, 조직 686건, 담당업무·연락처 11,380건 |
| 개인정보 | 3종 가림(전화번호·주민번호·이메일), 시연용 최소 가드레일(D-030), 합성 데이터로 발표 |
| 승인 | `STEP-XX 시작 승인 / 완료 승인 / 반려` |
| 소통 | `message.md` ↔ `respond.md`(Claude), `codex_only_*`(Codex) |
| 헌장 줄 수 | 150줄 [보고서] |
| 커밋 제목 | `YYYY-MM-DD HH:MM` |

## 이 사례를 읽을 때 주의 [사실]

1. 첫 세션에서 **설계보다 구현이 먼저** 일부 진행되었습니다([02 #1](02-user-corrections.md)).
2. 최종 검증의 `pytest 41 passed / vitest 4 passed`는 그 초기 코드의 결과입니다(`fc1439ba:765`).
3. Codex 29건 PASS는 **설계 반영** 판정입니다. AUD-19·22의 **코드 결함은 남아 있습니다**([04](04-codex-audit.md)).
4. ChatGPT는 9월부터 기획에 참여했고 지시문 초안을 썼지만, **AI끼리는 자동으로 연결되지 않았고** 사용자가 모든 지시와 결과를 중계했습니다. ChatGPT의 제안이 모두 채택된 것은 아닙니다([05](05-chatgpt.md)).
