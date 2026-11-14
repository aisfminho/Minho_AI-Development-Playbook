# 세션 색인

## 보관 위치

`<archive>` = 이 Playbook 폴더의 상위 보관 폴더(읽기 전용). 원래 경로(사용자 홈 아래 경로)는 공개 문서에서 가렸습니다.

| 원본 | 위치 |
|---|---|
| Claude Code 세션 | `<archive>/claude-code/20261114-232522/<project-dir>/{세션ID}.jsonl` |
| Claude 서브에이전트 | `<archive>/claude-code/20261114-232522/<project-dir>/{세션ID}/subagents/agent-{ID}.jsonl` |
| Claude 도구 결과 | `<archive>/claude-code/20261114-232522/<project-dir>/{세션ID}/tool-results/` |
| Claude 프로젝트 메모리 | `<archive>/claude-code/20261114-232522/<project-dir>/memory/*.md` |
| Codex 세션 | `<archive>/codex/20261114-232709/sessions/2026/11/13/rollout-*.jsonl` |

## Claude Code 메인 세션 (11개)

| 표기 | 전체 ID | 줄 수 | 시작(KST) [보고서] | 주제 |
|---|---|---|---|---|
| `d39ff7ed` | d39ff7ed-3ab2-4377-8625-f1a639e4af29 | 1,519 | 11/11 21:16 | 자료·데이터 실측·LLM 선택·초기 구현과 중단·GitHub |
| `4d23f4bc` | 4d23f4bc-6970-4d37-b2d8-214a769ca7f9 | 732 | 11/12 11:14 | 구조·헌장·가상환경·스킬/훅 |
| `44d22df7` | 44d22df7-0aaa-49f1-bb3e-91050f8c301e | 1,565 | 11/12 12:38 | Step 승인·평가·법령 RAG·Git 규칙 |
| `55b37226` | 55b37226-aced-4109-8a13-f4f3ac2e40c1 | 763 | 11/13 10:35 | 결정 확정·개인정보·일정·설계 감사·문서 작성 |
| `79503ed4` | 79503ed4-bf75-4e67-82e0-c76df5db45e9 | 1,386 | (55b37226에서 이어짐) | 문서 동기화·정합성 리뷰·UI/UX·A+ |
| `09fb2455` | 09fb2455-4836-4f01-8540-fd488ab96443 | 918 | 11/13 14:58 | Codex 채널 분리·감사 반영·상태표 |
| `7cba337d` | 7cba337d-5850-4382-8497-758e5319d550 | 304 | 11/13 17:26 | 인계 스킬·SessionEnd Hook |
| `f8416f8e` | f8416f8e-3a8e-48ad-ae3b-1ce27eb0ae04 | 80 | 11/13 17:3x | Hook 시험 |
| `badbdc12` | badbdc12-f825-4f04-9666-df11a4fcb878 | 183 | 11/13 17:34 | Hook 시험 확인 |
| `bab8244b` | bab8244b-6bdc-4c69-9508-ef2a368a18f4 | 992 | 11/14 11:17 | 설정·보고 보관·최소 단위·미결 질문 |
| `fc1439ba` | fc1439ba-924b-4daf-991d-2151a7bad205 | 874 | 11/14 13:09 | 미결 해소·최종 검증·커밋·push·태그 |

1차 보고서의 "JSONL 27개 = 메인 11 + 서브에이전트 관련 약 16"은 [보고서]입니다. 이번 확인: 메인 11개, 서브에이전트 파일 19개(고유 16개, 5개는 `55b37226`·`79503ed4`에 중복).

## 서브에이전트 (고유 16개)

| 세션 | 에이전트 파일 |
|---|---|
| `d39ff7ed` | agent-a6e2b0756bf470bdb |
| `44d22df7` | agent-a4e0b09cf10302760 |
| `55b37226` | agent-ae2ab98d45963d858, agent-a8c3484f0967d4484, agent-a598efc35849e3543 (감사) / agent-ad75c840b1ae26e33, agent-a417ea5a5b30c2950, agent-a0c0e725821ca68b9, agent-a79f619edca1d781a, agent-a29dff387b57d297f (작성, `79503ed4`에도 있음) |
| `79503ed4` | agent-a4886e0e155463c53, agent-a74479056eb844800 |
| `09fb2455` | agent-a257927352cdea365 |
| `bab8244b` | agent-a94ce891045ee7d3e, agent-a99791b6f6dce7fe0, agent-ab892e0afc06e18b6 |

## Codex 세션 (2개)

| 표기 | 파일 | 줄 수 | 시작 | 주제 |
|---|---|---|---|---|
| `codex1` | rollout-2026-11-13T14-51-24-01a1d375-f1cb-7ab2-b229-a9e90669a49b.jsonl | 125 | 11/13 14:51 | 감사 요청서 읽기·감사 계획 |
| `codex2` | rollout-2026-11-13T15-26-00-01a1d395-a03f-7141-b959-c1d1124c6aef.jsonl | 958 | 11/13 15:26 (11/14까지) | 권한 시험·1~3차 감사·재검증·최종 재대조 |

## 프로젝트 메모리 (9개)

`MEMORY.md`(색인), `approval-gates.md`, `codex-only-files.md`, `design-before-implementation.md`, `milestone-1125-demo.md`, `respond-md-output.md`, `step-approval-process.md`, `testable-minimal-units.md`, `ui-design-direction.md`. 메모리 본문에는 커밋 작성자 계정 등 개인정보가 있어 인용 시 제외했습니다.

## 줄 번호 표기 주의

- 줄 번호는 JSONL 파일의 물리적 줄 번호(1부터)입니다.
- 사용자 메시지·도구 결과·Claude 응답이 각각 한 줄입니다. 같은 내용이 `api-request-blob` 줄에 중복될 수 있으므로, 이 Playbook은 `user`/`assistant` 줄을 우선 표기했습니다.
- `b1t5v1u06.txt:N`은 `fc1439ba/tool-results/b1t5v1u06.txt`(Git diff 출력)의 줄 번호입니다.
